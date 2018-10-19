v1.1/routers/router.go                                                                              0000644 0001750 0001750 00000013416 13312745743 016343  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package routers

import (
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/configs"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/routers"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.0/controllers"
	c11 "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.1/controllers"
	"gopkg.in/gin-gonic/gin.v1"
)

const (
	version = "1.1"
)

func init() {
	routers.RegisterRouter(registerRoutes)
}

// ServerStart function for start web server
func registerRoutes(
	engine *gin.Engine,
	params *configs.Params,
) {
	routingsDefaultPath(engine, params)
	routingsAuthenticationPath(engine, params)
	routingsMenuPath(engine, params)
	routingsProfilePath(engine, params)
	routingsOrganizationPath(engine, params)
	routingsApartmentPath(engine, params)
	routingsHousePath(engine, params)
	routingsReceiptsPath(engine, params)
	routingsMetersPath(engine, params)
	routingsReducedMetersPath(engine, params)
	routingsChangePasswordPath(engine, params)
	routingsLogoutPath(engine, params)
	routingsRemageSessionIDPath(engine, params)
	routingsPaymentsPath(engine, params)
}

func routingsDefaultPath(
	engine *gin.Engine,
	params *configs.Params,
) {
	controller := c11.DefaultController{
		Params: params,
	}
	engine.GET(version+"/", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndex()
	})
}

func routingsAuthenticationPath(
	engine *gin.Engine,
	params *configs.Params,
) {
	controller := controllers.AuthenticationController{
		Params: params,
	}
	engine.POST(version+"/authentication", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndex()
	})
}

func routingsMenuPath(
	engine *gin.Engine,
	params *configs.Params,
) {
	controller := c11.MenuController{
		Params: params,
	}
	engine.GET(version+"/menu", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndex()
	})
}

func routingsProfilePath(
	engine *gin.Engine,
	params *configs.Params,
) {
	profileController := controllers.ProfileController{
		Params: params,
	}
	engine.GET(version+"/profile", func(context *gin.Context) {
		profileController.Context = context
		profileController.ActionIndex()
	})

	accountsController := controllers.ProfileAccountsController{
		Params: params,
	}
	engine.GET(version+"/profile/accounts", func(context *gin.Context) {
		accountsController.Context = context
		accountsController.ActionIndex()
	})
}

func routingsOrganizationPath(
	engine *gin.Engine,
	params *configs.Params,
) {
	controller := controllers.OrganizationController{
		Params: params,
	}
	engine.GET(version+"/organization", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndex()
	})
}

func routingsApartmentPath(
	engine *gin.Engine,
	params *configs.Params,
) {
	controller := controllers.ApartmentController{
		Params: params,
	}
	engine.GET(version+"/apartment", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndex()
	})
}

func routingsHousePath(
	engine *gin.Engine,
	params *configs.Params,
) {
	controller := controllers.HouseController{
		Params: params,
	}
	engine.GET(version+"/house", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndex()
	})
}

func routingsReceiptsPath(
	engine *gin.Engine,
	params *configs.Params,
) {
	receiptsController := c11.ReceiptsController{
		Params: params,
	}
	engine.GET(version+"/receipts", func(context *gin.Context) {
		receiptsController.Context = context
		receiptsController.ActionIndex()
	})
	engine.GET(version+"/receipts/:year", func(context *gin.Context) {
		receiptsController.Context = context
		receiptsController.ActionView()
	})
	receiptController := c11.ReceiptsReceiptController{
		Params: params,
	}
	engine.GET(version+"/receipts/:year/receipt/:month", func(context *gin.Context) {
		receiptController.Context = context
		receiptController.ActionIndex()
	})
}

func routingsReducedMetersPath(
	engine *gin.Engine,
	params *configs.Params,
) {
	controller := controllers.ReducedMetersController{
		Params: params,
	}
	engine.GET(version+"/reduced-meters", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndex()
	})

	engine.POST(version+"/reduced-meters", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndexPost()
	})
}

func routingsMetersPath(
	engine *gin.Engine,
	params *configs.Params,
) {
	controller := controllers.MetersController{
		Params: params,
	}
	engine.GET(version+"/meters", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndex()
	})

	engine.POST(version+"/meters", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndexPost()
	})
}

func routingsChangePasswordPath(
	engine *gin.Engine,
	params *configs.Params,
) {
	controller := controllers.ChangePasswordController{
		Params: params,
	}
	engine.POST(version+"/changePassword", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndex()
	})
}

func routingsLogoutPath(
	engine *gin.Engine,
	params *configs.Params,
) {
	controller := controllers.LogoutController{
		Params: params,
	}
	engine.GET(version+"/logout", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndex()
	})
}

func routingsRemageSessionIDPath(
	engine *gin.Engine,
	params *configs.Params,
) {
	controller := controllers.RemakeSessionIDController{
		Params: params,
	}
	engine.POST(version+"/remakeSessionID", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndex()
	})
}

func routingsPaymentsPath(
	engine *gin.Engine,
	params *configs.Params,
) {
	controller := c11.PaymentController{
		Params: params,
	}
	engine.GET(version+"/payments", func(context *gin.Context) {
		controller.Context = context
		controller.ActionIndex()
	})
}
                                                                                                                                                                                                                                                  v1.1/controllers/receipts.go                                                                        0000644 0001750 0001750 00000004521 13306431165 017472  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package controllers

import (
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/configs"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/consts"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/tools"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.1/responses/receipts"
	"gopkg.in/gin-gonic/gin.v1"
)

// ReceiptsController structure intented for contein some methods
type ReceiptsController struct {
	Context *gin.Context
	Params  *configs.Params
}

// ReceiptsReceiptController structure intented for contein some methods
type ReceiptsReceiptController struct {
	Context *gin.Context
	Params  *configs.Params
}

// ActionIndex method intended for send JSON response
func (controller *ReceiptsController) ActionIndex() {

	err := checkKvadoCertificate(controller.Context)
	if err != nil && controller.Params.Environment != consts.EnvironmentDev {
		tools.SendResponse(controller.Context, 401, nil, []byte(err.Error()))
		return
	}

	responseData := receipts.ReceiptsData{
		Context: controller.Context,
		Params:  controller.Params,
	}

	code, reqBytes, errBytes := responseData.GetResponse()
	tools.SendResponse(responseData.Context, code, reqBytes, errBytes)
}

