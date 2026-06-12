---
title: "Change resolution of a program?"
date: 2020-06-21
forum: Desktop Environments
---

### Post by msaud on 2020-06-21
[COLOR=#242729][FONT=Arial]I recently installed Zoom and it is opening up really weird - everything is like super zoomed-in. Is there a way to change the "resolution" of a program? I was wondering if there was a configuration file that zoom was getting its settings from and maybe that file had the resolution incorrect.
[/FONT][/COLOR][IMG]https://i.stack.imgur.com/jLDKS.png[/IMG]

[COLOR=#242729][FONT=Arial]By the way, I have already tried[/FONT][/COLOR]*sudo apt purge ... *[COLOR=#242729][FONT=Arial]to uninstall it and then manually removed the [/FONT][/COLOR]*~/.zoom*[COLOR=#242729][FONT=Arial]directory, too, but that did not work.
Also, [/FONT][/COLOR][COLOR=#242729][FONT=Arial]I just installed Anaconda and opened up Anaconda Navigator, and this is how it's being displayed:

[/FONT][/COLOR][IMG]https://i.stack.imgur.com/cZXST.png[/IMG][COLOR=#242729][FONT=Arial]

Here are my system settings:
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]Screen Resolution: 1920 x 1080
OS: Ubuntu 20.04 LTS
GNOME Version: 3.36.2
Windowing System: X11

Thank you, and I really hope to solve this before the weekend ends[/FONT][/COLOR]

---

### Post by TheFu on 2020-06-21
I am clueless about this stuff, but  [https://www.linuxuprising.com/2019/04/how-to-enable-hidpi-fractional-scaling.html](https://www.linuxuprising.com/2019/04/how-to-enable-hidpi-fractional-scaling.html)  says the entire OS display can be scaled on 20.04. This is usually meant to be used by people with high resolution displays - 4k, 8k and higher.

For programs that are just wrapped around a web browser, you can try the common <cntl>---- and <cntl>+++ to decrease and increase fonts.  Don't forget the <shift> to access the '+'.

---

### Post by CatKiller on 2020-06-21
Gnome's DPI scaling is a work in progress, and its ability to play nicely with others is not great as a matter of policy. You may find that  it helps to use ```
QT_SCALE_FACTOR=1 zoom
```

---

### Post by anarchy-x on 2020-06-29
Did these solutions work?  -- I've been staying away from Zoom and sticking with the trusty Jitsi, XMPP, and Matrix for this stuff. :p Now,  I want to use it even less. lol
If any of the solutions worked, please mark the thread Solved.

---

