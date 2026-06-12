---
title: "Desktop screen - left side not visible, menus beyond reach"
date: 2016-05-14
forum: Desktop Environments
---

### Post by beesblaas on 2016-05-14
I had some upgrade troubles and my Ubuntu boots fine but but the desktop does not show the menus on the left.
So I cannot start any program because I cannot see or click a program. I can see some icons & files I had previously on the desktop.
Everything to the left of the screen is not visible. It is as if there is an amplification factor that pushes the left menu too far to the left and out of range of the monitor, e.g. I see "UNTU 14.04 LTS" because the "UB" and anything left is chopped off.


[LIST]
[*]It is not the monitor - I have tried using different monitor settings - moving the screen to the right etc, trying "wide" mode, also used a different monitor (Samsung and Phillips). Also - this is a dual-boot with windoze, and windoze does not have an issue with the monitor. 
[*]I can right-click on the Ubuntu desktop and get access to the screen setup - I have tried all the different settings e.g. 1920x1080, 1680x1050, 1600x900 etc, etc, none of them help. 
[*]It is not an issue with grub - because I managed to change the video setting from 800x600 to 1920x1080 in grub and afterwards the grub menu resolution changed as instructed - but it is not the grub menu that is an issue, it is the desktop. 
[*]I managed to do a xrandr -q and it told me that it was set at 1920x1080 which is correct for the monitor. 
[*]I have done: "sudo apt-get remove --purge unity" and then "sudo apt-get install --reinstall ubuntu-desktop", but it does not help. 
[*]I have rebooted a previous version of the kernel and it has the same problem 
[/LIST]

This issue happened a year ago and I think I fiddled somewhere in a configuration file with video settings and it was OK. But I have a memory like a goldfish - I don't know what I did.
**Please help**. My Ubuntu is rusted so I have simply been trying this & that from what I read on the web. I'm fiddling in the dark.

---

### Post by beesblaas on 2016-05-14
ADDITIONAL INFORMATION:
I have found that if I log in as a different user, then the desktop screen is perfect.
However id I log in as myself, I still cannot see any menu/application buttons.
I copied all the screen settings from the user who has the good screen - resolution, background, screen behaviour etc, still no luck.

So this is definitely a software/configuration issue, and it is something which affect one user and not the other.
What can this be ???????
Is there a configuration file from the good screen that I can compare with the bad desktop screen ?

---

### Post by CantankRus on 2016-05-14
A couple of things you can try.
Reset compiz to default....
```
dconf reset -f /org/compiz/
```
Log out.

You could also try setting your entire dconf settings to default.
You will lose a lot of personal app settings etc you may have changed and will have to redo.
```
dconf reset -f /
```
Log out.

---

### Post by beesblaas on 2016-05-15
Thank you very much CantankRus
your suggestion solved it!
dconf reset -f /
I did have a look at dconf settings before I did your reset. There was a line: "x-offset=48" and I'm sure this was the cause of the problem, shifting the screen. The dconf settings when I logged in as the other user did not have this line.
How on earth it got there I do not know. Maybe it was me in a past life :D

---

### Post by CantankRus on 2016-05-15
I doubt if "x-offset=48" was the culprit. This is just a setting for the offset from left edge when using the expo plugin (workspace switcher)
but glad it's solved. :D

---

