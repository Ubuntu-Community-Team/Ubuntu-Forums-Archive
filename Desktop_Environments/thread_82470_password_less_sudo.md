---
title: "password less sudo"
date: 2005-10-26
forum: Desktop Environments
---

### Post by mariuss on 2005-10-26
I used to have password less sudo configured in Hoary, but after upgrading to Breezy this stopped working. The settings are the same, I checked:
System / Help / Ubuntu 5.10 Starter Guide / Users Administration / 10.

Any clues why this is not working anymore?

---

### Post by aysiu on 2005-10-26
[QUOTE=mariuss]
Any clues why this is not working anymore?[/QUOTE] Maybe because, from a security standpoint, it's a bad idea?

---

### Post by mariuss on 2005-10-26
[QUOTE=aysiu]Maybe because, from a security standpoint, it's a bad idea?[/QUOTE]

Thanks, I know about the risks.

Something got broken during the upgrade and I am trying to solve that.

Marius

---

### Post by aysiu on 2005-10-26
[QUOTE=mariuss]Thanks, I know about the risks.

Something got broken during the upgrade and I am trying to solve that.

Marius[/QUOTE] I wasn't trying to warn you about the risks (though, I'm glad you know what they are), but I'm speculating that maybe they somehow disabled that because of the risks. I don't know.

---

### Post by mariuss on 2005-10-26
Well, the Ubuntu guide tells you how to do it, so it should be possible. Also, I have another machine where it works (I enabled this only after upgrading to Breezy). It is possible for sure.

---

### Post by mariuss on 2005-10-26
One more thing.

Plain **sudo** on the command line works as expected, the one not working as expected is **gksudo** (aka **gnome-sudo**).

---

