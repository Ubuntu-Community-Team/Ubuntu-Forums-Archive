---
title: "how could I remove KDE at all?"
date: 2005-04-08
forum: Desktop Environments
---

### Post by T31 on 2005-04-08
Hi guys, Im short of space in my hdd, how could I remove completely kde from my box?

I had warty and then moved to hoary by the changing of sources.list file

Thanks in advance

(dont be angry with me KDE lovers) xD

---

### Post by kiddo on 2005-04-08
sudo apt-get remove kde-base

And you could do it by synaptic, would be quite easier: just spot everything that begins with a K :) besides, synaptic allows for "complete removal".

Also, don't forget to do a
sudo apt-get clean

To remove temp packages from time to time. That's what's maybe filling your diskspace.

---

### Post by bored2k on 2005-04-08
This guide might come in handy for removing it:
[http://ubuntuforums.org/showthread.php?t=24403&highlight=debfoster](http://ubuntuforums.org/showthread.php?t=24403&highlight=debfoster)

Beware: not for the faint of heart/.

---

### Post by jdong on 2005-04-08
As others have mentioned, the easiest way to remove KDE is to remove something deep at heart, that KDE apps all depend on. Your best bet is to remove "kdelibs".

---

### Post by az on 2005-04-08
kdelibs4 and arts, I think.

---

### Post by T31 on 2005-04-08
Hey guys! thanks a lot :)))

easy and clean! :)

---

### Post by momo66 on 2005-05-21
Worked for me.  Now I just cleaned off about 80% of the apps off my menus.

Back to some simplicity.

---

