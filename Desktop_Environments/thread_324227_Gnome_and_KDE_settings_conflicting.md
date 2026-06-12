---
title: "Gnome and KDE settings conflicting??"
date: 2006-12-23
forum: Desktop Environments
---

### Post by jpolanco on 2006-12-23
Recently, under Gnome, I installed qt3-qtconfig and kcontrol following [*this guide*]("http://ubuntuforums.org/showthread.php?t=76633"), to change the way my KDE apps, like AmaroK, look like. I was running a Murrina theme, and I'd had no problems before this. But after I installed kcontrol, and switched some settings like the KDE themes (I installed Polymer theme), I started to have some problems with my Gnome theme. First, the colors on the title bar weren't as they were supposed to be, and now, the gnome theme manager crashes every time I start it. Now I changed to a Metacity theme, but it still doesn't look as it should, and I can't customize the theme with the theme manager.

Then I logged in to a failsafe gnome session, and at the startup and then when I opened the theme manager, it appeared this:

> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

I hope I can get some help about this. Thanks in advance.

---

### Post by Tiede on 2006-12-23
I am having a similar problem: I recently uninstalled KDE on my system which was a dual KDE/Gnome ubuntu system. While i still had KDE, I was having the problem mentioned above. My gnome-themes-daemon would crash everytime I log in to gnome. It happened after I checked use my Qt style in GTK apps, since it said it was for better desktop integration. As a workaround to the crashes, I changed the setting in kcontrol from Qt to the default human theme, which at the time, was my GTK theme also. This way, the daemon would stop crashing when in gnome. I since uninstalled KDE, and I thought those problems would have left me, but  I was dead wrong... Now, the gnome-settings-daemon does not crash anymore, but it does not change properly neither. The only theme that seems to completely change is the Industrial theme. In all others, the scrollbar, the buttons, the 'selected' color, and the focus - to cite only those- do not change colors. Why is this happening? I tried uninstalling everything related to KDE in Synaptics, but it does not seems to affect it. dpkg-reconfigure did not seem to help neither. I finally went in Gconf, did a search for KDE and QT, and both turned up with empty results... I am running out of ideas, any suggestions anyone.

P.S: Is this me, or this sounds like it's bug-worthy?

---

### Post by Tiede on 2006-12-24
I found how to fix the issue I was having. Turns out KDE left some config files in my /home folder. I just removed the files .kderc,.gtk_qt_engine_rc and .gtkrc-2.0 and I was good to go! Oooh, how good it felt to see the old modified scrollbars again!!! :)
Hope this helps you with your problem too.

---

### Post by jpolanco on 2006-12-24
Almost everything is working good now. I deleted 2 folders in my home directory: .qt and .kde, and that seems to fix the problem. My only problem now is that my windows titlebars are blue (like in the Tango theme), when they're supposed to be green, but it still looks good though :)  I'll try reinstalling the murrina engine or something like that.

Anyway, the big problem was fixed, thanks a lot ;)

---

### Post by jpolanco on 2006-12-24
Actually now that I also deleted the 3 files you named, my titlebars look like they should, hehe :D

---

### Post by Tiede on 2006-12-27
Hmmm... Great then! Nice to know this worked out for you. I think the developper may have omitted to delete these files on package removal. Should I file that on launchpad (being that it is already resolved and all)?
--Oh, By the way, marc the thread as [SOLVED], so if someone else is having the same problem, they can get the solution from it. ;)

---

### Post by jpolanco on 2006-12-27
> **Tiede said:**
> 
--Oh, By the way, marc the thread as [SOLVED], so if someone else is having the same problem, they can get the solution from it. ;)

Sorry, I'm quite new to the forums...How can I do that? :-?

---

### Post by Tiede on 2006-12-28
just edit the first post, and put [SOLVED] in front of the title

---

