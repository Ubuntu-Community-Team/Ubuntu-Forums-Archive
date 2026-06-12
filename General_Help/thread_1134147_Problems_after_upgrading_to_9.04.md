---
title: "Problems after upgrading to 9.04"
date: 2009-04-23
forum: General Help
---

### Post by prssn on 2009-04-23
Okey, I need serious help seriously fast!
I just upgraded to 9.04 and instantly a number of problems popped into existence.

1. AWN doesn't work, when i try to open it it says "Screen isn't composited. Please run compiz (-fusion) or another compositing manager."

2. I can't scroll between workspaces

3. No desktop effects work, when I try to set to "normal" or "extra" effects it just says "Desktop effects could not be enabled"

4. Cube doesn't work anymore

So I had none of these problems while I was running 8.04, or 8.10. And I really need to fix this fast! Help please!!

---

### Post by whollycow on 2009-04-23
Sounds like Compiz is not enabled.  Try going into System->Preferences->Appearance->Visual Effects and see whether "None" is checked.

---

### Post by scottuss on 2009-04-23
Yes Compiz is not enabled. Also check that you have 3D graphics drivers installed.

Go to System > Administration > Hardware Drivers and check that they are enabled.

---

### Post by prssn on 2009-04-23
Yes, "None" is applied, but when I try to change it to "Normal" or "Extra" it just says that "Desktop effects could not be enabled".

Also, when i go to hardware drivers it tells me that "no proprietary drivers are in use on this system"

---

### Post by scottuss on 2009-04-23
> **prssn said:**
> Yes, "None" is applied, but when I try to change it to "Normal" or "Extra" it just says that "Desktop effects could not be enabled".

Also, when i go to hardware drivers it tells me that "no proprietary drivers are in use on this system"

Right, there are no 3d drivers installed then, that is why Compiz can't start.

What graphics chipset do you have? Nvidia, Intel, ATI?

---

### Post by prssn on 2009-04-23
I run Ubuntu on an HP Compaq 6910p Notebook, with Mobile Intel GMA X3100

So how do I install the driver for that?

---

### Post by prssn on 2009-04-23
Bump

---

### Post by Jameshardy88 on 2009-04-23
you should be able to install the correct drivers from system>administration>hardware drivers if i remember correctly

---

### Post by prssn on 2009-04-23
This is how it looks when I open Hardware Drivers
[IMG]http://upload.snelhest.org/images/090423Screenshot.png[/IMG]
Nothing shows

---

### Post by Mze on 2009-04-23
try a "Fix Xserver" from Recovery Mode if you haven't already.

---

### Post by prem1er on 2009-04-23
Wow. Use a thumbnail.

---

### Post by prssn on 2009-04-23
Exactly how do I do that? I'm new to Ubuntu, so if you could describe that woul be great.

---

### Post by Mze on 2009-04-23
> **prssn said:**
> Exactly how do I do that? I'm new to Ubuntu, so if you could describe that woul be great.

reboot machine, then select the 2nd option in your boot menu. and follow previous instructions.

Looks like your [graphics card]("http://ubuntuforums.org/showthread.php?t=1076014") had some issues during beta, but has been apparently fixed.

---

### Post by JK3mp on 2009-04-23
> **prssn said:**
> Exactly how do I do that? I'm new to Ubuntu, so if you could describe that woul be great.

Everything is just the source of one missing bit. 3d accel gfx driver. What is the model etc. of your gfx card?

---

### Post by prssn on 2009-04-23
Mobile Intel GMA X3100

---

### Post by prssn on 2009-04-23
Bump

I need serious help

---

### Post by Mze on 2009-04-23
Check this [thread]("http://ubuntuforums.org/showthread.php?t=1133874") too for more info

---

### Post by prssn on 2009-04-23
Yes, I did that, nothing happened

---

### Post by Mze on 2009-04-23
if you've tried everything and nothing has worked, then there's a possible regression with your graphics card, you might just have to do without Compiz till some updates come your way.

All the best.

---

### Post by prssn on 2009-04-23
So no one has any idea how I can install the drivers for my graphics card? Seriously, otherwise, is there a way to go back to 8.10?

---

### Post by scottuss on 2009-04-23
> **prssn said:**
> So no one has any idea how I can install the drivers for my graphics card? Seriously, otherwise, is there a way to go back to 8.10?

There are downgrade methods, but I've seen machines get screwed over for less. No point, if you really have to go back best way is to backup important data and do a clean install.

---

### Post by max_power on 2009-04-23
your gonna have to wait for things to shake out. 

It looks like this release has a lot more problems then those in the past. I have been running 9.04 since alpha without a hitch but the RC has given me a ton of problems.

---

### Post by hellios81 on 2009-04-23
several things did it for me
first enable UXA in xorg.conf

gksudo gedit /etc/X11/xorg.conf

 add these lines

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
        VideoRam        65536
	Option		"Tiling"			"false"
EndSection

second use this 

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821/comments/7](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821/comments/7)

---

### Post by Mze on 2009-04-24
Ubuntugeek has a thread up for [Intel Graphics cards]("http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html"), see if it is of any help

---

