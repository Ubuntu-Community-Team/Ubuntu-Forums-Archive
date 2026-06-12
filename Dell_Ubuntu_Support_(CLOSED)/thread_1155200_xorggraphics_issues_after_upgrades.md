---
title: "xorg/graphics issues after upgrades"
date: 2009-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by the2ndgenesis on 2009-05-10
Hey everyone. Just had a brief question on Xorg after an upgrade to Jaunty on my XPS M1530 laptop... I'll do my best to be brief:

Until about a month ago I was using Hardy (after skepticism about the VPN client in Intrepid), but then had a brief moment of bravado and decided to upgrade all the way to Jaunty myself (a terrible idea in retrospect).

As anticipated the driver for my nVidia card stopped working after the upgrade to Intrepid (I figured I'd be able to fix it later), and then xserver stopped working for me period after the upgrade to Jaunty. I reset my xorg.conf using ```
dpkg-reconfigure xserver-xorg
``` to fix the problem, but now Jaunty just loads to a black screen and I can't get anywhere.

I'll save my questions on the nVidia driver for another time/thread, but for the time being I'd like to at least be able to get back to the desktop so I can start tweaking it through something other than windows or a liveCD. The contents of my xorg.conf are as follows:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

My laptop's specs are here:
[http://www.notebookreview.com/default.asp?newsID=4135](http://www.notebookreview.com/default.asp?newsID=4135)

Thanks so much for any advice you guys can offer. I'm sorry if my questions are particularly naive/noobish, I really don't know who else to ask about this issue.

---

### Post by coffeeaddict22 on 2009-05-11
There are two easy options to try first: boot up, and select the recovery option (just below the usual boot option).  The menu there will give you an option of "repair graphics" which might fix it completely; Another option is to go to a root console with networking, which may help too.

---

### Post by polychro on 2009-05-11
Hi, Had same problem, did what coffeeadict22 suggests and worked. good luck --V.

---

### Post by the2ndgenesis on 2009-05-11
Thanks for the suggestion coffeeaddict. I was hoping that would solve my problem, but that doesn't seem to be the case. Oh well.

Anyway, my new xorg.conf is as follows:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Anyone else have suggestions? I can post the outputs of other config files upon request.

---

### Post by unutbu on 2009-05-11
I found an xorg.conf for the XPS M1530 here:
[http://modzer0.cs.uaf.edu/~hardwarehank/files/M1530.xorg.conf](http://modzer0.cs.uaf.edu/~hardwarehank/files/M1530.xorg.conf)

The link above was found here:
[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530)
(Search for "fully tweaked and working xorg.conf"

---

