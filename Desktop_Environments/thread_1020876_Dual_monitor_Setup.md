---
title: "Dual monitor Setup"
date: 2008-12-24
forum: Desktop Environments
---

### Post by alingham on 2008-12-24
Hi
I've recently got my hands on a LCD monitor which I have to the left of my Laptop screen. 
When I try to configure the dual display under KDE 4.1 (System Settings -> Display) the two green boxes representing the displays are on top of each other. Clicking on them brings up dotted lines, but I can't move them or reposition them in anyway. They are fixed on top of each other.

Anything I'm doing wrong or need to know?
I've attached a picture so you can see my dilemma.
[IMG]http://alingham.com/images/dual-screen.png[/IMG]

---

### Post by SuperSonic4 on 2008-12-24
What graphics card do you have? I find KRandRDisplay to be crap compared to nvidia-settings

---

### Post by alingham on 2008-12-24
Not sure. When I do the ldscp or whatever it is it says the Graphics card is PCI... which probably means its inbuilt. I have a Toshiba A200 Satellite.
Will nvida-settings work for it regardless?

---

### Post by alingham on 2009-01-01
Anyone got any ideas? Is this a generic problem with KDE 4.1? Is there a workaround!?

---

### Post by theDaveTheRave on 2009-01-06
I don't think this is KDE specific, I have the exact same thing on my Gnome desktop.

The external screen is larger that then in built one, and they both show the same thing (only because the inbuilt screen is smaller I only get a "portion" of what it available).

I know that I saw a setup howto to have 2 monitors of different sizes on the forums somewhere, but I stupidly didn't tag it and now I can't find it.

I want to have separate screens with different windows opened on each - or even one window spread across the 2 monitors.

I'll report back if I find anything.

David

---

### Post by alingham on 2009-01-06
Yup - hearing you loud and clear on that one!
I found the same setup how to which works with the xorg.conf file...
Had it working nice and good...
Except one morning when I wanted to use my laptop as an actual laptop (heaven forbid!) and it couldn't cope with it... even though the laptop was set as the main monitor...
Haven't had any more replies and I'm still hunting for a solution...

---

### Post by theDaveTheRave on 2009-01-07
Is there a possiblity of having 2 xorg.conf files and then just switching between them with a script??

Obviously a reboot would be required.... or maybe a script could detect the screen types at boot and then select the desired xorg.conf setup??

I'm not too sure about the xorg.conf and I'm not that happy about playing around with it... but I guess to really consider myself a linux "geek" I should start thinking about what I need can do with it.

would you like a copy of my xorg.conf??

it may help you return to a basic setup so as your laptop will function as a laptop again??

David

---

### Post by alingham on 2009-01-07
Nah its ok. I have a back up of the original.
At the moment I have both screens just displaying the same thing until something is done about it.
The reason for that is because I never know when I'll want to pull the LCD out to use the computer on the move as a laptop again, and when that happens there's little doubt I'll be wanting to mess around switching xorg.conf's etc...

---

### Post by vertago1 on 2009-10-22
Is there any chance the GUI setup will get fixed? Sometimes I am using a laptop and borrow a random monitor and don't want the hassle of looking up how to edit my xorg.conf each time.

For some reason the "Multiple Monitors" screen always says "This module is only for configuring systems with a single desktop spread across multiple monitors. You do not appear to have this configuration." Also, on "Size & Orientation" I cannot drag the screens so that they are not stacked on top of one another so it appears the GUI isn't capable of changing whether or not the xserver has more than one screen.

Am I looking in the wrong part of the settings?

---

### Post by rickgo on 2009-10-23
I think this is broken.My comp locked up before the login screen came up.All I got was a 2 inch long blue line.Luckily a hard shutdown and disconnect of the 2nd monitor and
everthing was ok again. Jus have to wait for more infor/fix

---

### Post by paulmerchant on 2009-11-03
Each time I plug an extra monitor in with my laptop, I manually run grandr to configure the display settings. It's a slight annoyance to not have KDE remember my dual display settings, but doing this is not a bad work around until the multiple monitor support is fixed in KDE.

---

### Post by hrizzy on 2010-01-15
xrandr works fine for me for dual head set up (integrated Intel card in Dell laptop + Dell LCD). 

This is the script (every time when I connect LCD I have to run it, but this is not the biggest issue for me)

```
#!/bin/bash
xrandr --output VGA1 --mode 1280x1024
xrandr --output LVDS1 --mode 1440x900
xrandr --output VGA1 --above LVDS1
```This is tested on Ubuntu 9.04 with Gnome and Debian sid with KDE.
In 9.04 you should add in your xorg.conf (in Screen section) the following:

```
SubSection "Display"
Virtual X Y
EndSubSection
```Where X Y is max resolution you need for your desktop to stretch on both screens.

---

