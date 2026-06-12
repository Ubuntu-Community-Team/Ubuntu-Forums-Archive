---
title: "Screen Resolution"
date: 2007-08-23
forum: Dell  Ubuntu Support
---

### Post by jp316ad on 2007-08-23
Hey guys I have a problem that I've been trying to solve but nothing works. 

I am running from the Live Cd and want to install but when I get to the setup where it asks you for the region you are located at, I can't even scroll down to click next or whatever it says. I tried moving the window on top and tried moving it up alittle but its just too big.

I need to change the screen resolution and I typed in this code:

sudo dpkg-reconfigure -phigh xserver-xorg

but I get this:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070823053639

What do I do now?

---

### Post by ridgeland on 2007-08-23
When you put the CD in and boot there is a menu with a countdown timer.  There you can select the screen resolution before getting to the desktop.

---

### Post by jp316ad on 2007-08-23
I did that. It's supposed to be F4 right? I selected the resolution that I wanted but when it starts its at 800 x 600.

---

### Post by ridgeland on 2007-08-23
I just tried booting the LiveCD and changing the resolution using F4.
I changed it to 640x480 or such.  It booted to 1024x768, ignoring the setting as you said.
When you boot and try:
menu -> System -> Preferences -> Screen Resolution
what options are presented?
I've also had the case where shrinking the two panels gave me the extra space I needed to view the entire window.  To shrink the panels right click on them go to properties and turn on [X] Show hide buttons, on the edge of the panel will be a toggle - expand/shrink.  This will give you more viewing area.

---

### Post by steve.horsley on 2007-08-23
The command **xrandr** will list a set of allowable video modes. Then you can select the mode number (from the first column) with:
**xrandr -s 1**
or whatever number you want. You can also do:
**xrandr -s 1280x1024**
if it's allowed.

---

### Post by jp316ad on 2007-08-23
When I went to:

menu -> System -> Preferences -> Screen Resolution

The only options that were presented to me were the 640 x 480 and 800 x 600 but I know that my computer handles more than that because I also have Windows XPro Svc pk 2 on it and its set to 1024.

---

### Post by Salpiche on 2007-08-23
Try : *sudo dpkg-reconfigure xserver-xorg*, and just follow through with it, I had to use it without the "*-phigh*"  in order to get it to work.

---

### Post by ridgeland on 2007-08-23
800x600 will work if you shrink both panels out of sight before you start the installation.
After installation you can setup your resolution the way you want to keep it.

---

