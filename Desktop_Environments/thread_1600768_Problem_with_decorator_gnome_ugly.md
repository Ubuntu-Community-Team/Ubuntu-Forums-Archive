---
title: "Problem with decorator gnome ugly"
date: 2010-10-19
forum: Desktop Environments
---

### Post by Syirrus on 2010-10-19
I did a fresh install of 10.10 x64 (automatically applied updates) and when I get into gnome it looks like this:



[ATTACH]172850[/ATTACH]



Notice how every other windows but the "Appearance Preferences" is ugly gray. How do I fix this?


Syirrus

---

### Post by perlid on 2010-10-19
I've got the same problem. Using Xubuntu 10.10 (and hence Xfce). In ~7 out of 10 logins I will get the default GTK+ theme (i.e. the only look), rather than the GTK+ theme I've chosen. It seems that the GTK+ theme configuration is just ignored. It also affect the icon theme, which defaults to the GNOME theme. However, the Xfce window manager theme is always correct. Going to the GTK+/Icon theme changes will not help, any selection I make in that dialog has no effect on the running session. If I log out and in a few times I usually end up with the correct desktop. Very annoying.

---

### Post by Syirrus on 2010-10-19
Whenever I log out and log back in I get the same thing with GTK.  I'm puzzled.....  Compiz works and everything else, I just get a messed up theme. 

Syirrus

---

### Post by bepcyc on 2010-10-23
> **Syirrus said:**
> I did a fresh install of 10.10 x64 (automatically applied updates) and when I get into gnome it looks like this:

I have the same configuration. First boot was ok, next boot I had this ugly default GTK icons. My first thoughts were of fresh updates and nvidia restricted driver. 

Guess we need to file a bug..

---

### Post by rbaietta on 2010-10-29
Hi, I have the same problem (see attached file): decorations are not applied to any window except the "appearance" configuration window. The menu bar, as well as any other menu, appears as bare as plain old "motif" decorations.
 
My 10.10 installation started from scratch, I am not able to state if the problem started after installing the first program from KDE of after having installed ATI graphic driver FGLRX.
 
Does anyone know if a bug has been filed, or a solution given?
 
Thank you

---

### Post by Dubhghaill on 2010-10-30
Hi All

I'm having the exact same problem on 10.10. My install is an upgrade from 10.4. I've got a radeon 5750. I've tried both the fglrx driver and the open source ati driver and have the problem with both. When I open up the appearance preferences window (which is the only one styled correctly) it shows me as having a custom theme selected instead of ambiance. Changing back to ambiance doesn't help.

Logging out and in a few times tends to fix the problem. I've dug around in syslog and a few places but can't find any gtk error messages or anything relevant. If anyone has submitted a bug please let me know otherwise I'll submit one.

Thanks

---

### Post by Dubhghaill on 2010-10-30
More people seem to be having the problem here: [http://gutsywww.ubuntuforums.org/showthread.php?p=10037882#post10037882](http://gutsywww.ubuntuforums.org/showthread.php?p=10037882#post10037882) and someone has submitted a bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/667640](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/667640)

---

### Post by Dubhghaill on 2010-10-31
I've found if you create a text file in your home directory called .gtkrc-2.0 and add the following lines to it:

include "/usr/share/themes/Ambiance/gtk-2.0/gtkrc"
 include "/home/sean/.gtkrc-2.0.mine"
gtk-icon-theme-name = "ubuntu-mono-dark"
gtk-theme-name = "ubuntu-mono-dark"

That should get you the default 10.10 gtk and icon theme.

---

### Post by Lokiii on 2010-11-02
> **Dubhghaill said:**
> I've found if you create a text file in your home directory called .gtkrc-2.0 and add the following lines to it:

include "/usr/share/themes/Ambiance/gtk-2.0/gtkrc"
 include "/home/sean/.gtkrc-2.0.mine"
gtk-icon-theme-name = "ubuntu-mono-dark"
gtk-theme-name = "ubuntu-mono-dark"

That should get you the default 10.10 gtk and icon theme.

I had the same issue! This seems to have fixed it! Thanks!

Hope this bug gets sorted out eventually though!

---

