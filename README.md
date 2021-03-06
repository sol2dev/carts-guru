CartsGuru
=========

[![Latest Stable Version](https://poser.pugx.org/ossbrownie/carts-guru/v/stable)](https://packagist.org/packages/ossbrownie/carts-guru)
[![Total Downloads](https://poser.pugx.org/ossbrownie/carts-guru/downloads)](https://packagist.org/packages/ossbrownie/carts-guru)
[![Latest Unstable Version](https://poser.pugx.org/ossbrownie/carts-guru/v/unstable)](https://packagist.org/packages/ossbrownie/carts-guru)
[![License](https://poser.pugx.org/ossbrownie/carts-guru/license)](https://packagist.org/packages/ossbrownie/carts-guru)

Recover Your Abandoned Carts and Turn Them into Sales.

## curl
A basic CURL wrapper for PHP (see [http://php.net/curl](http://php.net/curl) for more information about the libcurl extension for PHP)

## Requirements
- **PHP** >= 5.3
- **EXT-CURL** = *

## Usage
```php
$cartsGuru = new CartsGuru(
    new HTTPClient(
        new CurlClient(),
        new Config(array(
            'apiAuthKey' => 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx',
        ))
    ),
    'site-id-xxxx-xxxx-xxxx-xxxxxxxxxxxx'
);

$item = new Item(array(
    'id' => 'test-item-0008',
    'label' => 'product',
    'quantity' => 1,
    'totalATI' => 200,
    'totalET' => 150,
    'url' => 'http://site.com/product/0008',
    'imageUrl' => 'http://site.com/product/0008.jpg',
));

$cart = new Cart(
    array(
        'id' => 'test-cart-0008',
        'totalATI' => 200,
        'totalET' => 150,
        'accountId' => '3847569834',
        'firstname' => 'Tester',
        'email' => 'test@site.com',
        'country' => 'United States',
        'countryCode' => 'USA',
    )
);
$cart->addItem($item);
$status = $cartsGuru->trackCart($cart);

$order = new Order(
    array(
        'id' => 'test-order-0008',
        'cartId' => 'test-cart-0008',
        'totalATI' => 200,
        'totalET' => 150,
        'state' => 'approved',
        'accountId' => '3847569834',
        'firstname' => 'Tester',
        'email' => 'test@site.com',
        'country' => 'United States',
        'countryCode' => 'USA',
    )
);
$order->addItem($item);
$status = $cartsGuru->trackOrder($order);
```

## Contact

Problems, comments, and suggestions all welcome: [oss.brownie@gmail.com](mailto:oss.brownie@gmail.com)