// ActionView method intended for send JSON response
func (controller *ReceiptsController) ActionView() {

	err := checkKvadoCertificate(controller.Context)
	if err != nil && controller.Params.Environment != consts.EnvironmentDev {
		tools.SendResponse(controller.Context, 401, nil, []byte(err.Error()))
		return
	}

	responseData := receipts.ReceiptsYearData{
		Context: controller.Context,
		Params:  controller.Params,
	}

	code, reqBytes, errBytes := responseData.GetResponse()
	tools.SendResponse(responseData.Context, code, reqBytes, errBytes)
}

// ActionIndex method intended for send JSON response
func (controller *ReceiptsReceiptController) ActionIndex() {

	err := checkKvadoCertificate(controller.Context)
	if err != nil && controller.Params.Environment != consts.EnvironmentDev {
		tools.SendResponse(controller.Context, 401, nil, []byte(err.Error()))
		return
	}

	responseData := receipts.ReceiptsMonthData{
		Context: controller.Context,
		Params:  controller.Params,
	}

	code, reqBytes, errBytes := responseData.GetResponse()
	tools.SendResponse(responseData.Context, code, reqBytes, errBytes)
}
                                                                                                                                                                               v1.1/controllers/default.go                                                                         0000644 0001750 0001750 00000001675 13306431165 017307  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package controllers

import (
	"errors"

	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/configs"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/consts"
	"gopkg.in/gin-gonic/gin.v1"
)

// DefaultController structure intented for contein some methods
type DefaultController struct {
	Context *gin.Context
	Params  *configs.Params
}

// ActionIndex method intended for send JSON response
func (controller *DefaultController) ActionIndex() {
	controller.Context.Data(
		200,
		"text/plain; charset=UTF-8",
		[]byte("This api version: 1.1"),
	)
}

func checkKvadoCertificate(ctx *gin.Context) error {
	certificate := ctx.GetHeader("Kvado-Certificate")
	if certificate == "" {
		return errors.New(`{"result":"error", "message":"Kvado-Certificate not found"}`)
	}

	if certificate != consts.KvadoCertificate {
		return errors.New(`{"result":"error", "message":"Kvado-Certificate not valid"}`)
	}
	return nil
}
                                                                   v1.1/controllers/menu.go                                                                            0000644 0001750 0001750 00000002072 13312745571 016625  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package controllers

import (
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/configs"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/consts"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/tools"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.1/responses"
	"gopkg.in/gin-gonic/gin.v1"
)

// MenuController structure intented for contein some methods
type MenuController struct {
	Context *gin.Context
	Params  *configs.Params
}

// ActionIndex method intended for send JSON response
func (controller *MenuController) ActionIndex() {

	err := checkKvadoCertificate(controller.Context)
	if err != nil && controller.Params.Environment != consts.EnvironmentDev {
		tools.SendResponse(controller.Context, 401, nil, []byte(err.Error()))
		return
	}

	responseData := responses.MenuData{
		Context: controller.Context,
		Params:  controller.Params,
	}

	code, reqBytes, errBytes := responseData.GetResponse()
	tools.SendResponse(responseData.Context, code, reqBytes, errBytes)
}
                                                                                                                                                                                                                                                                                                                                                                                                                                                                      v1.1/controllers/payment.go                                                                         0000644 0001750 0001750 00000002104 13326624043 017325  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package controllers

import (
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/configs"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/consts"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/tools"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.1/responses/payment"
	"gopkg.in/gin-gonic/gin.v1"
)

//PaymentController structure intented for contein some methods
type PaymentController struct {
	Context *gin.Context
	Params  *configs.Params
}

// ActionIndex method intended for send JSON response
func (controller *PaymentController) ActionIndex() {

	err := checkKvadoCertificate(controller.Context)
	if err != nil && controller.Params.Environment != consts.EnvironmentDev {
		tools.SendResponse(controller.Context, 401, nil, []byte(err.Error()))
		return
	}

	responseData := payment.Data{
		Context: controller.Context,
		Params:  controller.Params,
	}

	code, reqBytes, errBytes := responseData.GetResponse()
	tools.SendResponse(responseData.Context, code, reqBytes, errBytes)
}
                                                                                                                                                                                                                                                                                                                                                                                                                                                            v1.1/responses/payment/connection.go                                                                0000644 0001750 0001750 00000002365 13306431165 021147  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package payment

import (
	"fmt"
	"time"

	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/configs"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/consts"
	pb "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/protofiles"
	"google.golang.org/grpc"
)

//CreateReceiptsConnection function create gRPC connection
func CreateReceiptsConnection(params *configs.Params) (
	conn *grpc.ClientConn,
	c pb.LkReceiptsClient,
	callOpts []grpc.CallOption,
) {
	opts := []grpc.DialOption{}
	opts = append(opts, grpc.WithInsecure())
	opts = append(opts, grpc.WithTimeout(time.Second*10))
	opts = append(opts, grpc.WithMaxMsgSize(1024*1024*1024*1)) //1Gb

	if params.Environment == consts.EnvironmentDev {
		fmt.Printf("gRPC connection to host: %s\n", params.ReceiptsService)
	}

	// Set up a connection to the server.
	conn, err := grpc.Dial(params.ReceiptsService, opts...)
	if err != nil {
		fmt.Printf("did not connect: %v", err)
	}

	c = pb.NewLkReceiptsClient(conn)

	callOpts = []grpc.CallOption{}
	callOpts = append(callOpts, grpc.MaxCallRecvMsgSize(1024*1024*1024*1)) //Receive message size 1Gb
	callOpts = append(callOpts, grpc.MaxCallSendMsgSize(1024*1024*1024*1)) //Send message size 1Gb

	return
}
                                                                                                                                                                                                                                                                           v1.1/responses/payment/sort-period.go                                                               0000644 0001750 0001750 00000001013 13325354135 021246  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package payment

import (
	pb "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/protofiles"
)

//PeriodAsk struct to sort []*pb.LkUserReceiptsPaymentPeriod
type PeriodAsk []*pb.LkUserReceiptsPaymentPeriod

