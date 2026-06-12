---
title: "fluxbox plus parts of gnome running? Where startups defined?"
date: 2012-02-14
forum: Desktop Environments
---

### Post by flemur13013 on 2012-02-14
Hi - 

I have ubuntu 10.04/64 with fluxbox replacing gnome window manager - I think.  

Previous installs of fluxbox automagically gave it as a login option, but this time it didn't and I had to change 
"Session=fluxbox" in ~/.dmrc to make it show up at login - after some other goofing around - and I'm wondering if I have extraneous parts of gdm/gnome running, and also how to stop some processes from starting (they aren't listed in ~/.fluxbox/startup, and get started somewhere else - where?).

Sometimes I have two backgrounds!  I can drag the top one like a regular window (SUPER-Left mouse). 
The bottom one is set with ~/.flubox/lastwallpaper 
This goes away after logout/reboot and could be from running gnome-session-properties or nautilus without --no-desktop.

**Here's the processes in question**: should they be running when fluxbox is running? 
My questions/comments are in (?), in caps to see easier, not yelling! :
 ++

root /usr/lib/pulseaudio/pulse/gconf-helper
  (**?**)

root /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-uat5TC/database -nolisten tcp
  (**SHOULD THE ABOVE TWO BE RUNNING? gdm and gnome?** )

gdm   /usr/bin/dbus-launch --exit-with-session
root  /usr/lib/gdm/gdm-session-worker
  (**SHOULD THE ABOVE TWO BE RUNNING? gdm ??** )

user  /usr/bin/gnome-keyring-daemon --daemonize --login
  (?)

user  sh /home/user/.fluxbox/startup
user  /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/startfluxbox
user  /usr/bin/dbus-launch --exit-with-session /usr/bin/startfluxbox
   (HOW fluxbox GETS STARTED)

user  nm-applet
user  gnome-volume-control-applet
   (THE ABOVE TWO ARE STARTED IN ~/.fluxbox/startup - do they start other gdm/gnome components?)

user  fluxbox
   (OK!)

user  /usr/bin/gnome-screensaver --no-daemon
   (IT'S SET TO INACTIVE WITH gnome-screensaver-preferences)
   (**Where does it get started?!?!?**)
   (??? **[SIZE="3"]_HOW CAN I TURN THIS OFF?_[/SIZE]** IT'S NOT IN "startup" FILE.)

user  /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
root  [kondemand/0]
root  [kconservative/0]
   (?? KDE stuff - or to do with CPU frequency ?? I don't have KDE unless some of it got installed with another package)

 ++

Thanks!

---

### Post by Rodney9 on 2012-02-14
I hope  some of these will help you - 

[http://www.batushkas.com/linux-desktop-tips/52-using-fluxbox-with-gnome.html](http://www.batushkas.com/linux-desktop-tips/52-using-fluxbox-with-gnome.html)

[http://www.wikihow.com/Configure-Fluxbox](http://www.wikihow.com/Configure-Fluxbox)

[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

[http://blog.bodhizazen.net/linux/a-5-minute-guide-to-fluxbox/](http://blog.bodhizazen.net/linux/a-5-minute-guide-to-fluxbox/)

Rodney

---

### Post by flemur13013 on 2012-02-14
I stopped gnome-screensaver from starting by renaming the /etc/xdg/autostart/ .desktop file (and did the same to some other files).

startup locations:

/usr/share/gnome/autostart/  : nonexistent
/usr/share/autostart/        : nonexistent
/etc/xdg/autostart/  : many programs; gnome-screensaver was here.
/usr/share/gdm/autostart/ : has LoginWindow only
~/.config/autostart/ : more programs

I guess some gdm/gnome processes should be running under fluxbox because fluxbox is a window manager and gdm is a display manager....

---

