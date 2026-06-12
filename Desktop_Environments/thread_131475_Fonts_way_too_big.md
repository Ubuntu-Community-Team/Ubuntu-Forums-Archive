---
title: "Fonts way too big"
date: 2006-02-16
forum: Desktop Environments
---

### Post by pixelnate on 2006-02-16
When I use Jahshaka or Scribus, the application fonts are way too big. In fact, they are so large that some terms are cut off by their button bounds. I have looked for a solution on this forum, but I must be using the wrong search terms, because I just cannot find an answer.

How can I make these fonts smaller? The font menu in Gnome does nothing to solve this. Thanks in advance.:-k

---

### Post by arctic on 2006-02-16
Scribus is a KDE based application. If you want to change the fonts, I suggest you install the kcontrol center, from where you can change fonts etc for qt-based KDE apps.

---

### Post by pixelnate on 2006-02-16
I can install that in Gnome?

---

### Post by kaamos on 2006-02-16
Yes you can. It will pull the kde base libraries with it, and is also overkill in the terms of options to configure. I suggest you skip that and use qtconfig instead.

To install
```
sudo apt-get install qt3-qtconfig
```
and to run
```
qtconfig
```

You might also wish to check out this: [http://ubuntuforums.org/showthread.php?t=76633](http://ubuntuforums.org/showthread.php?t=76633)

---

### Post by arctic on 2006-02-16
You install that with synaptic or apt-get and can launch it in Gnome. Sure. If it ain't in your menu, just launch kcontrol from a terminal. Every KDE app can be launched in Gnome, just like every Gnome app can be run in KDE.

---

### Post by nalmeth on 2006-02-16
> Every KDE app can be launched in Gnome, just like every Gnome app can be run in KDE.

Sometimes not so seamlessly. I get knotify starting but not launching with a lot of apps in gnome, when doing simple things with the app

---

### Post by pixelnate on 2006-02-16
> You might also wish to check out this: [http://ubuntuforums.org/showthread.php?t=76633](http://ubuntuforums.org/showthread.php?t=76633)
Is it really necessary to do all of this? I would rather not be tied to a theme. Maybe I am misunderstanding it, but this originally looked to me like I would have to install kde. I would rather not do that either.

---

### Post by kaamos on 2006-02-16
No, you can just install qtconfig and set the font in that. It does not depend on kde.

---

### Post by pixelnate on 2006-02-16
Thanks. I'll play with this when I get home.

---

