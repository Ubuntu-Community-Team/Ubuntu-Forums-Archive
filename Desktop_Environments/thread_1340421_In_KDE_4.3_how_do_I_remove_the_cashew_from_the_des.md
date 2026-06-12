---
title: "In KDE 4.3 how do I remove the cashew from the desktop?"
date: 2009-11-28
forum: Desktop Environments
---

### Post by lightningfox on 2009-11-28
Hello

I am using Kubuntu 9.10 (KDE 4.3).

How do I remove the cashew from the desktop?

---

### Post by Zorael on 2009-11-28
You need to install a special widget for this that removes it. It's not in the official repos.

The kde-look.org entries for the one that removes it completely is [here](http://kde-look.org/content/show.php/I+HATE+the+Cashew?content=91009), and then there's an alternative one that allows you to set the cashew's transparency [here](http://kde-look.org/content/show.php/Stealth+Cashew?content=108460).

If you don't feel like compiling it yourself you could grab it from Sam Rog's PPA ([ppa:samrog131/ppa](https://launchpad.net/~samrog131/+archive/ppa)), package name **plasma-widget-cashew-off**. That PPA has a lot of other nice nifties, like the Smooth Tasks task manager replacement (**plasma-widget-smooth-tasks**), and the vertical one (**plasma-widget-task-vertical**), but obviously it's not an official software source, so no guarantees.

---

### Post by Mark76 on 2010-05-15
Is there a new way to do this? All I get when I try to cmake the widget is error after error after error and I can't see a way of not getting errors :mad:

---

### Post by Zorael on 2010-05-15
Sam Rog's ppa has a version for lucid as well as one for Karmic. It still works; I just tried it now in lucid and 4.4.3.
```
$ sudo add-apt-repository ppa:samrog131/ppa
$ sudo aptitude update
$ sudo aptitude install plasma-widget-cashew-off
```

If you really want to build it yourself, you could try downloading the source of that package, and see if he's using any patches to get it to build.

---

