---
title: "Autohide delay and other GNOME prefs"
date: 2004-11-04
forum: Desktop Environments
---

### Post by CapKrugers on 2004-11-04
In trying to make my Ubuntu installation more pleasant (since I am so used to my Windows environment configuration), I was wondering how to change the autohide delay of panels in GNOME. Also, I was wondering how to access something like the "Global Panel Preferences" in GNOME talked about here: [http://www.linuxselfhelp.com/gnome/users-guide/globalpanelprefs.html](http://www.linuxselfhelp.com/gnome/users-guide/globalpanelprefs.html)

Ubuntu's menus are pretty good, but I really like to edit the tiny details. 

In addition, is there any way to change Nautilus to use a single window and use a Folders toolbar like in Windows explorer? I am trying to make GNOME as close to my Windows XP configuration as possible (haha, yes, I know, that may make you unhappy) but it's only to increase my productivity by allowing myself to use an environment in a way I'm already used to. Are there any Windows-like themes for GNOME? Can I get MS Sans Serif as my default font (Verdana is okay for now)? Is it possible for me to use a different window manager?

If most of this is already in an FAQ then I'm sorry. I know that might be too many questions for one thread. I'm pretty much a Linux n00b but I'm not average Joe GUI user, and I'm really excited to be trying out Linux finally.;

Any help would be greatly appreciated!

---

### Post by oddabe19 on 2004-11-05
right click the panel you want to hide, goto properties, then select auto hide, etc...

---

### Post by fng on 2004-11-05
Use of a single window in Nautilus :
Computer -> Desktop preferences -> File Management -> Behaviour tab
Mark "Always open in browser windows"
Save

That should do the trick :)

---

### Post by fng on 2004-11-05
Why do you need a windows theme if there are a lot better themes out there? :)

Themes can be found here:
[http://art.gnome.org](http://art.gnome.org)
[http://www.gnome-look.org](http://www.gnome-look.org)
[http://www.themedepot.org](http://www.themedepot.org)

---

### Post by CapKrugers on 2004-11-05
[QUOTE=oddabe19]right click the panel you want to hide, goto properties, then select auto hide, etc...[/QUOTE]

As far as I could see, there was no option to configure the time delay of auto-hide (I would like the panel to instantly unhide when I hover over where it should be). Was there a button I missed?

Also, in response to fng's post:
I appreciate the links. However, I just like a Windows-like theme. I'm used to it and there are no extra annoying frills or distracting colors. I'm entitled to my opinion, even if it's wrong  :mrgreen:

---

### Post by taurendil on 2005-01-30
I found the settings you were wanting for autohide, I was looking for the hidden size.  If you go to Applications->System Tools-> Configuration Editor

then under apps->panel->global 
you'll find what you want 

Hope that helps!

Namarie
-Taurendil

---

### Post by szr4321 on 2005-09-14
Thanks a lot, taurendil!
That was exactly what I was looking for.

The globals settings didn't work for me though because they were overwritten for my bottom panel, so I had to change them there (/apps/panel/toplevels/bottom_panel_screen0/).

---

### Post by Centx on 2006-10-02
thanks, was looking for this. gconf-editor rocks !

---