func (p PeriodAsk) Len() int      { return len(p) }
func (p PeriodAsk) Swap(i, j int) { p[i], p[j] = p[j], p[i] }
func (p PeriodAsk) Less(i, j int) bool {
	if p[i].Period.Year == p[j].Period.Year {
		return p[i].Period.Month > p[j].Period.Month
	}
	return p[i].Period.Year > p[j].Period.Year
}
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     v1.1/responses/payment/message.go                                                                   0000644 0001750 0001750 00000000624 13325353161 020430  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package payment

import (
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.0/responses"
)

//Message json message struct
type Message struct {
	Title   string          `json:"title,omitempty"`
	Text    string          `json:"text"`
	Color   responses.Color `json:"color,omitempty"`
	Badge   bool            `json:"badge"`
	Payment *Info           `json:"payment,omitempty"`
}
                                                                                                            v1.1/responses/payment/payment-data.go                                                              0000644 0001750 0001750 00000005121 13325353016 021364  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package payment

import (
	"encoding/json"
	"errors"
	"fmt"
	"strconv"

	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/configs"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/consts"
	pb "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/protofiles"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/requests"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.0/responses"
	"golang.org/x/net/context"
	"google.golang.org/grpc/metadata"
	"gopkg.in/gin-gonic/gin.v1"
)

// Data structure intended for contein data
type Data struct {
	Context *gin.Context
	Params  *configs.Params
}

// GetResponse method generate JSON response
func (data *Data) GetResponse() (int, []byte, []byte) {

	sID, aID, oID, err := getHeaders(data.Context)
	if err != nil {
		return 400, nil, responses.MakeErrorJSON(err.Error())
	}

	uID, statusCode, err := requests.GetLkUserID(data.Params, sID)
	if err != nil {
		return statusCode, nil, responses.MakeErrorJSON(err.Error())
	}

	conn, c, callOpts := CreateReceiptsConnection(data.Params)
	defer conn.Close()

	a, err := strconv.ParseUint(aID, 10, 32)
	if err != nil {
		return 400, nil, responses.MakeErrorJSON("Bad Account-Id")
	}

	ctx := metadata.AppendToOutgoingContext(
		context.Background(),
		"lkuserid",
		strconv.FormatInt(uID, 10),
		"organizationid",
		oID,
	)

	pr := &pb.LkUserReceiptsPaymentRequest{AccountId: uint32(a)}
	payment, err := c.GetPaymentInfo(ctx, pr, callOpts...)
	fmt.Println(payment)
	if err != nil {
		fmt.Printf("Could not get grpc data: %s\n\n", err.Error())
		return 500, nil, responses.MakeErrorJSON(err.Error())
	}
	switch payment.PaymentInfo.(type) {
	case *pb.LkUserReceiptsPaymentResponse_Info:
		info := NewPaymentInfo()
		info.Fill(payment.GetInfo())
		if data.Params.Environment == consts.EnvironmentDev {
			fmt.Printf("GetPaymentInformation gRPC response: %#v\n\n", payment)
		}

		if data.Params.Environment == consts.EnvironmentDev {
			fmt.Printf("Payment: %#v\n", info)
		}
		res, _ := json.Marshal(info)
		return 200, res, nil
	}

	return 200, nil, nil
}

func getHeaders(ctx *gin.Context) (
	sessionID string,
	accID string,
	orgID string,
	err error,
) {
	sessionID = ctx.GetHeader("Session-Id")
	if sessionID == "" {
		err = errors.New("Session-Id can not be empty")
		return
	}
	accID = ctx.GetHeader("Account-Id")
	if accID == "" {
		err = errors.New("Account-Id can not be empty")
		return
	}
	orgID = ctx.GetHeader("Organization-Id")
	if orgID == "" {
		err = errors.New("Organization-Id can not be empty")
		return
	}

	return
}
                                                                                                                                                                                                                                                                                                                                                                                                                                               v1.1/responses/payment/payment.go                                                                   0000644 0001750 0001750 00000011662 13325354064 020470  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package payment

import (
	"sort"
	"strconv"
	"sync"

	pb "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/protofiles"
)

//HTTPHeader json http header
type HTTPHeader struct {
	Field string `json:"field"`
	Value string `json:"string"`
}

//Info json payment info
type Info struct {
	Form     *Form     `json:"form"`
	Request  *Request  `json:"request"`
	Messages []Message `json:"messages,omitempty"`
}

//Fill fill Info from *pb.LkUserReceiptsPaymentInfo
func (i *Info) Fill(m *pb.LkUserReceiptsPaymentInfo) {
	var wg sync.WaitGroup
	wg.Add(3)
	go func() {
		defer wg.Done()
		i.Form.Fill(m)
	}()
	go func() {
		defer wg.Done()
		i.Request.Fill(m)
	}()
	go func() {
		defer wg.Done()
	}()
	wg.Wait()

}

//Request json payument request
type Request struct {
	URL        string            `json:"url"`
	Headers    []HTTPHeader      `json:"headers"`
	Parameters map[string]string `json:"parameters"`
}

//Fill fill Request from *pb.LkUserReceiptsPaymentInfo
func (r *Request) Fill(m *pb.LkUserReceiptsPaymentInfo) {
	r.URL = "https://pay.pscb.ru/"
	r.fillHeaders(m)
	r.Parameters["service"] = m.GetService()
	r.Parameters["attr_2"] = m.GetAddress()
	r.Parameters["attr_3"] = m.GetFlatNumber()
	r.Parameters["attr_5"] = strconv.FormatUint(uint64(m.GetHousesCardId()), 10)
	r.Parameters["attr_6"] = m.GetEmail()
}

func (r *Request) fillHeaders(m *pb.LkUserReceiptsPaymentInfo) {
	r.Headers = []HTTPHeader{
		HTTPHeader{
			Field: "Host",
			Value: "pay.pscb.ru",
		},
		HTTPHeader{
			Field: "Accept",
			Value: "text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8",
		},
		HTTPHeader{
			Field: "Accept-Language",
			Value: "ru-RU,ru;q=0.8,en-US;q=0.5,en;q=0.3",
		},
		HTTPHeader{
			Field: "Referer",
			Value: "http://cabinet.kvado.ru/payonline",
		},
		HTTPHeader{
			Field: "Content-Type",
			Value: "application/x-www-form-urlencoded",
		},
		HTTPHeader{
			Field: "Connection",
			Value: "keep-alive",
		},
		HTTPHeader{
			Field: "Upgrade-Insecure-Requests",
			Value: "1",
		},
	}
}

