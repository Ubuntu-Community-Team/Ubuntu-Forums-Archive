---
title: "I need help with gnome menu items/commands"
date: 2006-01-19
forum: Desktop Environments
---

### Post by ardchoille on 2006-01-19
I am using Ubuntu 5.10 with gnome. I have installed fluxbox and openbox (using openbox as the wm in gnome) and I would like to set up the menus for these two window managers. I have most of the menus set up and am in need of the commands/apps that are launched when clicking on the following items in gnome:

From nautilus:
1) File -> Empty trash
2) File -> Close All Windows
3) Go -> Clear History

From the System menu:
4) Take Screenshot
5) Help
6) About gnome
7) About Ubuntu

Also, does anyone know how to get/use a notification area app/dockapp without having to run the gnome panel or kde kicker? A working dockapp would be nice but I can't find one that can handle more than 4 notification area icons at one time. Running apps that use the notification are in openbox is a problem as this window manager does not have a notification area - neither do WindowMaker or blackbox and I need to be able to use notification area icons.

That's it, I should be good to go once I have these items taken care of for the two window managers :)

EDIT: OK, I got most of these. The only thing I need now is to know which file(s) gnome edits when you click on "Go -> Clear History". I'd like to make a script that does this on a regular basis but I need the command or file. Anyone got any ideas about this?

---

### Post by ardchoille on 2006-01-20
I found an app in the repos. The app name is Docker and is a suitable notification area replacement when running a window manager which does not include a notification area. Be advised, however, that if you launch Docker **while** you have a notification area applet in your gnome panel, gnome will hang with no alternative except to turn off the power to the machine. Docker will run fine **after** you remove the gnome notification area applet from the gnome panel.

EDIT: When running docker while you have a notification area applet active in the gnome menus, docker will cause the system to hang to the point that the user is forced to reset the power on the machine. This is **totally unacceptable** behaviour and I will not use this app until some kind of safeguard is implemented.

---

### Post by ardchoille on 2006-01-23
Anyone have any ideas about the items in the first post?

---

### Post by ardchoille on 2006-01-29
Anyone?

---

### Post by bluevoodoo1 on 2006-02-14
I don't know a solution to the Go > Clear History... but could you be so gracious and post the commands to the others you mentioned?

---

