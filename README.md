# yii2-ccavenue
Yii2 [ccavenue](https://www.ccavenue.com/) payment gateway integration.

## Installation
1.Make a components folder to your project if it does not exist.  
  Copy the yii2-ccvaenue/components/Ccavenue Class into the folder.  

2.Now open the yii2-ccvaenue/config folder and copy the function.php file,  paste this into your project config folder.

3.Include the function.php file into the config/web.php file in your project.  
  for refference please check the yii2-ccvaenue/config/web.php file.

4.In yii2-ccvaenue/SiteController before action method i have  
  removed the csrf validation for **payment-process** and **payment-cancel** method, because this   
  2 method will be handle the ccavenue api request.  

5.yii2-ccvaenue/SiteController **actionSubscription** will process your request and submit the request   
  to the ccvaenue payment gateway.  
  ```
  $redirectUrl = Url::to(['site/payment-process'], true);
            $cancelUrl = Url::to(['site/payment-cancel'], true);

            $params = [
                'tid' => time(),
                'merchant_id' => 12345,
                'order_id' => 14523,
                'amount' => 2500,
                'currency' => 'INR',
                'redirect_url' => $redirectUrl,
                'cancel_url' => $cancelUrl,
                'language' => 'EN',
            ];

            \app\components\Ccavenue::form($params, 'auto', 'test', 'websites');
 ```
  
  Here ***auto*** is the submission mode,   
       ***test*** is the name of environment of ccavenue.  
  it will be two test and production.  
       ***websites** is the server name which i use for testing.  
  it can be live,local,websites or anything which u want.  

  for more details check yii2-ccvaenue/components/Ccavenue class.  

6.Copy the yii2-ccvaenue/SiteController ***actionPaymentProcess*** and ***actionPaymentCancel***  
  methods with views(yii2-ccvaenue/views.*)  


  Your are done!!.  


## Note
I have made this for educational purpose also for reducing the development time.  
i did not found any helpful resources for ccavenue payment gateway integration in yii2.  
Hope it will helps someone.  
Good luck!!!  

   

  




