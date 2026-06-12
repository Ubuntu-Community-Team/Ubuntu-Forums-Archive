---
title: "KDE GTK App Fonts"
date: 2005-11-29
forum: Desktop Environments
---

### Post by elias4444 on 2005-11-29
Ok, this has just bothered me for far too long. I really like KDE, but keep going back to Gnome primarily because of the weird font issues in KDE. In KDE, I have to shrink the fonts down to like size 8 or less for them not to appear too big, and even then, when I run a GTK app, the fonts in that app are still way too big. I've gone into the Appearance-GTK fonts section and told it to match the fonts, but then if I ever run Gnome, it's font settings are all messed up.

A long time ago, when running Gentoo, I was able to fix this by manually specifying the DPI - but in Ubuntu I'm not sure how to do that - and honestly, I'm curious why I should have to find a way? Ubuntu does everything else right! :p 

Any ideas?

---

### Post by elias4444 on 2005-12-01
shameless bump... hoping for a helpful reply...

---

### Post by jonesy on 2005-12-01
I remember I used to be able to fix this by running gnome-settings-daemon.  I believe you have to edit a gtkrc file of sorts.  Check the gentoo forums,  I KNOW there is something there on how to do this, I just don't have the time right now to hunt it down, sorry, and good luck!

---

### Post by vh1 on 2005-12-02
are you using KDM?

if you are, then you're looking for the file /etc/kde3/kdm/kdmrc

there's an option there called ServerArgsLocal, or ServerLocalArgs. just put "-dpi 96" on the end of that line and restart KDM

---

### Post by elias4444 on 2005-12-02
Is there a way to do that when using GDM?

---

### Post by chele on 2005-12-03
I don't know if it will help in your case, but you may want to force the system to know about the true dpi of your monitor.

:~$ cat /var/log/Xorg.0.log | grep DPI
(==) RADEON(0): DPI set to (75, 75)

75dpi is so 1985. In order to correct it, measure your visible screen with a ruler and add the following to the Monitor section of the /etc/X11/xorg.conf file:

DisplaySize  306 229

Then restart the X11 session (CTRL-ALT-BACKSPACE).

That example is the dimensions of my 15" lcd, in mm. Adjust to the actual values for your screen.

This results in:

:~$ xdpyinfo | grep dimensions
  dimensions:    1600x1200 pixels (306x229 millimeters)
:~$ cat /var/log/Xorg.0.log | grep DPI
(**) RADEON(0): DPI set to (133, 133)

In Gnome, go to System > Preferences > Font > Details and adjust the dpi setting to the same value as xorg now reports. I assume KDE has a similiar setting.

---

