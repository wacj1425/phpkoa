PHPKoa 
=================


安装
=======
```
composer require naka1205/phpkoa
```

使用
=======

```php
<?php
require __DIR__ . '/vendor/autoload.php';

use Naka507\Koa\Application;
use Naka507\Koa\Context;

$app = new Application();

$app->υse(function(Context $ctx) {
    $ctx->status = 200;
    $ctx->body = "<h1>Hello World</h1>";
});

$app->listen(3000);

```

```php
<?php
require __DIR__ . '/../vendor/autoload.php';

use Naka507\Koa\Application;
use Naka507\Koa\Context;
use Naka507\Koa\Error;
use Naka507\Koa\Timeout;
use Naka507\Koa\Router;

$app = new Application();
$app->υse(new Error());
$app->υse(new Timeout(1));

$router = new Router();
$router->get('/demo1', function(Context $ctx, $next) {
    $ctx->body = "demo1";
});
$router->get('/demo2', function(Context $ctx, $next) {
    $ctx->body = "demo2";
});
$app->υse($router->routes());

$app->listen(3000);

```