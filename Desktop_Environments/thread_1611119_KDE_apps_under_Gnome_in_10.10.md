---
title: "KDE apps under Gnome in 10.10"
date: 2010-11-01
forum: Desktop Environments
---

### Post by daranz on 2010-11-01
Ever since I upgraded to 10.10, I've been having problems with running KDE apps under my Gnome desktop.

Problem one: Apps start in full screen. With Amarok, I was able to set a shortcut key to un-fullscreen the program, which worked. BasKet does not have an option for setting such a keyboard shortcut, and it's pretty much just stuck in fullscreen. Since I'm running Gnome, I do not have an option for un-fullscreening it via the window list bar/right click window menu.

Second problem: My KDE apps seem to use my GTK theme/color settings, but only partially. This results in a situation where I have black text on gray background, which makes it pretty unusable unless I change the GTK theme to something more black-on-white. Before 10.10, KDE apps used to run with what I assume was some sort of a KDE theme, completely different from my GTK theme. I was OK with that, and if possible, would like to remove whatever Gnome-KDE compatibility thing that is causing this.

---

### Post by nickblame on 2010-11-14
i've noticed that too. its really annoying with black background on labels. is there a workarround?

---

### Post by victorhugo289 on 2011-01-15
Does anyone know why this happens?

---

### Post by jaygo on 2011-02-28
> **victorhugo289 said:**
> Does anyone know why this happens?

It's the same issue as with the OP, and myself: you're getting black text on a black background.

---

### Post by victorhugo289 on 2011-02-28
Hi everyone, I found a solution in this thread: 
[http://ubuntuforums.org/showthread.php?t=1580266](http://ubuntuforums.org/showthread.php?t=1580266)

You have to install this program which is originally intended for KDE:
```
sudo apt-get install systemsettings 

```
"Now you can use systemsettings to configure tooltip bg and font color for KDE applications."

It worked perfectly for me!

---

### Post by cms123 on 2011-08-01
Thanks a lot. worked like a charm. However still not able to change background color. But if I change tooltip font, I could see teh popup clearly. Thanks.

---

