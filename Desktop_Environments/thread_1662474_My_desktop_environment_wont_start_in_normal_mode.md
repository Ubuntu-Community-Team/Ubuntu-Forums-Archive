---
title: "My desktop environment wont start in normal mode"
date: 2011-01-08
forum: Desktop Environments
---

### Post by suenda on 2011-01-08
I get a blank screen with no progress when I use normal mode, but I am able to get into desktop environment using recovery mode and selecting safe graphics mode from there. Anything I could to do to restore my normal desktop environment

---

### Post by suenda on 2011-01-08
I ran a boot info script from terminal. It generated the result as follows:

---

### Post by Krytarik on 2011-01-08
Everything seems to be ok with your boot config.

What exactly do you mean with "blank screen", blinking cursor, nothing at all, do you see the splash screen before?

It might be video driver related. What video card/chip is installed, what drivers do you use?

You might look in "/var/log/messages" if any errors are logged.

---

### Post by RaidersJH34 on 2011-02-03
i am having the same problem. i am trying to dual boot windows 7 and 10.10. i downloaded it from a cd, a flash drive, and an alternate download. And when its done loading and i run ubuntu from the grub loader, it goes black, then a cursor appears and alot of information comes then says welcome to ubuntu 10.10, and asks for a username and password. when i type both in, it comes up saying how i can use sudo and other stuff.

---

### Post by Krytarik on 2011-02-03
@RaidersJH34: The behaviour you are experiencing is completely different from those described by the OP, if I got it right. It seems you are logging into a "Terminal" session instead of "Gnome". After entering your username at the login screen, check at the bottom what "Session" is chosen, and change it.

---

### Post by RaidersJH34 on 2011-02-06
there wasnt anything at the bottom anout what session i was on or using. how can i change it? Everything is shown through a terminal. and only command prompts can be used.

---

### Post by Krytarik on 2011-02-06
It seems like you haven't installed ANY desktop environment. Please enter the following command, it will tell us if that is true:
```
dpkg -l|grep ubuntu-desktop
```In my case it says:
```
ii  ubuntu-desktop                        1.197                                           The Ubuntu desktop system

```If there is no result at all at your system, you are free to decide what DE you want to use/install:
[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

Then just install the desired meta-package with a command like this:
```
sudo apt-get install ubuntu-desktop
```
After the installation and reboot (at least of gdm) you should be given the respective session option at the login screen.

---

### Post by RaidersJH34 on 2011-02-07
when i type in the code to download the meta package, it said was already updated and nothing happened.

---

### Post by Krytarik on 2011-02-07
Back again. Do you really enter your username *before* looking for those option!?

> **Krytarik said:**
> @RaidersJH34: The behaviour you are experiencing is completely different from those described by the OP, if I got it right. It seems you are logging into a "Terminal" session instead of "Gnome". After entering your username at the login screen, check at the bottom what "Session" is chosen, and change it.

---

### Post by RaidersJH34 on 2011-02-09
yes i made sure i logged into my username. im 100% positive i did.

---

### Post by Krytarik on 2011-02-09
Then try those:
- at the login screen, press Alt+Ctrl+F1
- login at the console
```

sudo service gdm stop
sudo dpkg-reconfigure gdm
sudo service gdm start

```

---

### Post by RaidersJH34 on 2011-05-08
i did all the codes and my screen turned black and froze

---

### Post by RaidersJH34 on 2011-05-08
actually i went into safe mode and i can run it with low quality

---

### Post by Krytarik on 2011-05-08
Now that 3 months have passed, please say exactly what the current issue is, and what version of Ubuntu you are currently running. Thanks.

---

