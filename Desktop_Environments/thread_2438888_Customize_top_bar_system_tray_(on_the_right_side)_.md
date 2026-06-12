---
title: "Customize top bar system tray (on the right side) remove menu entries?"
date: 2020-03-19
forum: Desktop Environments
---

### Post by druidicbearclan on 2020-03-19
I recently installed ubuntu 18.04 on my laptop. Lots of things unfortunately needed tweaking and 
I just got over the last hurdle of making my bluetooth headset reconnect normally by installing blueman. (bluetooth manager)
But, now im facing the small annoyance of having 2 different icons to select bluetooth from, one of which is kinda broken anyway,
so I would like to disable that bluetooth menu entry in the system tray that I am no longer using (the default place ). 
I would like to keep bluetooth functionality itself ENABLED, just remove the menu entry for the system tray on the right only.
the other icon which is a separate one in the top bar itself for blueman i would like to keep it. 

Please advise me on how to do such a thing. I found lots of posts for tweaking the dock or adding/removing icons in the top bar..
disabling bluetooth altogether, but that's not what I'm looking for. 

Side question:
Is it also possible to re-arrange the order of the icons in the top panel? I cant find it in tweaks and dragging icons does nothing.
Maybe there is an extension for that?

uname -a :
Linux ouroboros 5.3.0-42-generic #34~18.04.1-Ubuntu SMP Fri Feb 28 13:42:26 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

GNOME version 3.28.2

Running Nordic-darker theme

[ATTACH=CONFIG]285239[/ATTACH]

---

### Post by Frogs Hair on 2020-03-19
Hello and Welcome

It think it would have to be done with an extension. You can look [here]("https://extensions.gnome.org/") , but be sure anything you select is up to date.

Edit: To use the linked page you will need to install the chrome-gnome-shell extension. You don't need chrome to use it.

---

### Post by druidicbearclan on 2020-03-19
Thanks for your fast reply. I'm aware of where and how to install extensions, my question is, which one? I have looked and didn't find anything with the search. plus in the end this is part of a shell theme no? I have edited the .css of my default ubuntu theme also to do some final tweaks but would like to be pointed in a general direction of where to look

Edit: I'm not a complete beginner at linux. I have manjaro at the office and my servers run freeBSD.
I already have a lot of tweaks done on my OS and extensions installed plus just a regular theme from looks-gnome, but I can't find at all how I would be able to change the menu entries in system tray. 
My results on google are not the desired effect.

---

### Post by Frogs Hair on 2020-03-19
I think the task would require some knowledge of gnome shell .css which I can't help with. The developer of your theme may know what to do.
[https://github.com/EliverLara/Nordic](https://github.com/EliverLara/Nordic)

---

### Post by druidicbearclan on 2020-03-20
Every theme I use has the exact same menu structure and icons, its just an overlay for default ubuntu right? so it should either be the ubuntu.css or as you said the gnome-shell.css, or maybe the ShellMenu-01.gir from the parent directory or something?

I don't see why I'm being directed the github of a specific theme developer when this is just the default ubuntu menu with just a different color.
Maybe I need to move my post to another category?

EDIT: I have just confirmed that the default ubuntu shell theme and nordic theme are identical 

Kind regards

---

### Post by Frogs Hair on 2020-03-20
> I don't see why I'm being directed the github of a specific theme  developer when this is just the default ubuntu menu with just a  different color.  You could ask there or wait for a forum member with gnome shell .css experience. Ubuntu developers seldom visit here and don't know about third party theme developers.

---

### Post by druidicbearclan on 2020-03-20
I understand. Thanks for the effort I expected this answer to be more well documented also. I'll try to look into the files myself in the meantime.

---

### Post by Frogs Hair on 2020-03-20
There is some gnome documentation.

[https://wiki.gnome.org/Projects/GnomeShell/Development](https://wiki.gnome.org/Projects/GnomeShell/Development)

---

