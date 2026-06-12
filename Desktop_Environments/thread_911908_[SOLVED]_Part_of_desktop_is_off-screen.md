---
title: "[SOLVED] Part of desktop is off-screen"
date: 2008-09-06
forum: Desktop Environments
---

### Post by Green_Mac on 2008-09-06
I had some screen resolution problems after adding a Belkin Switch2 to use a Windows laptop and Linux box with the same keyboard and mouse, which I have since solved (tried so many things, can't remember which one worked, warning, don't drink and compute).  My problem now is that the bottom and the left side of what should be showing on the screen are now just off the screen, in other words I need to resize what Ubuntu is trying to display so that it fits on my screen (Acer AL1912, OSD menu doesn't seem to have anything to fix it).

---

### Post by ad_267 on 2008-09-06
What video card do you have and what drivers are you using? Don't know if I can help but that will be useful for anyone else who might be able to.

---

### Post by Green_Mac on 2008-09-06
I built the thing myself, and there's no way I would have thrown out the paperwork that came with the motherboard, but I that doesn't mean I know where in this room it is.  I was about to post this question on another channel, I'm used to M$ Windows being able to tell me about every piece of hardware in my system, but I can't find a way for Ubuntu to tell me what my graphics card is.

---

### Post by Dave_Connor on 2008-09-06
Try "lspci" and look for VGA controller.

---

### Post by mgmiller on 2008-09-06
I did a quick lookup of your monitor and got the owners manual for it.  On the front panel of the monitor there are 4 buttons, a light and then the power button.  The first button all the way to the left is the "Auto" button.  Pressing that will usually fix odd resize problems on LCD panels.  You may need to hit it when switching back and forth with the KVM switch until the monitor remembers what it's supposed to look like with a given signal.

Hope this helped....:popcorn:

---

### Post by Green_Mac on 2008-09-07
Thanks to both of you.  I'll make a note of lspci, that's really useful to know.  It tells me I'm using ATI Technologies Inc Radeon HD 3200 Graphics.

Unfortunately, the auto button isn't a lot of help.  The bottom of the screen is now slightly more visible, but it's also moved even farther to the left.

---

### Post by mgmiller on 2008-09-07
You could try adding the correct horizontal synch and vertical refresh to your /etc/X11/xorg.conf file.  Here is what that section looks like in mine:

Section "Monitor"
    Identifier    "VX2235wm"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1680x1050"
    Horizsync    31.5-65.5
    Vertrefresh    56.0 - 65.0


For your monitor, the horizsync should be 24.0-80.0
and the vertrefresh should be 49.0 - 75.0

Also. the native resolution on the Modelname line should be 1280x1024 and obviously, the identifier line will have your monitors model number on it.

Remember to back up the xorg.conf file before making any changes, just in case something gets borked.

Open a terminal and type:
```
sudo cp /etc/X11/xorg.conf xorg.conf.backup
```Then type:
```
gksu gedit /etc/X11/xorg.conf
```and make the changes suggested above, and click save.

Log off and log back on to restart x.
(Sometimes after logging off, you have to hit ctrl-alt-backspace to restart x)

Make sure correct resolution and refresh rates (1280 x 1024 @ 60 Hz) are selected.

Fixed?

Good luck

---

### Post by mgmiller on 2008-09-07
There is one more thing you can try to set up the monitor and card correctly.

Use this command to pop up the gui:
```
gksu displayconfig-gtk
```
then skip to instruction 5 below.

If you want to permanently add it to your menu system and then run it, do the following:


1) Right click Applications and select "Edit Menus"
2) Scroll to and select, by left clicking, the "Other" location on the left side.
3) On the right side put a check mark in the box next to "Screens and Graphics", then click "Close".
4) Go to Applications > Other > Screens and Graphics
5) On the screen tab, click the drop down next to model.
6) If you can find your model, great, if not, select "generic" at the top of the list and on the right find LCD of the correct resolution assuming it's an LCD, otherwise scroll down a bit and use Monitor of the correct resolution for CRT, or try Plug 'N Play.
If it is a wide screen monitor, don't forget to check the wide screen box.
7) Now you can find & select your resolution and refresh rate from the list on the right side. Click OK.
8 ) Go to the Graphics Card tab.
9) Click on Driver and select what you need.
10) Click the test button to make sure all is ok.
11) Click ok and you're done.

---

### Post by Green_Mac on 2008-09-07
Brilliant!  That last one did the trick.  Plus I've learnt about three new things.  Thanks to everyone.

---

### Post by mgmiller on 2008-09-07
> I'm used to M$ Windows being able to tell me about every piece of hardware in my system, but I can't find a way for Ubuntu to tell me what my graphics card is.

I'll give you one more useful gui tool for looking at your hardware.
```

sudo apt-get install gnome-device-manager
```

After it's installed, look in Applications > System Tools > Device Manager

I really think it should be part of the default install.  At the present time, it lets you look at your hardware, but not change anything, so it's safe to use.

---

### Post by Green_Mac on 2008-09-08
This is fantastic!  My problem is fixed and I'm *still* getting good stuff.

---

### Post by mgmiller on 2008-09-08
> This is fantastic!  My problem is fixed and I'm *still* getting good stuff. 	

Welcome to Ubuntu.....:lolflag:

---

