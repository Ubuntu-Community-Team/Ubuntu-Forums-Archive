---
title: "Select xorg.conf on boot?  Perhaps though GDM?"
date: 2006-01-03
forum: Desktop Environments
---

### Post by annex on 2006-01-03
Hello,

My girlfriend has a laptop with Ubuntu.  I have Xinerama setup on it using the external monitor port.

Depending on the situation the laptop needs two different configurations:
1. When the laptop is at home it needs a xorg.conf setup for xinerama.
2. When the laptop is anywhere else it needs a xorg.conf for only one monitor without xinerama.

I've been trying to think of an elegant way to switch between the two configurations.  I was wondering if gdm could do it somehow?  Obviously it would need to restart but could I add a button or such in gdm to change the file?

If not, could a little selector script written in bash or such?

Any ideas, suggestions?

Thanks

---

### Post by joneZ on 2006-01-03
Hi,

Do have looked at switchconf ? It is in the repostries.

apt-get show switchconf

sounds like what you need, and maybe you can improve that since it's a script.

Bye
Erik

---

### Post by Suger on 2006-01-04
Are you sure you need to disable Xinerama ? If there is only one monitor, doesn't it disable itself by default ?

---

### Post by annex on 2006-01-06
[QUOTE=Suger]Are you sure you need to disable Xinerama ? If there is only one monitor, doesn't it disable itself by default ?[/QUOTE]

It doesn't seem to know if there's a second monitor connected or not.  It will not use Xinerama if the second adapter is not installed but I haven't found a way to test if the 2nd monitor is connected or not.

Hrmmm that might be a good place to look.

joneZ: Thanks, I'll take a look at switchconf

---

### Post by iv0 on 2006-01-08
Hello,

I have the same problem, my XORG ATI driver doesn't detect the presence of a CRT monitor on my ATI9700. Thanks for suggesting switchconf, this is exactly what I need. Is there a simple way of choosing the configuration at the boot time?

Thanks a lot.

---

### Post by iv0 on 2006-01-09
Hi again,

I found an answer for this myself - I am using whereami + switchconf, and being very happy with it. This does the same job (after few hours of configuring :-)  as more famous SuSE SCPM tool for switching configurations.

Anyone interested in my configs? I use it to switch monitor layouts (xorg doesn't detect correctly presence of secondary VGA monitor), firestarter configuration and turn off numlock.

---

### Post by iv0 on 2007-03-23
Hello,

here is my configuration so you can use it as well. Please notice, that it doesn't work now (after few updates from ubuntu) as perfectly as it used to work before. Often it switches the config after second boot :-(

#The detection configuration file for 'whereami' /etc/whereami/detect.conf

# It is a good idea to default to somewhere...
default undocked

# If Docking station is detected, we are docked at home...
testusb 04a9:2220 docked

04a9:2220 is my docking station (adds 2 new usb ports).

# /etc/whereami/whereami.conf

#Docked
=docked switchconf docked

#Undocked
=undocked switchconf undocked

Then I have setup switchconf to change my xorg.conf file, turn on Numlock etc...

---

