---
title: "Connecting via Cable Modem"
date: 2006-04-09
forum: Desktop Environments
---

### Post by Afief on 2006-04-09
Hello everybody,

I've been living happily with ubuntu at home since i had a router that connected me to the internet, now at my new flat i don't have that luxery, i got a modem from my ISP that works fine with Windows after downloading their installer but won't run in linux, even after downloading their scripts.

I have tried to debug the script, but my knowledge of linux networking is quite limited and i couldn't get it to work.

Things i've noticed are wrong:
1. the interface folder is called dhcp3 not dhcp.
2. the interface file is simply called dhcp.less not dhcp-[interface].less

The modem is connected through a normal Lan interface.

i corrected those things, but still it wouldn't work. those are both scripts they offer(originally written for redhart, 4 years ago)
L2TP Client: [http://cables2.netvision.net.il/linux/l2tp-dialer.tar.gz](http://cables2.netvision.net.il/linux/l2tp-dialer.tar.gz)
PPTP Client Redhat8: [http://cables2.netvision.net.il/linux/nvcbl8.tar.gz](http://cables2.netvision.net.il/linux/nvcbl8.tar.gz)
PPTP Client Redhat7.3 and below: [http://cables2.netvision.net.il/linux/cable-linux.tar.gz](http://cables2.netvision.net.il/linux/cable-linux.tar.gz)

Thanks for your help
Afief

---

