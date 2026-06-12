---
title: "Wireless Adaptor installation Problem"
date: 2006-02-19
forum: Desktop Environments
---

### Post by joysa on 2006-02-19
Hello Dear Resquer!

i'm a newbi for linux,specially for new Linux Distro "uBantu" i know its somekinds of deritives of Debian Linux..wahtever..

i'm goin straight to the point,I'm havin problem installing my wireless adaptor get work,My specification:

Card: Linksys #[WUSB54Gv4], 802.11b/g, USB 2.0 -- [link here|List#WUSB54Gv4] 
Chipset: RT2500USB (RT2571F) (They just changed the chip and didn't tell anybody. Be careful which version (v1/v2/v4) you buy!) 
usbid: 13b1:000d 
Driver 00: Ralink Driver, Open Source: [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) - 2005-07-25 / Good alternative to ralinktech.com's driver. Works WELL. 

Everythin goes as directed by "ndiswrapperHOwTO" provided by ubantu Forum but seem problem presist,My hard is present,rt2500usb.inf on my **ndisgtk** list but still cant find WANL() on my network configar list...so no way to net acces,

*ndiswrapper -l *command shows everthin is ok,hardware present but can't access net.smbody plz help me..:( its really fraushtatin.:cry: 
[I][B]
i lyk ubantu views but no use with out net and mp3/mpeg plugin....absolutely no use.[/B][/I]:-k

---

### Post by qferret on 2006-02-19
Been there, done that...try a different version of the driver with ndiswrapper.
If it's seeing the hardware, but not creating the wlan0 interface, a different driver version should do it for ya.

---

