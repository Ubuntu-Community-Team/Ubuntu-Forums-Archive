---
title: "customization in xfce"
date: 2005-04-24
forum: Desktop Environments
---

### Post by Pulka on 2005-04-24
i'm loosing my mind with xfce!!!

it's all very nice and pretty, but not intuitive.

I can't seem to find out how the hell to add launchers (with their icons) in xfce panel. I can add the lauchers, but then i can't substitute the icons.

Another thing...i don't know how to associate files with programs. My jpeg's only open if i drag and drop to an image viewer program. The same happens with a bunch of other files.

Yet another thing...how the hell can i deactivate the option of opening windows with just one click of the mouse?

In gnome it's all so much easy :)

---

### Post by Psquared on 2005-04-24
[QUOTE=Pulka]i'm loosing my mind with xfce!!!

it's all very nice and pretty, but not intuitive.

I can't seem to find out how the hell to add launchers (with their icons) in xfce panel. I can add the lauchers, but then i can't substitute the icons.

Another thing...i don't know how to associate files with programs. My jpeg's only open if i drag and drop to an image viewer program. The same happens with a bunch of other files.

Yet another thing...how the hell can i deactivate the option of opening windows with just one click of the mouse?

In gnome it's all so much easy :)[/QUOTE]

I have not had this problem with Xfce 4.2 using the binary installer. What version are you using? You also may not have installed all the extras.

What happens when you right click on the panel to add a program? Does it open a window where you can add different categories?

I've played around with Xfce some so give me some details and I'll try to help you.

---

### Post by Pulka on 2005-04-24
i'm using version 4.2.1. I installed it throuh synaptic, and i installed a lot of extras.

When i right click in the panel, it gives me three choices: "add new item", "remove", "properties".
If i click add new item, i have a lot of choices...i can add the launcher, that's not the problem. i just can't change the icon

---

### Post by Xanf on 2005-04-24
I'd suggest to look for icons in /usr/share/pixmaps ....

---

### Post by Psquared on 2005-04-24
[QUOTE=Pulka]i'm using version 4.2.1. I installed it throuh synaptic, and i installed a lot of extras.

When i right click in the panel, it gives me three choices: "add new item", "remove", "properties".
If i click add new item, i have a lot of choices...i can add the launcher, that's not the problem. i just can't change the icon[/QUOTE]

If you click on the icon button in the panel after you add a launcher you can pick any icon you want. Just browse the pixmaps directory or you can pick an icon from a theme. I think for an icon in the panel you want an icon that is 48x48 pixels or one that is scalable.

The version available from os-cillation is Xfce 4.2.1.1 - but I think that is just a minor upgrade from the one you got from Synaptic.

---

### Post by Pulka on 2005-04-24
[QUOTE=Psquared]If you click on the icon button in the panel after you add a launcher you can pick any icon you want. Just browse the pixmaps directory or you can pick an icon from a theme. I think for an icon in the panel you want an icon that is 48x48 pixels or one that is scalable.[/QUOTE]

Yeah, that works in gnome. But in xfce, the option to change the icon doesn't appear. In gnome, if i click in the icon, it lets me choose another one. In xfce, it only lets me define what kind of app it is (network, multimedia, etc)

---

### Post by eric71 on 2005-04-25
When you right click a launcher and select "properties", does the window you get look like this (see attachment)?  It should, and you just click on the folder icon to open a GTK type file selector to choose your custom icon.

---

### Post by tread on 2005-04-25
How do I keep just one panel in xfce? I have one for the windows, workspace switcher etc. and one for the menu, applets etc. Can't I just have one? My resolution is 1280x800 .. so having two panels really eats into screen space, and I don't like panels on the side.

---

### Post by eric71 on 2005-04-25
Also, you can set the default run action this way:

If using Rox-Filer, right click on the file and under the "file" portion of the menu you should find "set run action".

For Xffm, right click on the file, chose "open with".  It will give you a little text box where you can enter the command, and check the box so it remembers the choice.

---

### Post by eric71 on 2005-04-25
[QUOTE=tread]How do I keep just one panel in xfce? I have one for the windows, workspace switcher etc. and one for the menu, applets etc. Can't I just have one? My resolution is 1280x800 .. so having two panels really eats into screen space, and I don't like panels on the side.[/QUOTE]

If you see my screen capture from my answer (above) about setting default run application, you can see my single panel in one of them.  It's hidden in the other.  I typed "killall xftaskbar4" in a terminal (not root) to get rid of the taskbar and saved the session to make it permanent.  I use the taskbar plugin (xfce4-taskbar-plugin, available in synaptic) in the main panel to make something that is just a little bit to0 windows like, but it's what I'm comfortable with.

---

### Post by tread on 2005-04-25
Thanks Eric, will try that! That was really the only thing keeping me from xfce .. I really liked the speed.

---

### Post by Pulka on 2005-04-25
thank you all! I Managed to solve the problems

---

### Post by eric71 on 2005-04-26
[QUOTE=Pulka]thank you all! I Managed to solve the problems[/QUOTE]

You're welcome.  Xfce is a great desktop, and you can basically make it do whatever you want - it's just not always as intuitive as Gnome.  My Xfce desktop and my Gnome desktop look almost identical (except the Xfce panel applets are much prettier for some reason) but the Xfce desktop took a lot more effort to set up.  You give up some ease of use (ie. having to set up applications to use for different mime types, doing all the launchers by hand, etc.) , but Xfce packs a lot into a little bit of disk space.  Xfce seems to run with a baseline memory usage of about 30 megabytes less than Gnome with the same applications running.  So if you've got limited memory, that can make all the difference.  And if you've got limited disk space, I think Xfce with most of the themes and plugins installed takes up like 50 mb, whereas Gnome is somewhere like 350 or more mb.  All those extra megabytes do add some more funtionality, and if you've got the hardware you might as well run Gnome.  I've got the hardware to run Gnome, but I keep going back to Xfce because for whatever reason I just like the way it looks and feels.  It's just got a little steeper learning curve than Gnome, which is about as easy as it gets.  Both are awsome inthe right situations.

---

### Post by Psquared on 2005-05-06
I installed Xfce using the os-cillation binary installer. I installed rox-filer in synaptic. When I start rox-filer it gives me an error about a symbolic link for icons. It says it exists, but it can't call the icons. As a result, I have rox-filer running, but the icons all look like yield signs.

Is that because I mixed the apps between the Xfce installer and the files in the repos?

Anybody know how to fix it?

---

### Post by suoko on 2005-05-08
try removing (or renaming) the mentioned simbolic link and re-choosing an icon theme.

---

