---
title: "Trouble constructing xorg.conf file"
date: 2011-01-06
forum: Desktop Environments
---

### Post by who-bear on 2011-01-06
I'm very new to Ubuntu (and Linux). I'm using a 13" Acer TimelineX and Ubuntu 10.10 with an external monitor. Since my system will only detect lower resolutions than I want, I am running: $ xrandr --addmode VGA1 1366x768 upon start-up.

I would like to use the xorg.conf file as a better fix (ie. not load in one resolution and then switch to another). I found this website helpful: [https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions) but I am still lost when it comes to constructing the file itself.

Thank you all very much in advance!

---

### Post by Krytarik on 2011-01-06
Since I recently didn't get Xorg to set the desired display mode by configuring the xorg.conf according that guide, I recommend setting it via the kdm/gdm startup scripts, also described in that guide, it worked for me. IMO it doesn't make a real difference vs. the xorg.conf-way.
> **Setting xrandr commands in kdm/gdm startup scripts**

 Both  KDM and GDM have startup scripts that are executed when X is initiated.   For GDM, these are in /etc/gdm/ , while for KDM this is done at  /etc/kde4/kdm/Xsetup.  In either case, you can paste in an xrandr  command line string into one of these scripts.   For GDM, try putting  them right before initctl -q emit login-session-start DISPLAY_MANAGER=gdm in /etc/gdm/Init/Default 
This  process requires root access and mucking around in system config files,  but will take effect earlier in the startup process than using  .xprofile, and will apply to all users including the login screen. 

---

### Post by who-bear on 2011-01-08
I added the line I'd been using on start-up("$ xrandr --addmode VGA1 1366x768") to /etc/gdm/Init/Default after the line "/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm" but I still had the same problem when rebooting. It loaded into the wrong resolution initially and then resized after login and loading everything (probably due to the start-up command).

---

### Post by Krytarik on 2011-01-08
> **who-bear said:**
> I added the line I'd been using on start-up("$ xrandr --addmode VGA1 1366x768") to /etc/gdm/Init/Default after the line "/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm" but I still had the same problem when rebooting. It loaded into the wrong resolution initially and then resized after login and loading everything (probably due to the start-up command).
You also have to *set* it, like this:```

xrandr --addmode VGA1 1366x768
xrandr --output VGA1 --mode 1366x768
```You should test it from a terminal before, if this works, then the automatic way will also work, and it will not set the display to another mode before.

---

### Post by who-bear on 2011-01-10
That worked perfectly. Thanks a million!

---

