---
title: "ksudoku is confusing synaptic"
date: 2005-12-13
forum: Gaming &amp; Leisure
---

### Post by JackDog on 2005-12-13
So ksudoku is not distributed with Ubuntu yet... 

I installed it via a debian package however now everytime Synaptic starts up it complains that I have a broken package. Is there a better ubuntu package for ksudoku or is there a way to tell synaptic to ignore it?

---

### Post by teaker1s on 2005-12-13
try fix broken packages under edit in synaptic, I've a gnome/kde system and had no problems so maybe the missing kde package will stop it complaining

---

### Post by JackDog on 2005-12-15
The fix command simply marks it to be removed, which I dont want to do. It works with no issues so I would prefer to not remove it. Isnt there some way to tell synaptic to ignore it so I can install updates and other software?

---

### Post by Chris Tucker on 2005-12-16
its not synaptic thats complaining.. its your apt subsystem, somehow ksudoku is conflicting with another package.

---

### Post by JackDog on 2005-12-16
[QUOTE=Chris Tucker]its not synaptic thats complaining.. its your apt subsystem, somehow ksudoku is conflicting with another package.[/QUOTE]
Well that is more accurate. But ksudoku did not need to install any dependencies, its just missing some. So I just need to tell apt to ignore it permanently.  What can I do to accomplish this or is there a more suitable ubuntu ksudoku deb package somewhere?

---

### Post by mazelado on 2006-01-01
I had trouble getting KSudoku installed too. Then I found this:

[http://www.czessi.net/breezy.php?i18n=de](http://www.czessi.net/breezy.php?i18n=de)

KSudoku and many other packages not in the Ubuntu repositories are here. If you follow the instructions to add this site to your repositories, you can get newer versions though some are a little too new (read: don't work quite right).

---

