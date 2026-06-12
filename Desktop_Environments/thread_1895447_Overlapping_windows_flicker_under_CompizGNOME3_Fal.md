---
title: "Overlapping windows flicker under Compiz/GNOME3 Fallback"
date: 2011-12-14
forum: Desktop Environments
---

### Post by Viman on 2011-12-14
Hello all, I've got an inoffensive, yet quite annoying bug that has been running under **Oneiric/GNOME3 Fallback/Compiz**. As I am not good with words even in my mother language, here is a 45sec demonstration of said bug:

[http://www.youtube.com/watch?v=wSDDagDfnFs](http://www.youtube.com/watch?v=wSDDagDfnFs)

**In summary:** clicking overlapping windows cause them to flicker as they are focused.

I've looked up this problem but was **unable to find anything close to it**, except for a cube effect flicker in this thread (unsolved):

[http://ubuntuforums.org/showthread.php?t=1860889](http://ubuntuforums.org/showthread.php?t=1860889)

Anyone else experienced this? Can you point me to a thread or help me fix this? Thanks in advance!

Additional information

```
lspci | grep -i graphics
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

xorg-server 1.10.4 

Compiz 0.9.6
```

Peace

---

### Post by relik1989 on 2011-12-21
I am having the same issue except in Gnome Shell. All overlapping windows act exactly how your video showed, and the Shell "Activities" panel and all notifications do it as well.

My graphics hardware is different than yours so at least I know its not my drivers again. But any help would be much appreciated, apparently this is a general Gnome issue, as it apparently affects Fallback and Shell

My graphics hardware is a AMD Radeon HD 6850 with the latest catalyst drivers version 11.12.

---

### Post by arisp on 2011-12-22
I had a similar problem when the focus animation was set to "fade". Once I set it through ccsm -> animations -> focus to none this kind of flickering stopped.

---

### Post by Viman on 2011-12-22
Like arisp said, it goes away once you disable the "fade" animation. That was the fix for me anyway.

I think this is a GNOME glitch in general, I had a LXDE+Compiz setup on my other machine and it never did it.

---

### Post by cbanakis on 2012-09-05
The other bug at [http://ubuntuforums.org/showthread.php?t=1860889](http://ubuntuforums.org/showthread.php?t=1860889)  may be related.

See if the same fix works for this...

sudo apt-get install synaptic

sudo apt-add-repository ppa:vanvugt/compiz-preproposed

sudo apt-get update

sudo apt-get install compiz=1:0.9.7.8-0ubuntu1vvpreproposed2  compiz-core=1:0.9.7.8-0ubuntu1vvpreproposed2  compiz-gnome=1:0.9.7.8-0ubuntu1vvpreproposed2  compiz-plugins=1:0.9.7.8-0ubuntu1vvpreproposed2  compiz-plugins=1:0.9.7.8-0ubuntu1vvpreproposed2  compiz-plugins-default=1:0.9.7.8-0ubuntu1vvpreproposed2  libdecoration0=1:0.9.7.8-0ubuntu1vvpreproposed2

(it will downgrade packages, allow it to continue)

Start synaptic

in "Search filter": put "compiz"

select every package that has a (!) next to it.

Select Package -> lock version

(they become red)

exit synaptic

Reboot or Restart X/Compiz.

---

