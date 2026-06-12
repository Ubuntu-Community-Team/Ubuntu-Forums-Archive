---
title: "Getting an icon on the desktop"
date: 2011-11-10
forum: Desktop Environments
---

### Post by rfbeck on 2011-11-10
I use Gnome classic (as opposed to Unity). I would like to put some icons on the desktop. How can I do this? Thanks.

---

### Post by An Sanct on 2011-11-10
Have you tried right-clicking on the item in the menu, you would like to have as a shortcut on the desktop and selecting "Add this launcher to desktop"?

---

### Post by rfbeck on 2011-11-22
I have tried that, but it doesn't seem to work. When I right click on an icon in the menu, it simply launches the program.
Any further help?
______
Robert

---

### Post by hhh on 2011-11-22
I don't use  Oneiric, so this might have changed, but right-click the desktop, there should be a menu item to "Create Launcher". Then you can enter the name (ex: Banshee), the command (banshee should be enough, or you can use the full path /usr/bin/banshee) and choose an icon (usually in /usr/share/pixmaps or /usr/share/icons/hicolor/48x48/apps).

---

### Post by rfbeck on 2011-11-22
Nope, that doesn't do it either, but thanks. I'm using Gnome Classic, and it seems to have lost a certain amount to functionality, much to my dismay. 
_______
Robert

---

### Post by rfbeck on 2011-11-23
What I found works for me is to "left" click and drag an icon from the top panel menus. 
______
Robert

---

### Post by jimmydean886-2 on 2011-11-23
First off, GNOME needs to know that you want desktop icons. To get these, you need the GNOME Tweak Tool.

you can find it in the software center as "Advanced Settings" or type in a command line:

```
~$ sudo apt-get install gnome-tweak-tool
```Then, launch it from Applications>>Accessories>>Advanced Settings.
go into the desktop screen on the sidebar and move the slider that has Nautilus (the file manager) handle the desktop.

Now, open a file browser window. DO NOT OPEN IT WITH SUDO.
Navigate to /usr/share/applications

Copy and paste whatever you want to your desktop folder, and you're all set.

---

### Post by rfbeck on 2011-11-24
That worked great. Thank you.

______
Robert

---

