---
title: "Can't install a game on Ubuntu"
date: 2010-12-23
forum: Gaming &amp; Leisure
---

### Post by windows4life on 2010-12-23
I tried adding a game that is already on Ubuntu called 'Beneath a steel sky' but for some reason it doesn't work. 

I did it the simple way by going onto the 'add/remove' link under applications. But I get the following error:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
I didn't use to have this problem but now it seems I can't add any game.

Btw, I'm using Ubuntu 9.04

Any help is appreciated thanks

---

### Post by slooow on 2010-12-23
Well, do what it says. Run

```
sudo dpkg --configure -a
```
in a terminal.

---

### Post by windows4life on 2010-12-23
Sorry, I forgot the 'I'm a n00b' part.

How do I open a terminal?

---

### Post by trinitydan on 2010-12-23
Go to applications>accessories>terminal> on the menu on the top left of your screen.

---

### Post by mastablasta on 2010-12-24
you will need to use DOSBox to run it i believe. Dos box is also in the repositories.
 
i also suggest a graphical front end for it to make it easier to run (if you are not versed in DOS commands). for example this one: [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)

---

### Post by ronnielsen1 on 2010-12-24
> i also suggest a graphical front end for it to make it easier to run (if  you are not versed in DOS commands). for example this one: [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)There's also right click, open with dosbox - super quick. It's also pretty easy to set it up in the menu to automatically open

---

### Post by Bölvaður on 2010-12-24
> **mastablasta said:**
> you will need to use DOSBox to run it i believe. Dos box is also in the repositories.

no I think it is scummvm he will need.
it is installable from add/remove, could actually be that thing he was trying to install and then he'd need to install the game through scumm.

I got sam and max so I might try this also sometime.

---

### Post by Nytram on 2010-12-24
Im pretty sure it's a Linux native version and will run on its own.

EDIT: my mistake it does indeed install scummvm as a dependency, although it runs behind the scenes.

---

