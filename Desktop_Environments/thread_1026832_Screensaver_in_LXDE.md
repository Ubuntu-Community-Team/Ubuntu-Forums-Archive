---
title: "Screensaver in LXDE"
date: 2008-12-31
forum: Desktop Environments
---

### Post by jis on 2008-12-31
How can you replace xscreensaver by gnome-screensaver in LXDE? (Xscreensaver does not lock screen when you e.g. suspend.) Even if I kill xscreensaver and run gnome-screensaver, the former is there after next login. How do you add a key-binding to lock screen in LXDE? (Ctrl-Alt-Delete works in Xfce.)

---

### Post by jis on 2009-01-01
xscreensaver is a dependency of lxde package. Thus I can't remove xscreensaver unless I want to remove whole LXDE. I don't understand why they are so tightly bind. I prefer gnome-screensaver for its power management features.

---

### Post by bhy on 2010-05-25
a similar problem here, xscreensaver is eating my CPU and I'd like to replace it by a blank screen, however there seems to be no way to disable it in LXDE.  btw, first I thought you wrote "how can they [the package managers] be so tightly blind [to the user's needs]" :)

---

### Post by amjjawad on 2011-03-09
[https://wiki.archlinux.org/index.php/LXDE#Gnome-screensaver_with_LXDE](https://wiki.archlinux.org/index.php/LXDE#Gnome-screensaver_with_LXDE)

Yes, I know this is an old thread but I'm trying to help those who will come across this one :)

After spending some time on searching, I guess using Xscreensaver which is the default package with Lubuntu is a better approach. Some may not even use a screensaver.

If the above link is the only way to get gnome-screensaver works for LXDE then it's unnecessary step.

---

### Post by Subito Piano on 2011-12-28
Thanks, amjjawad -- being in and out of my office your link was just what i needed!  :)

---

### Post by Subito Piano on 2011-12-28
Hmm - now my taskbar has reverted to my Gnome taskbar.  not bad, but, well, am i in LXDE or Gnome?  :P  How much am i using more resources and defeating the whole point of using LXDE?

EDIT:  A little digging led me [here]("http://urukrama.wordpress.com/openbox-guide/#shutdown") -- scroll down a little to see how to configure xscreensaver and have it lock, all automatically, when you add "xscreensaver" to the autostart file.

---

### Post by oldos2er on 2011-12-29
Closed, necromancy.

---

