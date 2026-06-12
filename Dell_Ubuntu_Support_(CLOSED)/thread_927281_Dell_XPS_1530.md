---
title: "Dell XPS 1530"
date: 2008-09-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by melenor on 2008-09-22
I just got a Dell XPS 1530 and i installed ubuntu 8.04.1 32-bit on it, the biggest problem is that the touch pad doesn't seem to work at all, it just goes crazy if i try to use it so i have been using my wireless mouse right now. 
So does anyone know how to get my touch pad working thank you, also my Dell had the Newest BIOS version.

---

### Post by melenor on 2008-09-22
i just realized that my wireless does not work either

---

### Post by jbloodwo on 2008-09-22
have you tried the howto in 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=912380](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=912380)

---

### Post by damis648 on 2008-09-22
Read the [Wiki]("https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#Touchpad%20is%20totally%20not%20working%20after%20lid%20is%20shut").
The answer is right there where the page is set to load. Just add the i8042.nomux=1 parameter to the GRUB kernel line for the trackpad. For wireless, you will need to use ndiswrapper... there are plenty of guides on this forum and that Wiki.

---

### Post by melenor on 2008-09-22
Thanks that took care of the touchpad, but not my wireless card, 	Dell Wireless 1505 Wireless-N Mini-card

---

### Post by damis648 on 2008-09-22
Good Luck! [http://ubuntuforums.org/showthread.php?t=912819](http://ubuntuforums.org/showthread.php?t=912819)

---

### Post by melenor on 2008-09-22
Any way to get it working without having to use the ndiswrapper?

---

### Post by damis648 on 2008-09-22
Sorry, no native drivers. But ndiswrapper works very well nevertheless.

---

### Post by melenor on 2008-09-22
will the next ubuntu have native drivers.
Are there any beta drivers or other drivers.

---

### Post by damis648 on 2008-09-22
I don't believe so for either of those. Sorry.

---

### Post by jespdj on 2008-09-23
> **melenor said:**
> will the next ubuntu have native drivers.
Are there any beta drivers or other drivers.
The Dell wireless card uses a WiFi chip from Broadcomm (as far as I know). Unfortunately, that's one of those hardware manufacturers who are not willing to support Linux or open source software.

Without detailed information about the hardware and without collaboration from the manufacturer, it's very difficult to write a driver for a piece of hardware.

So don't count on a native Linux driver soon.... :(

[SIZE="1"](Next time, buy an Intel WiFi card - they do make open source drivers).[/SIZE]

---

### Post by melenor on 2008-09-23
I thought that dell supported ubuntu, why then would they use a wireless card that isn't compatible? 

Is there a page to get a work around with the boardcom drivers.

---

### Post by damis648 on 2008-09-23
> **melenor said:**
> I thought that dell supported ubuntu, why then would they use a wireless card that isn't compatible? 

Is there a page to get a work around with the boardcom drivers.

It is. I think they use ndiswrapper also, and no. The easiest way to get this working is with NDISwrapper.

---

### Post by melenor on 2008-09-23
Also something that i just ran into was when I tried to enable the restricted Nvidia drivers, it messed up my screen when i booted up, i had to boot to Recovery Mode and fix X that reset it, and i logged on that way.

Would downloading the offical linux driver from nvidia's site work?

---

