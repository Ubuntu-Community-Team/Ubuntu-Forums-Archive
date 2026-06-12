---
title: "Maximum resolution: 1024 x 768"
date: 2009-02-04
forum: General Help
---

### Post by StephanG on 2009-02-04
Hey Guys :)

I've just recently installed Kubuntu 8.10 on my brother's computer for him using Wubi.  The drivers installed correctly.  But the highest resolution he can get at this time is 1024x768.  I checked the /etc/X11/xorg.conf file.  But all it had was this:

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

Isn't that a little bit empty?  Can I force a higher resolution?

---

### Post by glotz on 2009-02-04
Yes you can. It used to be automatical in the older versions but nowadays it's something of a black art if your monitor isn't brand spanking new and broadcast EDID. Try this [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

The important thing about it is to not give up too easily. You will get there after a dozen reboots and some swearing.

---

### Post by mixmaster on 2009-02-04
Thats a good link and I wish you well, but I have to admit that I eventually gave up on my work desktop with integrated intel graphics because no matter what I did I couldn't get a good resolution (it worked perfectly on Edgy and installed badly on Hardy but worked with the Edgy config).

My solution eventually was a £13 clearance sale ATI card from dabs.

---

### Post by StephanG on 2009-02-05
Thanks Guys, I'll try that now.  Uhm...*scratched head sheepishly* after I fix the damage that *new* driver my brother installed caused.

---

