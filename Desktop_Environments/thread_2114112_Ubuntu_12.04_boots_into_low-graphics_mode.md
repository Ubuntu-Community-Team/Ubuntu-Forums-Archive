---
title: "Ubuntu 12.04 boots into low-graphics mode"
date: 2013-02-09
forum: Desktop Environments
---

### Post by dimako83 on 2013-02-09
I am getting the error “The system is running in low-graphics mode” error on my PC. I'm running Ubuntu 12.04.2 LTS (I think it might had been updated from 12.04.1 and this could be the source of my problem).
Its and HP PC with integrated graphics card. it was running fine until yesterday. Trying to switch to gdm just boots up with my usual background and a computer icon in the middle of the screen but I cannot do anything and doesn't have an option to log in.

I have tried the solution in the next thread: How to fix "The system is running in low-graphics mode" error?

I have tried to:
1. sudo apt-get install --reinstall ubuntu-desktop
2. Verified greeter-session=pantheon-greeter
3. Have tried switching to GDM
4. Have checked I have enough free disk space
5. Installing a new Intel driver from X-Swat repository
6. Reinstalling xserver-xorg

Any help would be great. Thank You

---

### Post by pavi_elex on 2013-02-09
Go on command prompt.
$ apt-get update
&
$ apt-get upgrade
Are you facing any error here.

Try to open recovery mode and install broken packages.
This should be run without any error.

---

### Post by dimako83 on 2013-02-10
> **pavi_elex said:**
> Go on command prompt.
$ apt-get update
&
$ apt-get upgrade
Are you facing any error here.

Try to open recovery mode and install broken packages.
This should be run without any error.

I have no errors trying to run apt get update and after that apt-get upgrade

I am attaching some log files I hope it could help because I am already out of ideas how to fix it :-(

Xorg.0.log: [http://pastebin.com/bnS6dcmT](http://pastebin.com/bnS6dcmT)

Xorg.failsafe: [http://pastebin.com/ELzvBdHi](http://pastebin.com/ELzvBdHi)

lightdm.log: [http://pastebin.com/iBhKmzZ6](http://pastebin.com/iBhKmzZ6)

---

