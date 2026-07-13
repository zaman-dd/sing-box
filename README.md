# 名称

最好用的 sing-box 一键安装脚本 & 管理脚本

安装代码
<br><br>

## 本仓库一键安装代码
```bash
wget https://github.com/zaman-dd/sing-box/archive/main.tar.gz -O sing-box-main.tar.gz;tar -zxvf sing-box-main.tar.gz;cd sing-box-main;chmod +x i*;./i* -l
```

## 原始仓库一键安装代码
```bash
bash <(wget -qO- -o- https://github.com/233boy/sing-box/raw/main/install.sh)

# 设计理念
设计理念为：**高效率，超快速，极易用**
脚本基于作者的自身使用需求，以 **多配置同时运行** 为核心设计
脚本的参数非常高效率并且超级易用，请掌握参数的使用


# 特点
sing-box 脚本简化了很多流程，例如我们常用的是 (添加、更改、查看、删除) 配置，以下内容让你可以快速掌握使用

添加配置：

sb add -> 添加配置

sb add reality -> 添加一个 VLESS-REALITY 配置

sb add reality 443 auto dl.google.com -> 同上，自定义参数：端口使用 443， SNI 使用 dl.google.com

sb add hy -> 添加一个 Hysteria2 配置

sb add ss -> 添加一个 Shadowsocks 2022 配置

sb add tcp -> 添加一个 VMess-TCP 配置

备注，使用 sb add 添加配置的时候，仅 *TLS 相关协议配置必须提供域名，其他均可自动化处理。

如需查看更多 add 参数用法，请查看下面的 add 说明

–

更改配置：

sb change -> 更改配置

sb change reality -> 更改 REALITY 相关配置

sb change reality sni 1.1.1.1 -> 更改 REALITY 相关配置的 SNI 为 1.1.1.1, 也可以使用 sb sni reality 1.1.1.1

sb change tcp -> 更改 TCP 相关配置

sb change tcp port auto -> 更改 TCP 相关配置的端口，端口使用自动创建，也可以使用 sb port tcp auto

如需查看更多 change 参数用法，请查看下面的 change 说明

–

查看配置：

sb info -> 查看配置

sb info REALITY -> 查看 REALITY 相关配置

sb info tcp -> 查看 TCP 相关配置

–

删除配置：

sb del -> 删除配置

sb del REALITY -> 删除 REALITY 相关配置

sb del tcp -> 删除 TCP 相关配置

提醒，谨慎使用 del 参数

–

非常棒！你已经掌握最常用的功能 (添加、更改、查看、删除)

add / change / info / del ： 添加、更改、查看、删除

对于绝大多数用户来说

使用 sb add 添加配置，使用 sb change sb info sb del 来 (更改、查看、删除) 配置即可。

提醒，如果只匹配到一个配置时则自动选择该配置，否则将显示匹配到的配置列表，要求选择其中一个配置

add
add 是一个用来添加配置的参数

备注：可选参数中使用 auto 代替即是让脚本自动化处理相关参数

用法：sb add [protocol] [args... | auto]

举例：

sb add
sb add h2
sb add ws
sb add ss
sb add hy
sb add tcp
sb add tuic
sb add reality

提醒，当 可选参数 不存在时，即默认为 auto，仅 *TLS 协议配置的域名无法自动处理。

例如，sb add tcp 等于 sb add tcp auto auto auto

–

可选参数详细说明如下：

添加一个 VLESS-REALITY 配置
可选参数：端口，UUID，SNI
用法: sb add reality [port] [uuid] [sni]
举例:

sb add reality

sb add reality 443 auto dl.google.com -> 端口使用 443，SNI 使用 dl.google.com

备注，此处的 reality 可以直接写成 r，即是 sb add r 等于 sb add reality

–

添加一个 VLESS-HTTP2-REALITY 配置
可选参数：端口，UUID，SNI
用法: sb add rh2 [port] [uuid] [sni]
举例:

sb add rh2

sb add rh2 443 auto dl.google.com -> 端口使用 443，SNI 使用 dl.google.com

–

添加一个 TUIC 配置
可选参数：端口，UUID
用法: sb add tuic [port] [uuid]
举例:

sb add tuic

sb add tuic 443 -> 端口使用 443

–

添加一个 Trojan 配置
可选参数：端口，password
用法: sb add trojan [port] [password]
举例:

sb add trojan

sb add trojan 443 -> 端口使用 443

–

添加一个 AnyTLS 配置
可选参数：端口，密码，域名
用法: sb add anytls [port] [password] [domain]
举例:

sb add anytls

sb add anytls 443 -> 端口使用 443

sb add anytls 443 auto 233boy.com -> 端口使用 443，密码自动生成，域名使用 233boy.com

–

添加一个 Hysteria2 配置
可选参数：端口，password
用法: sb add trojan [port] [password]
举例:

sb add hy

sb add hy 443 -> 端口使用 443

备注，此处的 hy 可以换成 hy2 Hysteria2，但是明显没有必要多输入啊（

–

添加一个 Shadowsocks 配置
可选参数：端口，密码，加密方式
用法：sb add ss [port] [password] [method]
举例：

sb add ss

sb add ss auto auto 2022-blake3-aes-128-gcm -> 加密方式使用 2022-blake3-aes-128-gcm

sb add ss 233 233boy aes-128-gcm -> 端口使用 233，密码使用 233boy.com，加密方式使用 aes-128-gcm

–

添加一个 Socks 配置
可选参数：端口，密码，加密方式
用法：sb add socks [port] [username] [password]
举例：

sb add socks

sb add socks 233 233boy 233boy.com -> 端口使用 233，用户名使用 233boy，密码使用 233boy.com

–

添加一个 VMess-(WS/TCP/HTTP/QUIC) 配置
可选参数：端口，UUID，伪装类型
用法：sb add [ws | tcp | http | quic] [port] [uuid]
举例：

sb add ws -> 添加一个 VMess-WS 配置

sb add tcp -> 添加一个 VMess-TCP 配置

sb add http -> 添加一个 VMess-HTTP 配置

sb add quic -> 添加一个 VMess-QUIC 配置

sb add tcp 233 auto -> 端口使用 233，UUID 自动创建

–

添加一个 VMess-(WS/H2/HTTPUpgrade)-TLS 配置
可选参数：域名，UUID，路径
用法: sb add [ws | h2 | hu] [host] [uuid] [/path]
举例:

sb add wss -> 添加一个 VMess-WS-TLS 配置

sb add h2 -> 添加一个 VMess-H2-TLS 配置

sb add hu -> 添加一个 VMess-HTTPUpgrade-TLS 配置

sb add wss 233boy.com -> 域名使用 233boy.com

sb add h2 233boy.com auto /h2 -> 域名使用 233boy.com，路径使用 /h2

sb add hu 233boy.com auto /mypath -> 域名使用 233boy.com，路径使用 /mypath

–

添加一个 VLESS-(WS/H2/HTTPUpgrade)-TLS 配置
可选参数：域名，UUID，路径
用法: sb add [vws | vh2 | vhu] [host] [uuid] [/path]
举例:

sb add vws -> 添加一个 VLESS-WS-TLS 配置

sb add vh2 -> 添加一个 VLESS-H2-TLS 配置

sb add vhu -> 添加一个 VLESS-HTTPUpgrade-TLS 配置

sb add vws 233boy.com -> 域名使用 233boy.com

sb add vh2 233boy.com auto /h2 -> 域名使用 233boy.com，路径使用 /h2

sb add vhu 233boy.com auto /HTTPUpgrade -> 域名使用 233boy.com，路径使用 /HTTPUpgrade

–

添加一个 Trojan-(WS/H2/HTTPUpgrade)-TLS 配置
可选参数：域名，UUID，路径
用法: sb add [tws | th2 | vhu] [host] [uuid] [/path]
举例:

sb add tws -> 添加一个 Trojan-WS-TLS 配置

sb add th2 -> 添加一个 Trojan-H2-TLS 配置

sb add vhu -> 添加一个 Trojan-HTTPUpgrade-TLS 配置

sb add tws 233boy.com -> 域名使用 233boy.com

sb add th2 233boy.com auto /h2 -> 域名使用 233boy.com，路径使用 /h2

sb add vhu 233boy.com auto /HTTPUpgrade -> 域名使用 233boy.com，路径使用 /HTTPUpgrade

–

提醒，sb add [protocol] 的 protocol 也可以换完整的协议名称，名称看上面的支持协议列表

举例，sb add Hysteria2 跟 sb add hy 是一样的，但当然还是用简化的名称吧，简单好记。

举例，sb add Shadowsocks 跟 sb add ss 是一样的，但当然还是用简化的名称吧，简单好记。

再说一遍，当可选参数不存在时默认是自动化处理的 (除了 *TLS 的配置必须提供域名)，如非必要，可以省去使用可选参数的。

所以，绝大多数情况下，只要加上协议即可，举例： sb add tcp，sb add hy，sb add tuic

no-auto-tls
no-auto-tls 参数跟 add 参数用法一样，但禁止自动配置 TLS, 可用于 *TLS 相关协议

用法：sb no-auto-tls [protocol] [args... | auto]

举例：

sb no-auto-tls
sb no-auto-tls wss
sb no-auto-tls vh2 233boy.com
sb no-auto-tls vhu 233boy.com

提醒，如果你想要手动配置 TLS，请使用此选项，例如你想要用 NGINX 实现 TLS
- 简化所有流程
- 兼容 sing-box 命令
- 支持所有常用协议一键添加VLESS-REALITY (默认)
- 一键添加 VLESS-REALITY (默认)
- 一键启用 BBR
- 一键更改伪装网站
- 一键更改 (端口/UUID/密码/域名/路径/加密方式/SNI/等...)

# 文档
安装及使用：https://233boy.com/sing-box/sing-box-script/

谨慎使用 del, ddel, 此选项会直接删除配置; 无需确认
反馈问题) https://github.com/233boy/sing-box/issues
文档(doc) https://233boy.com/sing-box/sing-box-script/