//Form json payment form
type Form struct {
	Payer      FormValue `json:"payer,omitempty"`
	Account    FormValue `json:"account,omitempty"`
	Period     FormValue `json:"period,omitempty"`
	Unit       FormValue `json:"unit,omitempty"`
	Sum        FormValue `json:"sum,omitempty"`
	Surcharge  FormValue `json:"surcharge,omitempty"`
	Commission FormValue `json:"commission,omitempty"`
	Cards      []string  `json:"cards,omitempty"`
}

//SetPaymentPeriod apply period to Form
func (f *Form) SetPaymentPeriod(m *pb.LkUserReceiptsPaymentPeriod) {
	f.Period.Value = formatPeriod(m.GetPeriod())
	f.Sum.Value = m.GetTotal()
}

//Fill fill Form from *pb.LkUserReceiptsPaymentInfo
func (f *Form) Fill(m *pb.LkUserReceiptsPaymentInfo) {
	go f.fillPeriod(m)
	f.Sum = FormValue{
		Value: m.GetTotal(),
		Param: "amount",
	}
	f.Payer = FormValue{
		Value: m.GetPayer(),
	}
	f.Account = FormValue{
		Value: m.GetAccount(),
		Param: "account",
	}
	f.Unit = FormValue{
		Value: m.GetUnit(),
	}
	f.Commission = FormValue{
		Value: m.GetCommission(),
	}
	f.Surcharge = FormValue{
		Value: m.GetSurcharge(),
		Param: "attr_7",
	}
	f.Cards = []string{"visa", "mastercard", "mir"}
}

func (f *Form) fillPeriod(m *pb.LkUserReceiptsPaymentInfo) {
	p := PeriodAsk(m.GetAllowedPeriods())
	l := len(p)
	if l > 0 {
		sort.Sort(p)
		f.Period = FormValue{}
		f.Period.Value = formatPeriod(p[0].GetPeriod())
		f.Period.Params = make(map[string]string)
		f.Period.Params["attr_1"] = "mm/yy"
		f.Period.Params["month"] = "mm"
		f.Period.Params["year"] = "yyyy"
		f.Period.Values = make([]AllowedValue, l)
		for i, v := range p {
			f.Period.Values[i].Value = formatPeriod(v.GetPeriod())
			if v.GetTotal() >= 0 {
				f.Period.Values[i].Update = make([]UpdateFormValue, 1)
				f.Period.Values[i].Update[0] = UpdateFormValue{
					Field: "sum",
					Value: v.GetTotal(),
				}
			}
		}
	}
}

//AllowedValue json allowed value for form values
type AllowedValue struct {
	Value  interface{}       `json:"value"`
	Update []UpdateFormValue `json:"update,omitempty"`
}

//UpdateFormValue json update struct for form values
type UpdateFormValue struct {
	Field string      `json:"field"`
	Value interface{} `json:"value"`
}

//FormValue struct for json form value
type FormValue struct {
	Value  interface{}       `json:"value"`
	Values []AllowedValue    `json:"values,omitempty"`
	Param  string            `json:"param,omitempty"`
	Params map[string]string `json:"params,omitempty"`
}

//NewPaymentInfo init new *Info
func NewPaymentInfo() *Info {
	i := new(Info)
	i.Messages = []Message{}
	i.Form = newPaymentForm()
	i.Request = newPaymentRequest()
	return i
}

func newPaymentForm() *Form {
	f := new(Form)
	f.Cards = []string{}
	return f
}

func newPaymentRequest() *Request {
	r := new(Request)
	r.Headers = []HTTPHeader{}
	r.Parameters = map[string]string{}
	return r
}

func formatPeriod(p *pb.LkUserReceiptsPeriod) string {
	s := strconv.FormatUint(uint64(p.GetMonth()), 10)
	s += "/"
	s += strconv.FormatUint(uint64(p.GetYear()), 10)
	return s
}
                                                                              v1.1/responses/menu.go                                                                              0000644 0001750 0001750 00000012156 13317156526 016305  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package responses

import (
	"encoding/json"
	"fmt"
	"strconv"
	"time"

	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/configs"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/consts"
	pb "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/protofiles"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/requests"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/tools"
	"golang.org/x/net/context"
	"google.golang.org/grpc"
	"gopkg.in/gin-gonic/gin.v1"
)

// MenuData structure intended for contein data
type MenuData struct {
	Context *gin.Context
	Params  *configs.Params
}

// MenuResponse structure declared request JSON
type MenuResponse struct {
	Menu []MenuItem `json:"menu"`
}

// MenuItem structure declared request JSON
type MenuItem struct {
	ID    string `json:"ID"`
	Badge int64  `json:"badge"`
}

// GetResponse method generate JSON resuqst
func (data *MenuData) GetResponse() (int, []byte, []byte) {

	sessionID := data.Context.GetHeader("Session-Id")
	if sessionID == "" {
		return 400, nil, MakeErrorJSON("Session-Id not be empty")
	}

	lkUserID, statusCode, err := requests.GetLkUserID(data.Params, sessionID)
	if err != nil {
		return statusCode, nil, MakeErrorJSON(err.Error())
	}

	accountIDString := data.Context.GetHeader("Account-Id")
	if sessionID == "" {
		return 400, nil, MakeErrorJSON("Account-Id not be empty")
	}
	accountID, err := strconv.ParseInt(accountIDString, 10, 64)
	if err != nil {
		return 400, nil, MakeErrorJSON("Error parse Account-Id")
	}
	if accountID == 0 {
		return 400, nil, MakeErrorJSON("Account-Id not be empty")
	}

	organizationIDString := data.Context.GetHeader("Organization-Id")
	if organizationIDString == "" {
		return 400, nil, MakeErrorJSON("Organization-Id not be empty")
	}
	organizationID, err := strconv.ParseInt(organizationIDString, 10, 64)
	if err != nil {
		return 400, nil, MakeErrorJSON("Error parse Organization-Id")
	}
	if organizationID == 0 {
		return 400, nil, MakeErrorJSON("Organization-Id not be empty")
	}

	conn, c, callOpts := CreateMenuConnection(data.Params)
	defer conn.Close()

	requestMessage := pb.LkUserMenuRequest{
		OrganizationID: organizationID,
		AccountID:      accountID,
		LkUserID:       lkUserID,
	}
	menuInformation, err := c.GetMenuInformation(context.Background(), &requestMessage, callOpts...)
	if err != nil {
		fmt.Printf("Could not get grpc data: %v\n", err)
		return 500, nil, MakeErrorJSON(err.Error())
	}
	if data.Params.Environment == consts.EnvironmentDev {
		fmt.Printf("GetMenuInformation gRPC response: %#v\n", menuInformation)
	}
	respStruct := MenuResponse{}
	respStruct.mapData(data.Params, menuInformation)
	res, _ := json.Marshal(respStruct)
	return 200, res, nil
}

