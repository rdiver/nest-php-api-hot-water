## UPDATE 15/11/2019

Sorry everyone, Google has broken this and added a reCaptcha to the login page that means that automation of logging in is now well and truly broken. It was great while it lasted but I don't think it will be fixable.

---

## UPDATE 25/11/2019

Malcolm has come up with an android workaround thats worth a read dated. November 20, 2019 at 3:12 pm
http://www.aimlesswandering.uk/web/2017/11/nest-thermostat-hot-water-controlled-by-alexa/

I have also found another way that I will post once I have a more robust script. It uses headless chrome, python and selenium.

---

# Nest PHP API to control Hot Water (unofficial)

PHP API to control Hot Water for the Nest Thermostat (UK)

After making several requests on the Nest Community forums, to be blown of by the Nest admins I decided to reverse engineer the web app to create a script that can boost hot water so I can use my alexa to control the hot water.
https://nestdevelopers.io/t/api-for-hot-water-control-3rd-gen-nest-thermostat/197
https://nestdevelopers.io/t/hot-water-boost-api-is-there-one/626
https://nestdevelopers.io/t/why-does-the-api-still-not-control-hot-water/862
and more recently https://nestdevelopers.io/t/nest-hot-water-api/931

My aim was to keep it as simple as possible, not my best work nor is it commented well but it works. Might neaten it in the future.
Thanks to Andy Blyler for his original curl functions and work. https://github.com/ablyler/nest-php-api

I will update this page to include the information I post on my blog but for now I've not written it :)
Blog post -> http://www.aimlesswandering.uk/web/2017/11/nest-thermostat-hot-water-controlled-by-alexa/


## Usage

```php
// include the nest api library
include_once('./nest-php-api.php');

// create new nest object w/ login information
$nest = new Nest('john@doe.com', 'password');

// boost hot water for 30 minutes
$nest->setHotWaterBoost(30);

// boost hot water for X minutes
$nest->setHotWaterBoost(X);

// cancel the current boost
$nest->cancelHotWaterBoost();

// or you can also cancel by calling the following
$nest->setHotWaterBoost(0);

// when you either set or cancel the boost a json response will be returned
{"success":true,"code":200,"data":"Boom, hot water changed. Or you set it to the same as before."}

```
