Yii 2 GeoIP extension
=====================



Provides information about geographical location of user by IP address.

Currently available:
* Country
* City
* Latitude, Longitude
* Country ISO Code

## Install

Run

```bash
$ php composer.phar require riskivy/yii2-geoip "~1.0"
```

#### OR 

add to your `composer.json`

```json
{
    "require": {
        "riskivy/yii2-geoip": "~1.0"
    }
}
```

and run

```bash
$ php composer update
```


## Usage

### Like component

```php
<?php

$config = [
    ...
    'components' => [
        'geoip' => [
            'class' => 'riskivy\GeoIP\GeoIP',
            'dbPath' => Yii::getAlias('@example/maxmind/database/city.mmdb')
        ],
    ]
    ...
];
```

somewhere in code

```php
$ip = Yii::$app->geoip->ip(); // current user ip

$ip = Yii::$app->geoip->ip("208.113.83.165");

$ip->city; // "San Francisco"
$ip->country; // "United States"
$ip->location->lng; // 37.7898
$ip->location->lat; // -122.3942
$ip->isoCode; // "US"

```

### Like object directly somewhere in your application

```php
$geoip = new \riskivy\GeoIP\GeoIP();
$ip = $geoip->ip("208.113.83.165");

$ip->city; // "San Francisco"
$ip->country; // "United States"
$ip->location->lng; // 37.7898
$ip->location->lat; // -122.3942
$ip->isoCode;  // "US"
```

FAQ
---

__Q__: I get error `Required database not available at /usr/share/GeoIP/GeoIPCity.dat.`. What to do?

__A__: Download this file [http://geolite.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz](http://geolite.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz) and ungzip it into `/usr/share/GeoIP/GeoIPCity.dat`
