---
title: "Change show desktop icon or minimize all script"
date: 2007-04-17
forum: Desktop Effects &amp; Customization
---

### Post by SiCk949 on 2007-04-17
Hi! I'm using Ubuntu 7.04 Beta with Compiz and I wanna change the "show desktop" icon, image:

[IMG]http://img256.imageshack.us/img256/1347/untitled2du6.jpg[/IMG]

Well, as you can see the icon has an ugly grey background that break my desktop :(

I tried two things:
- First, I tried to make a "thrower" (don't know if the translation is correct, i have the spanish version, here its called "Lanzador"). I had not found any command or script for show desktop (or minimize all windows, the same)
- Editing in app metacity panles gnome conf. but the type of "object" that the "show desktop icon" is not allow you to change the icon.

What I need:
- To know how to make a "thrower" for minimize all windows where I can set up a personalized icon OR
- To know how to change this icon for another one (physically or via configuration).

Sorry for my bad english and thanks in advance!

---

### Post by SiCk949 on 2007-04-17
nobody? :(
please!

---

### Post by Jhongy on 2007-04-18
I'd love to know too :-)

---

### Post by SiCk949 on 2007-04-19
Seems that nobody knows :(

---

### Post by thelinuxguy on 2007-04-21
Couldn't find anything....but if your concern is your desktop not being matched by the icon then remove it and use CTRL + ALT + D to minimize all windows and back.

---

### Post by tennyis on 2007-04-22
> **thelinuxguy said:**
> Couldn't find anything....but if your concern is your desktop not being matched by the icon then remove it and use CTRL + ALT + D to minimize all windows and back.

Anyway of changing it to be Windows key and M? I am switching from Windows and am used to that.

---

### Post by thelinuxguy on 2007-04-23
> **tennyis said:**
> Anyway of changing it to be Windows key and M? I am switching from Windows and am used to that.

When using Beryl as the Window Manager, Win + D is the shortcut to minimize all windows. If you have Beryl installed, you can configure this under 
Applications >> System Tools >> Beryl Settings Manager >> General Options >> Shortcuts >> Bindings.

Under Metacity, I couldn't configure Win + D or Win + M since it won't allow me to select anything after the Win key had been pressed. You can change it to Alt + Win however. 
System >> Preferences >> Keyboard shortcuts >> Window management.

---

### Post by blackened on 2007-04-23
I think this icon can be found either in /usr/share/*name of icon theme* or in /home/*username*/.themes/*name of icon theme*.

If you can't find it there then you might check in /usr/share/icons/hicolor or /usr/share/pixmaps.

I'm (woefully) typing this from a Windows machine, but will check tomorrow on my machine at home and give you an answer either way.

---

### Post by tennyis on 2007-04-23
Thanks, that seems to have worked :) yay windows key!

---

### Post by charlemagne86 on 2008-05-23
> **blackened said:**
> I think this icon can be found either in /usr/share/*name of icon theme* or in /home/*username*/.themes/*name of icon theme*.

If you can't find it there then you might check in /usr/share/icons/hicolor or /usr/share/pixmaps.

I'm (woefully) typing this from a Windows machine, but will check tomorrow on my machine at home and give you an answer either way.
hey had been lookin 4 the same thing too....
as u suggested searched....and found the show desktop icons here:
> 
/usr/share/icons/gnome/scalable/places

however, by what i can see, they are all having transparent backgrounds..so stumped!!!!

---

### Post by charlemagne86 on 2008-05-24
OKAY PPL

breakthrough achieved......i got th esolution to making a transparent background launcherfor show desktop::

first download the package "wmctrl" from the repositories....refer to its man page for detailed usage

now create a custom application launcher on the panel, choose the transparent backgrounded icon present in /usr/share/icons/gnome/scalable/apps  or create your own and use it...

in the command option enter the comand wmctrl -k on and exit

now whenever you click on the show desktop icon, it will show the desktop....but another click wont undo the effect!!!

---

