---
title: "Problem with Treo 680 synchronization on kubuntu"
date: 2010-01-12
forum: Desktop Environments
---

### Post by a_flj_ on 2010-01-12
Hi.

It goes like this: as soon as I plug the device into the USB port, it starts rebooting in and endless loop. dmesg tells me repeatedly:

[FONT="Fixedsys"][ 3660.035755] usb 3-3: Handspring Visor / Palm OS converter now attached to ttyUSB0
[ 3660.035832] usb 3-3: Handspring Visor / Palm OS converter now attached to ttyUSB1
[ 3713.193687] visor 3-3:1.0: device disconnected[/FONT]

If I rebooot and leave the handheld plugged in, it seems the usbserial and visor kernel modules don't get loaded for some reason, and the device doesn't get reset. But kpilot also isn't able to open /dev/pilot (or /dev/ttyS0 or whatever name the usb port gets assigned), so it's not really helpful.

The moment I manually modprobe usbserial/visor, the endless rebooting of the Treo starts again.

The HW is an Asus laptop - K70AB. I guess it's not a HW problem, since there is no problem on the same HW plugging the Treo in when running Windows 7.

Any ideas? Is there any other useful info I should provide?

br,

flj

PS: It's my first post to the ubuntu forums, so I'm not sure if I post this into the right forum. Should post it elsewhere?

---

### Post by derekh4 on 2010-02-15
I am having the same problem.  I'm running Ubuntu 9.10 on a Thinkpad and when I plug in my Palm Treo 680 with the visor module loaded the palm just continually performs soft resets over and over and over.

Anyone with any ideas?

I just switched from Fedora Core 10 and my Palm worked perfectly on the same computer with FC10.

---

### Post by derekh4 on 2010-02-15
It appears that the visor module causes problems with the Treo 680 and this bug has been reported but is not assigned.

Visor Module resets treo 680
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496665](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496665)

---

