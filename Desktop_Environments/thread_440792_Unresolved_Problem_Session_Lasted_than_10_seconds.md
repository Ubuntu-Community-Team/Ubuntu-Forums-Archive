---
title: "Unresolved Problem: Session Lasted than 10 seconds"
date: 2007-05-11
forum: Desktop Environments
---

### Post by pcpete on 2007-05-11
Yes, I realize this problem has been posted within the forum/on google... But many of the methods I have seen will not fix Gnome or KDE from having an error "Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem..." 

I was logged into **Fiesty 7.04 for days...** Everything was stable and I installed the KDE windows manager for messing around with a cool mac-look (and not risk messing up a beautifully simple gnome). 

I have tried reccommendations in the following forums:
[http://ubuntuforums.org/showthread.php?t=80599&highlight=session+lasted](http://ubuntuforums.org/showthread.php?t=80599&highlight=session+lasted)
(and some other one I will post link of..)

Here is the error that I am recieving within the ~/.xsession-errors file: 
----------------------------------------------
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running : /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "pete"

/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 17 id: not found
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator
exec: 224:  x-terminal-emulator: not found
-----------------------------------------------

I have tried: 

1.) chown on the .ICEauthority file in my home folder 
2.) recovery mode reinstall of libgnome 

I am frustrated, but maybe someone understand my trouble! Thanks for your help; I really appreciate this forum. If I find solutions, I'll post them!

---

### Post by pcpete on 2007-05-12
You know what, this is strange!... I ran some KDE stuff in Gnome (which would cause the windows error). 

[http://ubuntuforums.org/showthread.php?t=23467](http://ubuntuforums.org/showthread.php?t=23467)

But these recommendations didn't work.! ^

---

### Post by pcpete on 2007-05-12
[http://www.justlinux.com/forum/showthread.php?threadid=138003](http://www.justlinux.com/forum/showthread.php?threadid=138003)

Nothing in this thread seemed to work. Anyone have trouble with some type of error 17?

---

### Post by rug2 on 2007-05-14
Hey guys,

I had a similar problem after updating to Feisty via the Update Manager. 

I disabled the splash screen from gconf-editor and everything works now. The show_splash_screen is found at /apps/gnome-session/options/splash_image in gconf-editor, just remove the tick to disable.


Hope this helps,
vxc

---

### Post by tawniteamo on 2007-05-18
I am having a similar problem whilst attempting to install feisty from the live cd. it was an original from canonical, not burned, and I have tried 3 of them, and get the same error.

---

