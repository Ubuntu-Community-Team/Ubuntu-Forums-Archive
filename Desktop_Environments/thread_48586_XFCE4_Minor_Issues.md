---
title: "XFCE4 Minor Issues"
date: 2005-07-13
forum: Desktop Environments
---

### Post by DimitrisChr on 2005-07-13
I have installed XFCE4 in my Ubuntu installation and i have some questions as a new user:
The Delete button on the keyboard doesn't seem to do anything unlike in Gnome where its used as in windows to send files to the trash can. Is there a way to activate it or did i do something wrong. Also the print screen button is inactive.

Another problem i faced is that when i create a launcher and i type a command to be executed in terminal mode (like sudo wvdial) nothing happens. But when i open a terminal and type the exact same command myself it works fine. I found this to be happening everytime i had to create a launcher that used the sudo command followed by something else. Is there an issue with the sudo command in XFCE?

I posted another thread before about the menu in XFCE. Smeg doesn't work with XFCE since nothing changes when i edit the menu (only in gnome). The menu editor that comes with XFCE doesn't let you change the system menu that is autogenereted by the system itself.  I gave up looking for a solution and i deleted the menu and started creating my own from scratch.

If anyone can help with the above issues plz let me know. Thanks!!!

---

### Post by psychicdragon on 2005-07-13
To change the delete hotkey in rox do this:

in your home directory
gedit .gtkrc-2.0

paste this in:
gtk-can-change-accels = 1

then save the file

Open up rox

right click on something > open the file/dir menu > mouseover Delete > press the delete key twice.

I don't know why it uses ctrl + x as a default when every other file manager ever uses delete.

What does print screen do in gnome take a screenshot?

If you want to use sudo in a launcher use: 'gksudo command'

The menu thing bothered me too at first. I made my own with the menu editor and it's now exactly the way I wanted it.

---