func (menu *MenuResponse) mapData(params *configs.Params, menuInfo *pb.LkUserMenuInformation) {

	var lkCategoriesList []int64
	for _, menu := range menuInfo.Menu {
		if tools.InArrayInt64(menu.GetLkCategoriesID(), lkCategoriesList) == false {
			lkCategoriesList = append(lkCategoriesList, menu.GetLkCategoriesID())
		}
	}

	var menuItemsList []MenuItem
	if tools.InArrayInt64(31, lkCategoriesList) {
		menuItemsList = append(menuItemsList, MenuItem{
			ID:    "meters",
			Badge: 0,
		})
	} else if tools.InArrayInt64(35, lkCategoriesList) {
		menuItemsList = append(menuItemsList, MenuItem{
			ID:    "reduced_meters",
			Badge: 0,
		})
	}

	if tools.InArrayInt64(8, lkCategoriesList) || tools.InArrayInt64(36, lkCategoriesList) {
		menuItemsList = append(menuItemsList, MenuItem{
			ID:    "payment",
			Badge: 0,
		})
	}

	if tools.InArrayInt64(32, lkCategoriesList) || tools.InArrayInt64(36, lkCategoriesList) {
		menuItemsList = append(menuItemsList, MenuItem{
			ID:    "receipts",
			Badge: 0,
		})
	}

	if tools.InArrayInt64(4, lkCategoriesList) {
		menuItemsList = append(menuItemsList, MenuItem{
			ID:    "apartment",
			Badge: 0,
		})
	}

	if tools.InArrayInt64(1, lkCategoriesList) {
		menuItemsList = append(menuItemsList, MenuItem{
			ID:    "house",
			Badge: 0,
		})
	}

	if tools.InArrayInt64(13, lkCategoriesList) {
		menuItemsList = append(menuItemsList, MenuItem{
			ID:    "organization",
			Badge: 0,
		})
	}

	menu.Menu = menuItemsList
}

// CreateMenuConnection function create gRPC connection
func CreateMenuConnection(params *configs.Params) (
	conn *grpc.ClientConn,
	c pb.LkUserMenuClient,
	callOpts []grpc.CallOption,
) {
	opts := []grpc.DialOption{}
	opts = append(opts, grpc.WithInsecure())
	opts = append(opts, grpc.WithTimeout(time.Minute*30))
	opts = append(opts, grpc.WithMaxMsgSize(1024*1024*1024*1)) // 1Gb

	if params.Environment == consts.EnvironmentDev {
		fmt.Printf("gRPC connection to host: %s\n", params.ProfileService)
	}

	// Set up a connection to the server.
	conn, err := grpc.Dial(params.MenuService, opts...)
	if err != nil {
		fmt.Printf("did not connect: %v", err)
	}
	// defer conn.Close()

	c = pb.NewLkUserMenuClient(conn)

	callOpts = []grpc.CallOption{}
	callOpts = append(callOpts, grpc.MaxCallRecvMsgSize(1024*1024*1024*1)) // Receive message size 1Gb
	callOpts = append(callOpts, grpc.MaxCallSendMsgSize(1024*1024*1024*1)) // Send message size 1Gb

	return
}
                                                                                                                                                                                                                                                                                                                                                                                                                  v1.1/responses/error.go                                                                             0000644 0001750 0001750 00000000726 13312745312 016462  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package responses

import (
	"encoding/json"
)

// ErrorResponse structure define error response structure
type ErrorResponse struct {
	Result  string      `json:"result"`
	Title   interface{} `json:"title"`
	Message string      `json:"message"`
}

// MakeErrorJSON function make json response
func MakeErrorJSON(message string) (bytes []byte) {
	resp := ErrorResponse{
		Result:  "error",
		Title:   nil,
		Message: message,
	}
	bytes, _ = json.Marshal(resp)
	return
}
                                          v1.1/responses/receipts/connection.go                                                               0000644 0001750 0001750 00000002366 13306431165 021311  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package receipts

import (
	"fmt"
	"time"

	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/configs"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/consts"
	pb "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/protofiles"
	"google.golang.org/grpc"
)

//CreateReceiptsConnection function create gRPC connection
func CreateReceiptsConnection(params *configs.Params) (
	conn *grpc.ClientConn,
	c pb.LkReceiptsClient,
	callOpts []grpc.CallOption,
) {
	opts := []grpc.DialOption{}
	opts = append(opts, grpc.WithInsecure())
	opts = append(opts, grpc.WithTimeout(time.Second*10))
	opts = append(opts, grpc.WithMaxMsgSize(1024*1024*1024*1)) //1Gb

	if params.Environment == consts.EnvironmentDev {
		fmt.Printf("gRPC connection to host: %s\n", params.ReceiptsService)
	}

	// Set up a connection to the server.
	conn, err := grpc.Dial(params.ReceiptsService, opts...)
	if err != nil {
		fmt.Printf("did not connect: %v", err)
	}

	c = pb.NewLkReceiptsClient(conn)

	callOpts = []grpc.CallOption{}
	callOpts = append(callOpts, grpc.MaxCallRecvMsgSize(1024*1024*1024*1)) //Receive message size 1Gb
	callOpts = append(callOpts, grpc.MaxCallSendMsgSize(1024*1024*1024*1)) //Send message size 1Gb

	return
}
                                                                                                                                                                                                                                                                          v1.1/responses/receipts/receipts.go                                                                 0000644 0001750 0001750 00000003126 13306431165 020763  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package receipts

import (
	"errors"

	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.0/responses"
	"gopkg.in/gin-gonic/gin.v1"
)

