---
title: "Another Resolution Thread"
date: 2005-09-10
forum: Desktop Environments
---

### Post by Mr. Smiley on 2005-09-10
Im a total noob and I need some help.
I have a dell M780 Monitor. Im stuck at a resolution of 640X480 and refresh rate of 60Hz. Iv tried editing the /etc/X11/xorg.conf file but I can't do anything to the file because its a read only file. So I tried editing the permissions to make it a read/write file but it says I dont have the permissions to do this. Is there an admin account or something? Im just using the username that I made during the installation.
[Here](http://support.dell.com/support/edocs/monitors/M780/Eng/specs.htm) is my monitor preferences if you need them. Im using a voodoo3 Video card. 
Thanks for your help

---

### Post by krusbjorn on 2005-09-10
To be able to edit the xorg.conf file, you must open it with root permissions.

Type "sudo gedit /etc/X11/xorg.conf" in the terminal, and you will be able to edit the file. Remember to make a backup copy first:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

