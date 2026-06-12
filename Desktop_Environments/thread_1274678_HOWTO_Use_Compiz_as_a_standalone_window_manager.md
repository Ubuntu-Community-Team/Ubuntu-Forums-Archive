---
title: "HOWTO: Use Compiz as a standalone window manager"
date: 2009-09-24
forum: Desktop Environments
---

### Post by Tibuda on 2009-09-24
I have created a wiki entry about Compiz Standalone. It is not hard to setup.

[https://help.ubuntu.com/community/CompizStandalone](https://help.ubuntu.com/community/CompizStandalone)

If you have questions or suggestions, please use this thread.

---

### Post by ~sHyLoCk~ on 2009-09-24
Nice effort! I don't use compiz or ubuntu, but thanks for sharing! :)

---

### Post by earthpigg on 2009-09-24
will you consider adding a screenshot or two, or better explaining how the functionality works once the setup is done?

---

### Post by Tibuda on 2009-09-25
> **earthpigg said:**
> will you consider adding a screenshot or two, or better explaining how the functionality works once the setup is done?

I thought about it, but there's nothing really to see. Both the looks and the functionality depends on the stuff you use. With Compiz itself you'll only see your wallpaper (if the plugin is enabled). You can make it look exactly like Gnome if you run Nautilus and Gnome-Panel. I use Gnome-Do classical, Conky and Stalonetray, so I don't have any panel. I think the best way would be a section showcasing different setups. I'll take some screenshots later.

---

### Post by hhh on 2010-01-08
Is this thread still alive? The Community documentation you made doesn't seem quite right using Karmic.

---

### Post by txacoli on 2010-01-21
Here are some screenshots, I'm using lxpanel. This is Crunchbang 8.10 (I haven't swithced to karmic because of my ati radeon), but I did this setup in jaunty as well and it worked out of the box.  This is what I did to make it work: (fetched from)  [http://crunchbanglinux.org/forums/topic/2827/howto-run-compiz-as-a-standalone-window-manager/](http://crunchbanglinux.org/forums/topic/2827/howto-run-compiz-as-a-standalone-window-manager/)
 [INDENT]1)[B] sudo apt-get install compiz fusion-icon emerald compizconfig-settings-manager
[/B]
* if you are doing a fresh install (perhaps only minimal ubuntu and compiz) or you don't have a panel installed, it is recommended the first time you use compiz you should have a panel so you don't get stuck with no gmrun or interface, right-click menus won't work from scratch.  I recommend lxpanel for first time, you can remove it later once you get everything the way you like it.
[/INDENT][INDENT]2) [B]sudo nano /usr/share/xsessions/fusion.desktop
[/B]
(use whatever editor you like, I use nano for fresh install with no other window manager, leafpad if I am in #!)
[/INDENT][INDENT]3) copy and paste the following in to fusion.desktop (note: using GDM in the example, for fresh install you can simply startx or include the menu of your choice):
[B][Desktop Entry]
Encoding=UTF-8
# This is the name you'll see for the session in gdm
Name=Fusion
# This is the comment
Comment=Compiz Fusion Standalone
# The command
Exec=/usr/local/bin/start-fusion.sh
Type=Application[/B]
[/INDENT][INDENT]4) now create the start-fusion.sh:
[B]
sudo nano /usr/local/bin/start-fusion.sh[/B]
[/INDENT][INDENT]5) copy this in to the start-fusion.sh and edit it to include whatever you would normally include in your autostart.sh, I don't recommend starting conky it's a bit buggy, you can work with it after you are done:
[B]#!/bin/bash
compiz ccp &
emerald &         #edit to add: this is optional, you don't need emerald at all.
fusion-icon &
lxpanel    #or whatever panel you prefer, or no panel if you are brave[/B]
[/INDENT][INDENT]6)  save and make the file executable:
**sudo chmod +x /usr/local/bin/start-fusion.sh**
note:  I recommend you start with the few items you definetly must have in your startup, then add others a few at a time in case they get buggy.  The last item does not need the ampersand "&" at the end.  However if  you kill this app your session will exit.  This can be useful or annoying.
[/INDENT]

---

### Post by Gryphen on 2010-06-20
Is there a way to have compiz draw the wallpaper and have desktop icons?

---

### Post by bigsmitty64 on 2010-06-20
> **Gryphen said:**
> Is there a way to have compiz draw the wallpaper and have desktop icons?

Unless somethings changed recently, I don't believe you can do that yet. :(

---

### Post by Tibuda on 2010-06-20
> **Gryphen said:**
> Is there a way to have compiz draw the wallpaper and have desktop icons?

Yes, with the [FolderView screenlet](http://gnome-look.org/content/show.php/Folderview+Screenlet?content=102890).

---

### Post by bedbug on 2010-06-29
I am using the attached script for logout
Idea is stolen from ob-logout

---

### Post by onlygaryd on 2010-09-05
> I am using the attached script for logout
Idea is stolen from ob-logout

Where do you place the script? I downloaded it and linked to it in awn, but it doesn't work. I have a minimal Lucid system with compiz.

---

### Post by airydragon on 2010-11-17
> **Gryphen said:**
> Is there a way to have compiz draw the wallpaper and have desktop icons?

i am using [nitrogen]("http://projects.l3ib.org/nitrogen/") for wallpaper. and it is also in maverick repo. 

im still looking for an elegant solutions for
* desktop icons instead of natilius
* tray instead of stalonetray
* session functions (log out / switch user etc.)

---

### Post by ssuuddoo on 2011-10-07
for desktop icons try: idesk - it is very good, simple but candy.
for a nice panel with the systray: tint2 :p

[IMG]http://img7.imagebanana.com/img/cu11regn/thumb/1_001.jpeg[/IMG]

[full screenshot]("http://www.imagebanana.com/view/cu11regn/1_001.jpeg")

---