type ReceiptsYearsItem struct {
	Title  string `json:"title"`
	Number uint32 `json:"number"`
}

type DescReceiptsYearsItems []ReceiptsYearsItem

func (a DescReceiptsYearsItems) Len() int           { return len(a) }
func (a DescReceiptsYearsItems) Swap(i, j int)      { a[i], a[j] = a[j], a[i] }
func (a DescReceiptsYearsItems) Less(i, j int) bool { return a[i].Number > a[j].Number }

type ReceiptsReceiptsItem struct {
	Number      uint32          `json:"monthNumber"`
	Text        string          `json:"text"`
	DetailText  string          `json:"detailText,omitempty"`
	Color       responses.Color `json:"color,omitempty"`
	ReceiptLink string          `json:"pdf,omitempty"`
}

type DescReceiptsReceiptsItem []ReceiptsReceiptsItem

func (a DescReceiptsReceiptsItem) Len() int           { return len(a) }
func (a DescReceiptsReceiptsItem) Swap(i, j int)      { a[i], a[j] = a[j], a[i] }
func (a DescReceiptsReceiptsItem) Less(i, j int) bool { return a[i].Number > a[j].Number }

func getHeaders(ctx *gin.Context) (
	sessionID string,
	accID string,
	orgID string,
	err error,
) {
	sessionID = ctx.GetHeader("Session-Id")
	if sessionID == "" {
		err = errors.New("Session-Id can not be empty")
		return
	}
	accID = ctx.GetHeader("Account-Id")
	if accID == "" {
		err = errors.New("Account-Id can not be empty")
		return
	}
	orgID = ctx.GetHeader("Organization-Id")
	if orgID == "" {
		err = errors.New("Organization-Id can not be empty")
		return
	}

	return
}
                                                                                                                                                                                                                                                                                                                                                                                                                                          v1.1/responses/receipts/year-response.go                                                            0000644 0001750 0001750 00000002020 13312726345 021735  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package receipts

import (
	"sort"

	humanize "github.com/dustin/go-humanize"
	pb "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/protofiles"
)

//response type for ReceiptsYearData.GetResponse()
type YearResponse struct {
	Year     uint32                 `json:"year"`
	Title    string                 `json:"title"`
	Footer   string                 `json:"footer"`
	Receipts []ReceiptsReceiptsItem `json:"receipts"`
}

func (r *YearResponse) Fill(m *pb.LkUserReceiptsYear) {
	r.Year = m.GetName().GetNumber()
	r.Title = m.GetName().GetTitle()

	p := m.GetReceipts().GetCells()
	r.Receipts = make([]ReceiptsReceiptsItem, len(p))
	for i, p := range p {
		r.Receipts[i] = ReceiptsReceiptsItem{
			Number:      uint32(p.GetMonthNumber()),
			Text:        p.GetMonthName(),
			ReceiptLink: p.GetPdfLink(),
		}
		if s := p.GetSum(); s != 0 {
			text := humanize.FormatFloat(floatFormat, s)
			text += " ₽"
			r.Receipts[i].DetailText = text
			//@TODO colors
		}
	}
	sort.Sort(DescReceiptsReceiptsItem(r.Receipts))
}
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                v1.1/responses/receipts/receipts-year-data.go                                                       0000644 0001750 0001750 00000004300 13306431165 022623  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package receipts

import (
	"context"
	"encoding/json"
	"fmt"
	"strconv"

	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/configs"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/consts"
	pb "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/protofiles"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/requests"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.0/responses"
	"google.golang.org/grpc/metadata"
	"gopkg.in/gin-gonic/gin.v1"
)

// ReceiptsYearData structure intended for contein data
type ReceiptsYearData struct {
	Context *gin.Context
	Params  *configs.Params
}

// GetResponse method generate JSON response
func (data *ReceiptsYearData) GetResponse() (int, []byte, []byte) {

	sessionID, accID, orgID, err := getHeaders(data.Context)
	if err != nil {
		return 400, nil, responses.MakeErrorJSON(err.Error())
	}

	lkUserID, statusCode, err := requests.GetLkUserID(data.Params, sessionID)
	if err != nil {
		return statusCode, nil, responses.MakeErrorJSON(err.Error())
	}

	conn, c, callOpts := CreateReceiptsConnection(data.Params)
	defer conn.Close()

	a, err := strconv.ParseUint(accID, 10, 32)
	if err != nil {
		return 400, nil, responses.MakeErrorJSON("Bad Account-Id")
	}

	yearParam := data.Context.Param("year")

	if data.Params.Environment == consts.EnvironmentDev {
		fmt.Printf("Receipts Year: %v\n", yearParam)
	}

	yearVal, err := strconv.ParseUint(yearParam, 10, 32)
	if err != nil {
		return 500, nil, responses.MakeErrorJSON("Invalid year format")
	}

	r := pb.LkUserReceiptsReceiptsRequest{
		AccountId: uint32(a),
		Year:      uint32(yearVal),
	}

	ctx := metadata.AppendToOutgoingContext(
		context.Background(),
		"lkuserid",
		strconv.FormatInt(lkUserID, 10),
		"organizationid",
		orgID,
	)

	y, err := c.GetReceipts(ctx, &r, callOpts...)
	if err != nil {
		fmt.Printf("Could not get grpc data: %v\n", err)
		return 500, nil, responses.MakeErrorJSON(err.Error())
	}

	if data.Params.Environment == consts.EnvironmentDev {
		fmt.Printf("GetReceiptsInformation gRPC response: %#v\n", y)
	}

	rr := YearResponse{}
	rr.Fill(y)

	res, _ := json.Marshal(rr)
	return 200, res, nil
}
                                                                                                                                                                                                                                                                                                                                v1.1/responses/receipts/receipts-month-data.go                                                      0000644 0001750 0001750 00000006733 13313205743 023023  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package receipts

import (
	"context"
	"encoding/json"
	"fmt"
	"strconv"
	"sync"

	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/configs"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/consts"
	pb "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/protofiles"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/requests"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.0/responses"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.1/responses/payment"
	"google.golang.org/grpc/metadata"
	"gopkg.in/gin-gonic/gin.v1"
)

// ReceiptsMonthData structure intended for contein data
type ReceiptsMonthData struct {
	Context *gin.Context
	Params  *configs.Params
}

