---
title: "Laptop screen turns off after login"
date: 2014-04-27
forum: Desktop Environments
---

### Post by matizek on 2014-04-27
Hi! 

Firstly - well done Canonical, especially the section responsible for xubuntu. It has become a great desktop system which I use on a daily basis. 

Now to my problem. I have a Lenovo x220 laptop with xubuntu 14.04 installed. I am completely satisfied with it, the only problem that intermittently occurs is the turned off screen after I login after a computer sleep. This means, sometimes, when I open the lid of the computer and it wakes up from sleep, the screen is dimmed to the lowest setting. I still can see a normal xfce splash, but it's dimmed to the lowest setting. This dimmed screen after wake-up is a sign, that after I enter my password the screen will go completely blank and dark - it turn's itself off. The computer seems to be working, but the screen if off.
This doesn't happen always, however. Sometimes the laptop wakes up with a bright screen and allows me to login and continue with my work. When not, however, I have to hold the power button to shut down the computer. 
Other that dimmed screen, there is nothing different from a normal wake-up. I can move my mouse, change users, type in password. Just after login it goes off. I have noticed also that it's more probable that computer wakes into this weird state if it sleeps for a longer time, for example over night. A thing that could have impact on this is the brightness plugin, which I will disable to test if it causes the problem. But if not this, what could cause this weird behaviour?

Thanks for your time.

Matic

---

### Post by Toz on 2014-04-27
Hello and welcome to the forums.

This is a [known current bug]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1303736") with light-locker. If you read through the bug report, you'll see a possible workaround - assign:
```
xrandr --auto
```
...to a keyboard shortcut and after you login and the screen goes blank, press the key combination to get the screen back.

The other option is to uninstall or disable light-locker and install/enable xscreensaver.

---

### Post by matizek on 2014-04-27
Thank you Toz for a truly helpful reply! I've uninstalled light-locker and am quite satisfied with xscreensaver now. Next time I will look up for known bugs before i post. Have a nice day!

---

