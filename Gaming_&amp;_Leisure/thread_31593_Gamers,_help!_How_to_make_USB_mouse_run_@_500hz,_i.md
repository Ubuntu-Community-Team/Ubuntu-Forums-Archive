---
title: "Gamers, help! How to make USB mouse run @ 500hz, instead of 125hz!"
date: 2005-05-03
forum: Gaming &amp; Leisure
---

### Post by maniac99 on 2005-05-03
Hi there :)

Ok, so Linux by default runs the USB mouse at 125hz.  Which is pretty damn slow.  Some people are even using ps2 mice so they can get a maximum of 200hz.

I found this site which provides a link to a .patch file which can be used to patch a kernel [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=62](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=62) (the patch is here [http://omfg.linux.dk/pub/configurable-hid-mouse-polling/archive/usbhid-readd-kconfig-r2.patch](http://omfg.linux.dk/pub/configurable-hid-mouse-polling/archive/usbhid-readd-kconfig-r2.patch))

The thing is, it doesn't work.  patch -p1 < usbhid-readd-kconfig-r2.patch fails.  Everyone else on other distros is able to get it to work, is this a problem with Ubuntu?

In make menuconfig I can see under USB-Inputs the new option which you change to 2, and it changes the mouses responsiveness from 10ms to 2ms.  However, on reboot of the new kernel, doing cat /proc/bus/usb/devices shows that the mouse is still running at the old 10ms - not 2ms :(

Anyone know how I can fix this?

---

### Post by SteelValor on 2005-05-03
bump

For the love of emp! Help him before he settles for Xbox!

---

### Post by nickless on 2005-05-05
Normaly a usb mouse as an adapter, why aren't you using that? I have an usb mouse myself. As far as I know, using usb will slow your performance, using your processor...

---

### Post by equilibrium on 2005-05-09
I remember reading about this on the gentoo forums ages ago:

[http://forums.gentoo.org/viewtopic-p-1072020.html#1072020](http://forums.gentoo.org/viewtopic-p-1072020.html#1072020)

I am using the mouse applet atm to change res to 800dpi. If I get the time I might give the polling thing a go. Altho it would be nice if you could just build the module rather than the whole kernel.  :?

---

### Post by equilibrium on 2005-05-10
well I decided to give it a go tonight :)

I downloaded the sources etc, patched it and rebuilt the kernel.

I tried installing it but for some reason the module didn't change  :-? I took ages trying different things etc :( in the end after I installed my new kernel etc I just used the copy command to overwrite the old modules and low and behold it worked  \\:D/ 

```
cp  /usr/src/linux/drivers/usb/input/usbhid.ko /lib/modules/2.6.10-5-686-smp/kernel/drivers/usb/input/usbhid.ko
```
after reboot :)
```
cat /proc/bus/usb/devices
T:  Bus=01 Lev=02 Prnt=03 Port=02 Cnt=02 Dev#=  5 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c025 Rev=98.02
S:  Manufacturer=B16_b_02
S:  Product=USB-PS/2 Optical Mouse
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr= 98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   5 Ivl=2ms
```
```
cat /sys/module/usbhid/parameters/mousepoll
2
```

*goes off to kill some peeps on quake3*

I will hopefully look at maybe writing a how-to.

---

### Post by crane on 2005-05-11
[QUOTE=equilibrium]
*goes off to kill some peeps on quake3*

[/QUOTE]
 What server do you normally play on?
Screen name?

---

### Post by equilibrium on 2005-05-12
[QUOTE=crane]What server do you normally play on?
Screen name?[/QUOTE]
I normally play on euro OSP / 3W and RA3 servers :)

screen name = *equilibrium

here's my q3 favourites list from xqf:

```
Q3S 194.109.69.93:27960
Q3S 62.75.178.17:27961
Q3S 194.109.69.101:27960
Q3S 212.159.6.211:27980
Q3S 212.42.16.60:29263
Q3S 194.109.69.91:27960
Q3S 194.109.69.98:27960
Q3S 62.75.178.17:27962
```

---