func (data *ReceiptsMonthData) requestParams() (
	m uint64,
	y uint64,
	err error,
) {
	y, err = strconv.ParseUint(data.Context.Param("year"), 10, 32)
	if err != nil {
		return
	}
	m, err = strconv.ParseUint(data.Context.Param("month"), 10, 32)
	return
}

// GetResponse method generate JSON response
func (data *ReceiptsMonthData) GetResponse() (int, []byte, []byte) {
	m, y, err := data.requestParams()
	if err != nil {
		return 500, nil, responses.MakeErrorJSON(err.Error())
	}

	sID, aID, oID, err := getHeaders(data.Context)
	if err != nil {
		return 400, nil, responses.MakeErrorJSON(err.Error())
	}

	uID, statusCode, err := requests.GetLkUserID(data.Params, sID)
	if err != nil {
		return statusCode, nil, responses.MakeErrorJSON(err.Error())
	}

	conn, c, callOpts := CreateReceiptsConnection(data.Params)
	defer conn.Close()

	a, err := strconv.ParseUint(aID, 10, 32)
	if err != nil {
		return 400, nil, responses.MakeErrorJSON("Bad Account-Id")
	}

	ctx := metadata.AppendToOutgoingContext(
		context.Background(),
		"lkuserid",
		strconv.FormatInt(uID, 10),
		"organizationid",
		oID,
	)
	rr := newReceiptResponce()
	var wg sync.WaitGroup
	ce := make(chan error)
	cd := make(chan struct{})

	wg.Add(2)
	go func() {
		defer wg.Done()
		r := pb.LkUserReceiptsReceiptRequest{
			AccountId: uint32(a),
			Year:      uint32(y),
			Month:     pb.LkUserReceiptsMonth(m),
		}
		message, err := c.GetReceipt(ctx, &r, callOpts...)
		if err != nil {
			ce <- err
			return
		}
		if data.Params.Environment == consts.EnvironmentDev {
			fmt.Printf("GetPaymentInformation gRPC response: %#v\n\n", message)
		}
		rr.Fill(message)
	}()
	go func() {
		defer wg.Done()
		pr := &pb.LkUserReceiptsPaymentRequest{AccountId: uint32(a)}
		pi, err := c.GetPaymentInfo(ctx, pr, callOpts...)
		if err != nil {
			ce <- err
			return
		}

		if data.Params.Environment == consts.EnvironmentDev {
			fmt.Printf("GetPaymentInformation gRPC response: %#v\n\n", pi)
		}

		switch pi.PaymentInfo.(type) {
		case *pb.LkUserReceiptsPaymentResponse_Info:
			if len(pi.GetInfo().AllowedPeriods) == 0 {
				return
			}
			rr.Summary.Payment = payment.NewPaymentInfo()
			rr.Summary.Payment.Fill(pi.GetInfo())
		Loop:
			for _, p := range pi.GetInfo().AllowedPeriods {
				if uint64(p.Period.Month) == m && uint64(p.Period.Year) == y {
					rr.SetPaymentPeriod(p)
					break Loop
				}
			}
		}
	}()

	go func() {
		wg.Wait()
		close(cd)
	}()

	select {
	case err := <-ce:
		fmt.Printf("Could not get grpc data: %s\n\n", err.Error())
		return 500, nil, responses.MakeErrorJSON(err.Error())
	case <-cd:
	}

	if data.Params.Environment == consts.EnvironmentDev {
		fmt.Printf("ReceiptResponce: %#v\n", rr)
	}
	res, _ := json.Marshal(rr)
	return 200, res, nil
}
                                     v1.1/responses/receipts/receipts-data.go                                                            0000644 0001750 0001750 00000003557 13306431165 021702  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package receipts

import (
	"context"
	"encoding/json"
	"fmt"
	"strconv"

	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/configs"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/consts"
	pb "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/protofiles"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/requests"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.0/responses"
	"google.golang.org/grpc/metadata"
	"gopkg.in/gin-gonic/gin.v1"
)

//ReceiptsData structure intended for contein data
type ReceiptsData struct {
	Context *gin.Context
	Params  *configs.Params
}

//GetResponse method generate JSON response
func (data *ReceiptsData) GetResponse() (int, []byte, []byte) {

	sessionID, accID, orgID, err := getHeaders(data.Context)
	if err != nil {
		return 400, nil, responses.MakeErrorJSON(err.Error())
	}

	lkUserID, statusCode, err := requests.GetLkUserID(data.Params, sessionID)
	if err != nil {
		return statusCode, nil, responses.MakeErrorJSON(err.Error())
	}

	conn, c, callOpts := CreateReceiptsConnection(data.Params)
	defer conn.Close()

	a, err := strconv.ParseUint(accID, 10, 32)
	if err != nil {
		return 400, nil, responses.MakeErrorJSON("Bad Account-Id")
	}
	r := pb.LkUserReceiptsYearsRequest{
		AccountId: uint32(a),
	}

	ctx := metadata.AppendToOutgoingContext(
		context.Background(),
		"lkuserid",
		strconv.FormatInt(lkUserID, 10),
		"organizationid",
		orgID,
	)

	y, err := c.GetYears(ctx, &r, callOpts...)
	if err != nil {
		fmt.Printf("Could not get grpc data: %v\n", err)
		return 500, nil, responses.MakeErrorJSON(err.Error())
	}

	if data.Params.Environment == consts.EnvironmentDev {
		fmt.Printf("GetProfileInformation gRPC response: %#v\n", y)
	}

	rr := ReceiptsResponse{}
	rr.Fill(y)

	res, _ := json.Marshal(rr)
	return 200, res, nil
}
                                                                                                                                                 v1.1/responses/receipts/receipt-response.go                                                         0000644 0001750 0001750 00000007163 13325353213 022437  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package receipts

import (
	"fmt"
	"strconv"
	"sync"

	humanize "github.com/dustin/go-humanize"
	pb "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/protofiles"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.0/responses"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.1/responses/payment"
)

const (
	floatFormat = "# ###,##"
)

type ReceiptResponse struct {
	Summary  ReceiptResponseSummary  `json:"summary"`
	Accruals ReceiptResponseAccruals `json:"accruals"`
}

