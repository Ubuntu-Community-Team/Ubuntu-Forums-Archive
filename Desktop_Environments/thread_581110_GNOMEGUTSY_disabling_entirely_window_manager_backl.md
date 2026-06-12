---
title: "GNOME/GUTSY: disabling entirely window manager backlight management"
date: 2007-10-19
forum: Desktop Environments
---

### Post by weltall2 on 2007-10-19
I've just updated yesterday to gutsy with ubuntu alternate install (from dvd) with gnome 2.20 of course.
At a first (just like with livecds of betas tribes and release candidates) i didn't notice this problem, but after some hourse of usage it was starting to make me fell sick.
first of all when i manually choose the backlight setting with [FN]+ <= / => it seems the hw and gnome starts quarreling pratically when i press <= for example the hw puts a level, gnome puts another a bit higher and so on. this makes the backlight change something like a psychedelic video.
but that's not all from the power management there are only two functions: level to set the backlight and power off backlight (i'm  translating from the italian interface so they may be a bit different). pratically the first (which can't be disabled at all because if i put 0% i have the backlight powered off, if i put 100% i can't lower the screen backlight level, if i put something like 70% i have to continually put the backlight back to 100 and it's really annoying) the other command doesn't seem to do anything usefull.
**so i'd like to restore the behaviour i had on feisty and so NO backlight management by gnome** so i'd be able to manage it only trough hw and gnome will only power off the screen entirely after something like 20 minutes for example and dim the screen in software after 15 minutes (both cases can be restored just by moving the mouse, just like on a computer with no backlight managed like a desktop with a crt monitor)
thanks in advance and please answer as this is extremely annoying and it's also making me have an headcache.

the computer is an acer aspire 5920G and i use official nvidia driver if it does really matter...

---

### Post by cwhill on 2007-10-20
I need the same fix. Complete loss of manual control over LCD brightness. I can here my battery crying...

---

### Post by jim_p on 2007-10-20
Just a thought because I haven't installed Gutsy yet (and it seems I wont) and I dont use a laptop

Go to System > Preferences > Keyboard Shortcuts and disable the corresponding function from Gnome's reach!
I  have disabled all my keyboard's special keys (like  email, web, etc) and just kept the volume ones this way

---

### Post by cwhill on 2007-10-20
Thanks for the thought Jim. I thought maybe you had something there but...=( There were no keys for that control being used in Keyboard Shortcuts. I have a Purple Fn key that I hold down while pressing the UP and DOWN arrow keys that increases and decreases the LCD brightness respectively. When I hit those keys a cool little brightness ico even pops on the screen and a status bar indicating brightness levels. I can move the status bar and all by using the keys but it has no effect on the brightness. It is always simply maxed. Very bright. Hopefully we'll see some fixes soon. It kills the battery pretty quickly.
Thanks again.

---

### Post by jim_p on 2007-10-22
After some internet search, I found that there is a service in Gnome/Gutsy called "Hotkey Manager".
Please do a try and disable that as well and tell me if it works.
It is located in System > Administration > Services

---

### Post by cwhill on 2007-10-22
Jim I stopped and disabled that service. Even rebooted just incase but still same issue. The onscreen control comes up showing me the brightness symbol. Even shows it decreasing whenever I hit the key sequence but no change in actual brightness. I've read almost everything I can find but nothing seems to make a difference.

---

### Post by weltall2 on 2007-10-23
i was able to disable it partially. In other words i was able to disable the automatic management of the backlight (auto change of backlight level after some minutes and so on)
by disabling /apps/gnome-power-manager/backlight/enable in gconf. but still nothing for the manual change buttons which are still managed by either the hw and gnome making some psychedelic effects.
as for the key combinations i've scan all trough gconf and i coulnd't find anything about the fn key managent by gnome. let alone the shortcut manager which has nothing about backlight

---

### Post by joseff on 2007-11-02
could it be:
```
sudo chmod -x /etc/acpi/video_brightnessdown.sh
sudo chmod -x /etc/acpi/video_brightnessup.sh
```

It works for me on Compaq Presario V3502.

---

### Post by weltall2 on 2007-11-02
> **joseff said:**
> could it be:
```
sudo chmod -x /etc/acpi/video_brightnessdown.sh
sudo chmod -x /etc/acpi/video_brightnessup.sh
```

It works for me on Compaq Presario V3502.

thanks but it didn't work for me i still get the psychedelic effect, but at least i'm lucky that after all i can change the brightness

---

