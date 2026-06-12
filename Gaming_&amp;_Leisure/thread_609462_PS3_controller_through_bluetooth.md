---
title: "PS3 controller through bluetooth"
date: 2007-11-11
forum: Gaming &amp; Leisure
---

### Post by mavsman4457 on 2007-11-11
Has anyone gotten the PS3 controller, the SIXAXIS, to work in ubuntu through bluetooth?  I know that it is plug and play through usb but ideally I would get it to work through bluetooth and be wireless.  I've seen tutorials but I haven't actually gotten them to fully work, not to mention they are a bit complicated.  Anyone have success?

---

### Post by Sockerdrickan on 2007-11-11
This guy sure has [http://youtube.com/watch?v=TPt6kRCE5TE](http://youtube.com/watch?v=TPt6kRCE5TE)

---

### Post by mavsman4457 on 2007-11-23
Here is a nice guide that I found.  I haven't tried it yet but I hope it works.

Code:
apt-get install build-essential patch fakeroot joystick jscalibrator
mkdir ~/bluez
cd ~/bluez
apt-get source bluez-utils
apt-get build-dep bluez-utils
wget [http://www.pabr.org/sixlinux/patch-hidd-3.19-pabr3](http://www.pabr.org/sixlinux/patch-hidd-3.19-pabr3)
patch ./bluez-utils-3.19/hidd/main.c patch-hidd-3.19-pabr3
cd bluez-utils-3.19
dpkg-buildpackage -rfakeroot -uc -b
apt-get remove bluez-utils
cd ..
dpkg -i bluez-utils_3.19-0ubuntu3_i386.deb
/etc/init.d/bluetooth stop
hidd --server --nocheck -n
*press the PS button on the controller, should see something like this:
*hidd[10190]: New HID device 00:19:C1:3F:9E:AA (Sony Computer Entertainment Wireless Controller)
Press ctrl+c to exit hidd
/etc/init.d/bluetooth start

If you want to enable multiple sixaxis controllers simply redo:

/etc/init.d/bluetooth stop

through the end to configure additional controllers! Have fun!

---

### Post by hikaricore on 2007-11-23
> **Tux0r said:**
> This guy sure has [http://youtube.com/watch?v=TPt6kRCE5TE](http://youtube.com/watch?v=TPt6kRCE5TE)

lol inaccurate response to question :p

---

### Post by Sockerdrickan on 2007-11-23
I know but it sure makes you giggle, huh?, huh?, huh? :D

---

### Post by hikaricore on 2007-11-23
Actually I was kinda wanting to hit the guy. (on youtube)
He flew the damn thing all of 8 seconds in a 2 minute video...

---

### Post by SebF on 2007-12-19
mavsman... dit u get it to work? i have the same issue

---

### Post by mondoUNC on 2008-01-13
I was looking for the same thing and came across this link in google
[http://www.pabr.org/sixlinux/sixlinux.en.html](http://www.pabr.org/sixlinux/sixlinux.en.html)
I haven't tried it yet, but he has videos proving it works.

---

### Post by UK-Wobbie on 2008-01-13
I say it's fake as the 1st Video with the PlayStation 3 controller..
If you put anything with meta, It will do the shame thing like the PlayStation 3 controller! 

It will movie like anything if you add some power to it!

Seen something like it on some TV program :)

The 2st Video as got me foxed a bit!
But it's mad when the guy flys it and go off screen :)

---

### Post by epyon22 on 2008-06-30
has any one got this working in hardy? it seems that hardy uses a new version of bluez-utils 3.26 and the website doesnt have a patch for that. does the other patch patch-hidd-3.9-pabr3 work for this one? any help would be appreciated

---

### Post by __Ryan__ on 2009-04-04
I have managed to get the PS3 controller working over bluetooth with Ubuntu 8.10 Intrepid.

[http://www.wiredrevolution.com/ubuntu/setup-ps3-controller-over-bluetooth-on-ubuntu]("http://www.wiredrevolution.com/ubuntu/setup-ps3-controller-over-bluetooth-on-ubuntu")

Let me know how it goes.

---

### Post by Orbital_sFear on 2012-07-08
These are the sites you guys are looking for:
[http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_PS3_BD_Remote](http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_PS3_BD_Remote)
[http://kitlaan.twinaxis.com/projects/bluez-ps3remote/](http://kitlaan.twinaxis.com/projects/bluez-ps3remote/)

I got my ps3 talking over bluetooth on xubuntu 12.04 using those sites.

-Orbital

---