type ReceiptResponseSummary struct {
	Header  string                     `json:"header,omitempty"`
	Footer  string                     `json:"footer,omitempty"`
	Color   responses.Color            `json:"color,omitempty"`
	Payment *payment.Info              `json:"payment,omitempty"`
	Cells   []ReceiptResponseTableCell `json:"cells"`
}
type ReceiptResponseTableCell struct {
	Text       string `json:"text"`
	DetailText string `json:"detailText"`
}
type ReceiptResponseAccruals struct {
	Header string                     `json:"header,omitempty"`
	Footer string                     `json:"footer,omitempty"`
	Cells  []ReceiptResponseTableCell `json:"cells"`
}

func newReceiptResponce() *ReceiptResponse {
	r := new(ReceiptResponse)
	r.Accruals = *newReceiptResponseAccruals()
	r.Summary = *newReceiptResponseSummary()
	return r
}
func newReceiptResponseAccruals() *ReceiptResponseAccruals {
	a := new(ReceiptResponseAccruals)
	a.Cells = []ReceiptResponseTableCell{}
	return a
}
func newReceiptResponseSummary() *ReceiptResponseSummary {
	s := new(ReceiptResponseSummary)
	s.Cells = []ReceiptResponseTableCell{}
	return s
}

func (r *ReceiptResponse) SetPaymentPeriod(m *pb.LkUserReceiptsPaymentPeriod) {
	r.Summary.Payment.Form.SetPaymentPeriod(m)
}

func (r *ReceiptResponse) Fill(m *pb.LkUserReceiptsReceipt) {
	var wg sync.WaitGroup
	wg.Add(2)
	go func() {
		defer wg.Done()
		r.fillAccruals(m)
	}()
	go func() {
		defer wg.Done()
		r.fillSummary(m)
	}()
	wg.Wait()
}

func (r *ReceiptResponse) fillAccruals(m *pb.LkUserReceiptsReceipt) {
	r.Accruals.Header = "Итого начислено по услугам"
	r.Accruals.Cells = make([]ReceiptResponseTableCell, len(m.GetAcruals())+1)
	sum := float64(0)
	idx := 0
	for i, m := range m.GetAcruals() {
		cell := ReceiptResponseTableCell{
			Text:       m.GetTitle(),
			DetailText: humanize.FormatFloat(floatFormat, m.GetTotal()),
		}
		sum += m.GetTotal()
		r.Accruals.Cells[i] = cell
		idx = i
	}
	r.Accruals.Cells[idx+1] = ReceiptResponseTableCell{
		Text:       "ИТОГО",
		DetailText: humanize.FormatFloat(floatFormat, sum),
	}
}

func (r *ReceiptResponse) fillSummary(m *pb.LkUserReceiptsReceipt) {
	saldo := m.GetSaldo()
	sLen := 3
	lastIdx := 2
	if saldo == 0 {
		sLen = 2
		lastIdx = 1
	}
	r.Summary.Cells = make([]ReceiptResponseTableCell, sLen)
	r.Summary.Cells[0] = ReceiptResponseTableCell{
		Text:       "Начислено",
		DetailText: humanize.FormatFloat(floatFormat, m.GetTotalAccruals()),
	}

	if saldo < 0 {
		r.Summary.Cells[1] = ReceiptResponseTableCell{
			Text:       "Переплата",
			DetailText: humanize.FormatFloat(floatFormat, -1*saldo),
		}
	} else if saldo > 0 {
		sd := m.GetDateSaldo()
		sdt := fmt.Sprintf("%02d", sd.GetDay()) + "."
		sdt += fmt.Sprintf("%02d", sd.GetMonth()) + "."
		sdt += strconv.FormatUint(uint64(sd.GetYear()), 10)
		r.Summary.Cells[1] = ReceiptResponseTableCell{
			Text:       "Долг на " + sdt,
			DetailText: humanize.FormatFloat(floatFormat, saldo),
		}
	}
	r.Summary.Cells[lastIdx] = ReceiptResponseTableCell{
		Text:       "К оплате",
		DetailText: humanize.FormatFloat(floatFormat, m.GetTotal()),
	}
}
                                                                                                                                                                                                                                                                                                                                                                                                             v1.1/responses/receipts/receipts-responce.go                                                        0000644 0001750 0001750 00000003024 13312726343 022576  0                                                                                                    ustar   urfinjuezz                      urfinjuezz                                                                                                                                                                                                             package receipts

import (
	"sort"

	humanize "github.com/dustin/go-humanize"
	pb "gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/protofiles"
	"gitlab.private.kvado.ru/kvado-api/mobile/cabinet-mobile-api-entry-point/v1.1/responses/payment"
)

//response type for ReceiptsData.GetResponse()
type ReceiptsResponse struct {
	Messages []payment.Message      `json:"messages"`
	Years    []ReceiptsYearsItem    `json:"years"`
	Year     uint32                 `json:"year"`
	Title    string                 `json:"title"`
	Footer   string                 `json:"footer"`
	Receipts []ReceiptsReceiptsItem `json:"receipts"`
}

func (r *ReceiptsResponse) Fill(m *pb.LkUserReceiptsYears) {
	r.Messages = make([]payment.Message, 0)
	r.Year = m.GetCurrentYear().GetName().GetNumber()
	r.Title = m.GetCurrentYear().GetName().GetTitle()
	y := m.GetYears()
	r.Years = make([]ReceiptsYearsItem, len(y))
	for i, y := range y {
		r.Years[i] = ReceiptsYearsItem{
			Title:  y.GetTitle(),
			Number: y.GetNumber(),
		}
	}
	sort.Sort(DescReceiptsYearsItems(r.Years))
	p := m.GetCurrentYear().GetReceipts().GetCells()
	r.Receipts = make([]ReceiptsReceiptsItem, len(p))
	for i, p := range p {
		r.Receipts[i] = ReceiptsReceiptsItem{
			Number:      uint32(p.GetMonthNumber()),
			Text:        p.GetMonthName(),
			ReceiptLink: p.GetPdfLink(),
		}
		if s := p.GetSum(); s != 0 {
			text := humanize.FormatFloat(floatFormat, s)
			text += " ₽"
			r.Receipts[i].DetailText = text
			//@TODO colors
		}
	}
	sort.Sort(DescReceiptsReceiptsItem(r.Receipts))
}
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
