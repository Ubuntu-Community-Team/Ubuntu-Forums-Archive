---
title: "Indicator Applet Appmenu Does not work with many apps"
date: 2010-10-10
forum: Desktop Environments
---

### Post by ciuci on 2010-10-10
i installed indicator applet appmenu (the new maverick netbook globalmenu, but i installed it in the desktop version) in order to have a global menu, but unfortunately it does not work with firefox, netbeans, mono-develop and openoffice from the apps i tested so far. unlinke gnome2-global-menu which works only with gtk apps, this does work with qt apps (i tested it with qt creator) but in anki, the menu is displayed but inactive so you can't actually use it.

are there any plans to fix this issue? netbeans and oppen-office are java apps and monodevelop is a mono app. firefox probably uses some custom widget for the menu....


later edit: it also does not work with shotwell
later edit2: it does surprisingly work with tomboy which is mono as far as i know

---

### Post by ciuci on 2010-10-11
anyone anything?

---

### Post by vek on 2010-10-11
I'm pretty sure that many of those programs will need to have their code changed to support this.

Especially if their UIs are not Gnome/Qt.  You'll probably find that shotwell and tomboy were specifically customized to work with it.  Tomboy was also reworked to function correctly as an indicator applet, so I'm not surprised... firefox on the other hand tends to be slow (ie, never ever) to change to accommodate one particular OS.

---

### Post by ciuci on 2010-10-11
couldn't ubuntu patch mono and java so they'd work for all the apps, instead of patching individual apps like tomboy and shotwell?
couldn't they also patch firefox themselves to add the functionality, instead of waiting for the firefox devs to play along?

---

### Post by Ve0 on 2010-10-13
+1

---

### Post by AndyM3 on 2010-10-13
It's not that easy, depends on each app's toolkit. Only GTK and Qt support detaching menus.
Firefox and Thunderbird use XULRunner, which doesn't support detaching menus.
MonoDevelop probably uses some other toolkit, but Mono apps can be written to use GTK.
Java apps use Swing or something like that, which, as XULRunner, doesn't support detaching menus.

As a side note, I also installed the appmenu indicator, but gave up on it because I use "sloppy focus" and I can't access the menu sometimes. Also, it has weird graphical glitches.

---

### Post by miesogeno on 2010-10-15
does anyone else notice the appmenu memory leak?

or is it just my fresh install of maverick?

---

### Post by directhex on 2010-10-15
> **AndyM3 said:**
> It's not that easy, depends on each app's toolkit. Only GTK and Qt support detaching menus.
Firefox and Thunderbird use XULRunner, which doesn't support detaching menus.
MonoDevelop probably uses some other toolkit, but Mono apps can be written to use GTK.
Java apps use Swing or something like that, which, as XULRunner, doesn't support detaching menus.

As a side note, I also installed the appmenu indicator, but gave up on it because I use "sloppy focus" and I can't access the menu sometimes. Also, it has weird graphical glitches.

MD uses GTK#, but has a lot of custom widgets on top. It would need to be altered.

---

### Post by jctots on 2010-10-15
lyx also do not work with indicator applet appmenu. it doesnt show anything at all

---

### Post by Ve0 on 2010-10-19
> **AndyM3 said:**
> It's not that easy, depends on each app's toolkit. Only GTK and Qt support detaching menus.
Firefox and Thunderbird use XULRunner, which doesn't support detaching menus.
MonoDevelop probably uses some other toolkit, but Mono apps can be written to use GTK.
Java apps use Swing or something like that, which, as XULRunner, doesn't support detaching menus.

As a side note, I also installed the appmenu indicator, but gave up on it because I use "sloppy focus" and I can't access the menu sometimes. Also, it has weird graphical glitches.

But the Gnome Global Menu work with Shotwell in Ubuntu 10.04. Why AppMenu don't work with Shotwell?

And, realy lacking active App name.... (((

Ps: Sorry for my bad english.

---

### Post by tawie on 2010-10-22
> **miesogeno said:**
> does anyone else notice the appmenu memory leak?

or is it just my fresh install of maverick?

yes, and it is still a problem now, ubuntu update to today.

---

### Post by miesogeno on 2010-10-22
> **tawie said:**
> yes, and it is still a problem now, ubuntu update to today.

if you are interested on a panel menu, i am using Globalmenu like i did on lucid.
the PPA didn't work for maverick, so i installed through .deb packages and its working great, no memory leaks.

---

### Post by LostinSpacetime on 2010-10-24
> **miesogeno said:**
> does anyone else notice the appmenu memory leak?

or is it just my fresh install of maverick?

same here on maverick. I caught it once using over 500MB after hours of editing and gimping.

---

### Post by madjr on 2010-11-08
well **vlc** acts a bit weird sometimes with the appmenu thingy when you maximize the window

---

### Post by t.rei on 2010-11-10
> **LostinSpacetime said:**
> same here on maverick. I caught it once using over 500MB after hours of editing and gimping.

I just caught it with around 550MB after a day of work and two suspend-resume cycles.

I'll keep an eye on this. Anyone know of an open bugreport?

---

### Post by satis on 2010-11-12
> **t.rei said:**
> I just caught it with around 550MB after a day of work and two suspend-resume cycles.

I'll keep an eye on this. Anyone know of an open bugreport?

Same here, about 500MiB after uptime of about 4 days and about 5 suspend-resume cycles. I killed it, after which it asked to reload and now it's using <5MiB again. I also have no idea which apps could be causing it, I use a large variety of applications. Great tool otherwise, I really like the cleaner windows :).

I've found this bug report by the way: [https://bugs.launchpad.net/indicator-applet/+bug/634035](https://bugs.launchpad.net/indicator-applet/+bug/634035)

---

### Post by Burfee on 2010-11-14
same problem for me, but in the same cycle. I happened to use many applications while working on a project and closing and reopening some of them caused the applets memory usage to go up. i had to kill it regularly because it was going too high

the more applications you open, the higher it goes and it doesn't come down when you close them

---

