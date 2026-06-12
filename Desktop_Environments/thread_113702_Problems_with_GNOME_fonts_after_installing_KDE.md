---
title: "Problems with GNOME fonts after installing KDE"
date: 2006-01-06
forum: Desktop Environments
---

### Post by Iandefor on 2006-01-06
Hi all. I've been asking for a lot of help lately, but it's because I'm encountering a lot of problems I have no experience with. Here's another.
Just for laughs, I installed Kubuntu-desktop and ran it. Upon going back to GNOME, I found my panels and my application text fonts had been changed to the KDE default (whatever the heck they call it). I opened up the font manager dialog and changed it to Sans 9, but it did nothing. I uninstalled all the packages in Kubuntu-desktop and tried changing the fonts again. Again, no joy. Currently, I can get the application text to change properly for some programs, but not others. For instance, OO.O, Firefox, and the GIMP all use Sans 9 (the desired front for application text), but GAIM and gnome-panel and many of the configuration dialogs still use the KDE font. How can I get these applications to begin behaving properly?

---

### Post by potrick on 2006-01-07
whoa, that just happened to me today. After searching and finding nothing, I asked for help and recieved nothing. But then through the power of google I stumbled upon this...

[http://ubuntuforums.org/showthread.php?t=58787&highlight=kubuntu+gnome+font](http://ubuntuforums.org/showthread.php?t=58787&highlight=kubuntu+gnome+font)

In summary, *~/.gtkrc-2.0* is a file that you will want to delete before restarting.

---

### Post by Iandefor on 2006-01-07
Most excellent! Even after aptitude-purging all the KDE packages, it left a bunch of configuration files around. Thank you so much!

By the way: where did you get your avatar? I love Gir!

---

### Post by potrick on 2006-01-07
No problem. And I can't remember where I got the picture, a friend of mine and myself just went on a Zim picture downloading binge one day. When the haze settled, I had that.

---

### Post by Iandefor on 2006-01-07
Damn! Well, I'll have to go looking for it, then, I guess. Thanks anyways!

---

