## 效果预览

![效果](http://osleeix1f.bkt.clouddn.com/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20180125105013.png)

## 安装

确保你安装了 [Composer](https://getcomposer.org/):

```
composer require sjzlai/code
```
## 配置

1.打开laravel项目中 `config\app.php`

2.找到`providers`数组，在最下面添加` sjzlai\Code\CodeServiceProvider::class`              注意 “**，**”





## 生成验证码

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class IndexController extends Controller
{
    public function imgCode()
    {
         $app = app('code');//可以使用app全局函数 参数为code 生成code实例
         $app->make();    //make() 为生成验证码的方法
         //$app->fontSize = 16;// 设置字体大小        
         //$app->num = 4;// 设置验证码数量
         //$app->width = 100// 设置宽度
         //$app->height = 30// 设置宽度
         //$app->font = ./1.ttf // 设置字体目录
         return $app->get(); //get() 为获取验证码的方法
    }
}

```
## 设置路由文件

设置验证码路由

`routes/web.php`

```
<?php

Route::get('/', function () {
    return view('welcome');
});
Route::get('imgCode',"IndexController@imgCode");
```

## 视图调用

```<img src="/imgCode" art="点击更换"/>```