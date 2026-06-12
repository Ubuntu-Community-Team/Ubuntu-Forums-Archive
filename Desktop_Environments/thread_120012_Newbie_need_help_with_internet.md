---
title: "Newbie need help with internet"
date: 2006-01-20
forum: Desktop Environments
---

### Post by ThirdGenLS1 on 2006-01-20
alright I just booted up ubuntu last night and i can't get it to connect to the internet if my life depended on it. I have a wireless card but for right now i'm just trying to get it working with my etho cord. When i plug the cord in it reads that i'm connnected but i just can't get any internet. Its in DHCP mode right now and when i enter in the ifconfig eth0 in the terminal i get

Link encap:Ethernet HWaddr 00:08:02: DO:35:58
inet6 addr: fe80::208:3558/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1355 errors:0 drpped:0 overruns:0 frame:0
TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txpuenelen:100
RX bytes:62999 (61.5 KiB) TX bytes:2394 (2.3 KiB)
interrupt:11 Base adress:0xa800

and when i enter lspci | Eth
ethernet controller: Realtek Semiconductor Co., Ltd. Rtl-8139/8139c/8139C+ (rev 20)

When intering route -n it shows nothing in the gateway, genmask, ETC.

Any help would be greatly appreciated, cause i'm pretty excited to get this up and running.

---

### Post by bschuteker on 2006-01-20
I went a different route as I am a gui kind of guy. Try system > administration > Networking, then click on your eth0 and click activate. Then tell it to use DHCP

It worked for me.

---

### Post by ThirdGenLS1 on 2006-01-20
tried that and still doesnt work. thanks tho

---

### Post by carlosqueso on 2006-01-20
try typing ```
ifdown eth0
ifup eth0
``` and post what each of those say.  (it may just start working, that's what happens sometimes with my wireless card)

---

### Post by ThirdGenLS1 on 2006-01-20
both just said 

ifdown: failed to open statefile /etc/network/run/ifstate: permission denied

---

### Post by Aramil on 2006-01-20
Do it as root

---

### Post by ThirdGenLS1 on 2006-01-20
got it working thanks a lot guys, just needed to unplug and plug back in my router.

Now just need to figure out how to get my wireless card to work, but now i can at least download drivers to my comp now if needed.

---

