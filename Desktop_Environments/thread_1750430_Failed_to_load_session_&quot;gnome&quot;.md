---
title: "Failed to load session &quot;gnome&quot;"
date: 2011-05-05
forum: Desktop Environments
---

### Post by thomasmilo on 2011-05-05
I recently upgraded from 10.10 to 11.04.  I am able to log into and use LXDE desktop, but at the GUI login when I try to log into gnome-shell or Open Box, the log in fails.  With Open Box I just get a black screen.  When trying gnome, I get error "Failed to load session "gnome."  When trying KDE Plasma I get music and then black screen on which I can control the mouse cursor. 

Attached is my hardware info and xsession error file.  I am using a Samsung SyncMaster 175v monitor.  Version 10.10 worked well, with not issues, and was fully updated. I followed the upgrade directions, I believe.

Any suggestions based on the errors in the xsession error file?

Thank you.

---

### Post by m00p on 2011-05-07
I have the same problem, it also started from yesterday, maybe it is because of a update.

I have run in recovery mode, and runned the for repairing broken packages en apt-get update. But it didn't helped

---

### Post by bhasi75 on 2011-05-07
I too have the same problem. Am still able to use the system using the terminal (invoked with Ctrl + Alt + T). 

apt update did not help.

---

### Post by AVStudio on 2011-05-07
Same deal here.  I tried dpkg-reconfigure on things like gnome-session, gnome-shell, xserver-xorg.  nothing fixed...How about rolling back updates? Didn't gnome go from 3.0.0 to 3.0.1?  Anybody get this issue on older gnome?  More questions than answers I'm sorry

---

### Post by AVStudio on 2011-05-07
okay i got back in to gnome from the terminal.  by realizing my gnome-session package was being held back from apt-get upgrade.  i purged the package, reinstalled and now no problems. so thats:

sudo apt-get update
sudo apt-get upgrade #see if the package is held back
sudo apt-get purge gnome-session
sudo apt-get install gnome-session
startx

that was my command list and all is well.  Hope this helps!:)

---

### Post by bhasi75 on 2011-05-07
Thank you for the commands and information. 

I executed all the commands in the ubuntu recovery, this shows me the icons on the desktop but not the default theme which was earlier (i wish to see the icons on the left side of the screen and the top bar showing who's logged in, network status,etc)

I logged out of the recovery and logged in with Ubuntu Netbook, only wallpaper is shown.

---

### Post by bhasi75 on 2011-05-07
Finally got the desktop in 11.04 though not the one i am looking for. 

While logging into the system after providing the password (do not hit enter), select Ubuntu Classic from the bar at bottom of the screen. 

Hope this helps you too.

---

### Post by Lamukra on 2011-09-04
> **AVStudio said:**
> okay i got back in to gnome from the terminal.  by realizing my gnome-session package was being held back from apt-get upgrade.  i purged the package, reinstalled and now no problems. so thats:

sudo apt-get update
sudo apt-get upgrade #see if the package is held back
sudo apt-get purge gnome-session
sudo apt-get install gnome-session
startx

that was my command list and all is well.  Hope this helps!:)

If this will not help try this

1. Go to shell or recovery console
2. Then try to install gnome-accessibility-themes

```
apt-get install gnome-accessibility-themes
```

if it is installed try to reinstall it and reboot

It solved my issue at least

I took it from here

_[How do I install the lates version of Gnome 3?]("http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3")_

look on answers on July 10

Still cannot fully solve the problem with gnome 3, but at least can log in

---

