---
title: "Screensaver won't start with nonAdmin User"
date: 2008-04-01
forum: Desktop Environments
---

### Post by jnbek on 2008-04-01
Hi, I have xubuntu 7.10 installed on an old beast, and everything runs great and looks awesome, my only complaint is, when logged in as a user without sudo access, the Screen saver refuses to start. The monitor does blank out after about 20 minutes (which I also want to stop). I've read the other similar threads, none of which apply, it should be noted that clicking on Preview shows the Screensaver's preview. I am basically wanting to have the computer become an electronic picture frame, with a slideshow of all my pictures. Please advise how to make the screensaver start and keep the monitor from shutting off?
Thanks in advance.:)

---

### Post by jnbek on 2008-04-01
Well, In my research I did find out how to keep the monitor from shutting off by adding 

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

to the end of /etc/X11/xorg.conf and then for the stupid screensaver, I apt-get removed gnome-screensaver then apt-get installed xscreensaver, ran xscreensaver at a command prompt to set it up, then I added xscreensaver to Autostart Programs, restarted X, and it like so fixed my problem. 

:guitar:

---

