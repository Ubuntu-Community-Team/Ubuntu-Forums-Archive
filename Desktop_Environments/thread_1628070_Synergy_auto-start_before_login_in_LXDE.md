---
title: "Synergy auto-start before login in LXDE"
date: 2010-11-22
forum: Desktop Environments
---

### Post by magneze on 2010-11-22
I'd like Synergy to auto-start before and after login. After login is fine, but I can't find instructions for getting it to start before login (ie: so I can use synergy to enter user id/password). The Synergy docs don't cover LXDE. :(

Anyone done this before?

---

### Post by magneze on 2010-11-24
Bump

---

### Post by Muhnamana on 2011-01-12
Wow, I can't believe I'm not the only one needing to know this as well. I thought the Ubuntu steps might work but they don't.

Can anyone shed some light on this?

---

### Post by Muhnamana on 2011-01-17
Here's the closest I've got so far...

Add this line:
Syneryc xxx.xxx.x.xx (ip address)

to the following file: /etc/xdg/lxsession/Lubuntu/autostart

Still trying to find a solution to start on boot.

---

### Post by Muhnamana on 2011-01-17
Solution Found!

From the terminal, type sudo gedit /etc/init.d/rc.local

At the end of the file, add synergyc <your ip address> save and close.

I reboot and synergy started on boot.

Let me know if it works for you.

---

### Post by magneze on 2011-01-18
Nice one. Thanks.

---

### Post by CapnChkn on 2012-02-26
I am running a minimal install of 11.10 on an Asus eeepc 701 2g surf, with a 4 gig SDHC holding the entire OS, and LXDE.  Since I keep this plugged into a monitor when I'm not away, I have the monitor settings at 800x480 for the LCD on the netbook, and 1024 x 768 on the monitor.

Though the above instructions did start synergyc at the login screen, I couldn't get the system to recognise the working area of the monitor's resolution.  Everything worked just like it says on the box, but still runs in the upper right of the screen.

I know this works in Gnome by modifying the file lightdm.conf.  I will try to find a solution to my problem as well, and am not as good with Linux as I'd like to be...

---

### Post by thunder04 on 2013-01-05
I just installed Lubuntu 12.10 and cannot for the life of me get synergyc to start at boot (before login).

The farthest I've got is by creating synergyc.conf in /etc/init/ with the following contents:

```

start on login-session-start
exec /usr/bin/synergyc 10.7.17.200

```

However, it doesn't work.  I can see that it's being called via the syslog, but the error returned is:

```

WARNING: cannot open secondary screen: unable to open screen#012#011/build/buildd/synergy-1.3.8/src/cmd/synergyc/synergyc.cpp,346

```

What am I doing wrong?  I'd LOVE to accomplish this!

---

### Post by thunder04 on 2013-01-05
Nevermind!  I was able to accomplish this by following the instructions found here:

[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

[quote=SynergyHowto]

Add the following line at the end of /etc/lightdm/lightdm.conf:

```

greeter-setup-script=/usr/bin/synergyc <SERVER HOSTNAME>

```

Where **<SERVER HOSTNAME>** is the name/IP of the server you are connecting to.
[/quote]

---

### Post by ChrisQ on 2013-01-27
As a side note (for when I actually need this data again on the next hard drive failure driven reinstall)

if you use arandr to setup a dual/multi monitor system and save the configuration then use synergy in the lightdm.conf file without configuring lightdm for dual screen with the same script, you get really wonky synergy driven mouse behaviour with locking on whichever single monitor had the lightdm login on it. 

To stop this from happening you need to configure lightdm for proper dual screen and configure your desktop from lightdm as well.

I added the following to my /etc/lightdm/lightdm.conf file to get it to work flawlessly:

#for the login screen
display-setup-script=/home/chris/.screenlayout/dual.sh
#for my desktop session
session-setup-script=/home/chris/.screenlayout/dual.sh
greeter-setup-script=/usr/bin/synergyc -n serverv3 192.168.1.132




Where dual.sh is my saved arandr dual screen config.

---

