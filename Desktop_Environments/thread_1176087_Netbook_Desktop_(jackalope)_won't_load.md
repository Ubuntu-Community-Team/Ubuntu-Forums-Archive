---
title: "Netbook Desktop (jackalope) won't load"
date: 2009-06-01
forum: Desktop Environments
---

### Post by mr_bijae on 2009-06-01
I'm running the Netbook Remix ubuntu 9.04. I've had it running for two weeks with out an error. I installed some additional applications and the system hung. I got it restarted but when I did I noticed that the application bar wasn't loading. I used the navigation bar on the left to get to the Administration and Switch Desktop Modes. I switched it to Classic mode. This worked for a day or two. I was able to swtich once the system was fully up and work without issue. Here lately the system would no longer load when switched. Here are the steps I took to correct it. 

I created an application launcher to allow me to start terminal (as no applications were available).
Right Click Desktop -> Creat Launcher -> /usr/bin/xterm

Next launch the terminal and type the following command: 

killall gnome-panel: gnome-panel

When I launched this I received the following messages:

mr@mr-laptop:~$ killall gnome-panel; gnome-panel
gnome-panel: no process killed
** (gnome-panel:4200): DEBUG: Adding applet 0.
** (gnome-panel:4200): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:4200): DEBUG: Adding applet 1.
** (gnome-panel:4200): DEBUG: Adding applet 2.
** (gnome-panel:4200): DEBUG: Adding applet 3.
** (gnome-panel:4200): DEBUG: Adding applet 4.
** (gnome-panel:4200): DEBUG: Adding applet 5.
** (gnome-panel:4200): DEBUG: Adding applet 6.
** (gnome-panel:4200): DEBUG: Adding applet 7.
** (gnome-panel:4200): DEBUG: Adding applet 8.

(gnome-panel:4200): Gdk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window

(gnome-panel:4200): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:4200): DEBUG: Adding applet 9.
** (gnome-panel:4200): DEBUG: Adding applet 10.
** (gnome-panel:4200): DEBUG: Adding applet 11.
** (gnome-panel:4200): DEBUG: Adding applet 12.

At first I was concerned because the application bar was back to normal. I had to leave this terminal window open to keep the application bar working. If I closed this terminal the application bar was gone. 

Next I noticed that the windows did not have the windos controls. I could not move them, recize them or ALT+TAB to get to another window. I did some research and found that running a second terminal window with the following command returned the windows controls

$ gnome-wm

This was a one time fix and had to run these both after each start up. To solve the problem permanently I added gnome-wm and gnome-panel to the Start Up Applications. When I added these to the Startup Applications and rebooted the sytem it worked just as expected!

---

