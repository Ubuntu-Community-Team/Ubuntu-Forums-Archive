---
title: "No Events input detected in Krom Game Pad in Ubuntu 18.04"
date: 2020-04-10
forum: Gaming &amp; Leisure
---

### Post by paigorik on 2020-04-10
Dear ubuntu team,

When I plug the Krom Game Pad ([https://www.kromgaming.com/en/controllers/key](https://www.kromgaming.com/en/controllers/key)) in ubuntu 18.04, it seems it is detected by the system (using **xpad** driver from the kernel), but no input events are working. When I execute "dmesg" I obtain the following:

[ 1762.747913] usb 3-1.4.2: new full-speed USB device number 9 using xhci_hcd
[ 1762.862544] usb 3-1.4.2: New USB device found, idVendor=045e, idProduct=028e
[ 1762.862550] usb 3-1.4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1762.862553] usb 3-1.4.2: Product: Controller
[ 1762.862556] usb 3-1.4.2: Manufacturer: SHANWAN

I also have tried the userspace **xboxdrv** (off course by blacklisting the xpad one first, and following the correspondent commands for removing xpad "sudo rmmod xpad" and loading the xboxdrv  as "/usr/bin/xboxdrv --detach-kernel-driver --silent"). I even tried installing the  "**ubuntu-xboxdrv**[COLOR=#24292E][FONT=SFMono-Regular]", [/FONT][/COLOR]but none of the methods have worked. The controller in all cases gets recognized when using the application **jstest-jtk, **but never detects any event input.

The interesting thing is that I tried connecting the same controller in ubuntu 16.04 (older kernel), and just plugging and playing it is assigned a Shanwan driver according to **jstest-jtk **app and detects perfectly al input events.

Could somebody help me please what could I do to make it work in ubuntu 18.04 kernel?
It seems I have already used all my available options.

Thank you for your help in advance

---

### Post by Holger_Gehrke on 2020-04-10
The xpad driver is for xbox controllers. Unless that pad is for the original XBox or the XBox 360 that's the wrong driver. The right driver is probably a combination of joydev and hid/hid_generic/usbhid which is what my system uses automatically without any intervention from me for my noname-gamepad that also gives ShanWan as manufacturer.

Holger

---

### Post by paigorik on 2020-04-10
Thanks, I won't use the xpad driver then, but how can I load either joydev or [COLOR=#000000]hid/hid_generic/usbhid in ubuntu? Apparently this should be donde automaically but in my case it doesn't, (unless I plug it into ubuntu 16.04). I tried looking on other websites without any luck[/COLOR]

---

### Post by paigorik on 2020-04-10
[COLOR=#000000]Thanks, I won't use the xpad driver then, but how can I load either joydev or [/COLOR][COLOR=#000000][COLOR=#000000]hid/hid_generic/usbhid in ubuntu? Apparently this should be donde automatically but in my case it doesn't, (unless I plug it into ubuntu 16.04). I tried looking on other websites without any luck[/COLOR][/COLOR]

---

### Post by paigorik on 2020-04-12
> **Holger_Gehrke said:**
> The xpad driver is for xbox controllers. Unless that pad is for the original XBox or the XBox 360 that's the wrong driver. The right driver is probably a combination of joydev and hid/hid_generic/usbhid which is what my system uses automatically without any intervention from me for my noname-gamepad that also gives ShanWan as manufacturer.

Holger

Hi Holger, It seems that the correct module is joydev, since in Ubuntu 16.04 if I remove it, my controller stops working. I put it back and works again (recognized as SHANWAN android Gamepad), but in ubuntu 18.04 I have it active and doesn't show anything. Using xpad in ubuntu 18.04 recognizes it as a Microsoft Xbox Controller but no input is detected. Any work around this issue?

---

