# nb-captcha
依赖nbframework框架的图形验证码类库

## 安装
> composer require olcx/nb-captcha


##使用

###在控制器里输出验证码

```
public function index($id = "") {
    $captcha = new Captcha([
       // 验证码字符集合
       'codeSet'  => '123456789',
       // 验证码字体大小(px)
       'fontSize' => 35,
       // 是否画混淆曲线
       'useCurve' => false,
       // 验证码图片高度
       'imageH'   => 80,
       // 验证码图片宽度
       'imageW'   => 320,
       // 验证码位数
       'length'   => 5,
       // 验证成功后是否重置
       'reset'    => true
    ]);
    $captcha->show($id);
 }
```

### 控制器里验证
使用TP5的内置验证功能即可
~~~
$this->validate($data,[
    'captcha|验证码'=>'require|captcha'
]);
~~~
或者手动验证
~~~
if(!captcha_check($captcha)){
 //验证失败
};
~~~