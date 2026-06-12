---
title: "Wacom USB pen goes odd, If I take a break."
date: 2007-12-12
forum: Desktop Environments
---

### Post by eldaria on 2007-12-12
Hello, guys, 

I found out over a year ago that I have RSI, and I have since then been using a Wacom Pen tablet for my PC at home, and it has worked fine.
Now I finally got a Linux PC at work, (We were using Thin clients before) and I can now use a Pen Tablet here as well.
However I have a big issue with the pen.
If I don use the PC for only a few minutes, my Pen tablet stops working normally.

It becomes as if I did not modify the xorg.conf file to enable the Wacom tablet.
Basically Pen will only move if I push it down, no Drag possible, and middle/right mouse button no longer works.
Only way I can get it to work is by logging out and logging in again,
Reconnecting the tablet does no difference.

I tried to do some diagnostics, and it seems my USB resets.
dmesg shows following after Pen goes odd.
```
[ 6852.764450] hub 2-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[ 6852.764459] usb 2-2: USB disconnect, address 3
[ 6852.876354] usb 2-2: new low speed USB device using uhci_hcd and address 4
[ 6853.050591] usb 2-2: configuration #1 chosen from 1 choice
[ 6853.053596] input: Wacom Graphire4 4x5 as /class/input/input7

```
However, when PC Booted up The wacom was configured on Input4
```
[   22.351246] input: Wacom Graphire4 4x5 as /class/input/input4
[   22.357459] usbcore: registered new interface driver wacom
[   22.357463] build/buildd/linux-source-2.6.22-2.6.22/drivers/input/tablet/wacom_sys.c:v1.46:USB Wacom Graphire and Wacom Intuos tablet driver
```



Anybody have a solution for this, since it makes it almost impossible to work, well it makes it almost impossible to take a break. :-)

Regards.
Brian Levinsen

---

### Post by eldaria on 2007-12-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/linux/+bug/102659](https://bugs.launchpad.net/linux/+bug/102659) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ok, well after some more digging I found that I lucky enough to run into a combination of 2 bugs.

First I think my PC is affected by this bug:
[https://bugs.launchpad.net/linux/+bug/102659](https://bugs.launchpad.net/linux/+bug/102659)

Although Im not sure, but it would make sense.
This causes the USB to briefly disconnect and reconnect the Pen tablet.

And The Linux Wacom driver does not support to be Hot Plugged.
[http://linuxwacom.sourceforge.net/index.php/faq#HOTPLUG](http://linuxwacom.sourceforge.net/index.php/faq#HOTPLUG)

But the workaround described on the Linux Wacom project web page works, so I can now continue working.

---

