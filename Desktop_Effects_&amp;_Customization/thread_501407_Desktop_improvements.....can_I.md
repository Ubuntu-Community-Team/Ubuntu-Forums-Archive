---
title: "Desktop improvements.....can I ?"
date: 2007-07-15
forum: Desktop Effects &amp; Customization
---

### Post by derby007 on 2007-07-15
Q. Can I install Beryl or Compiz (or is it CompizFusion now) on my PC, I have an intel graphics 965G chip with i810 driver ?

---

### Post by walkerk on 2007-07-15
> **derby007 said:**
> Q. Can I install Beryl or Compiz (or is it CompizFusion now) on my PC, I have an intel graphics 965G chip with i810 driver ?

absolutely.. though i would suggest install the intel-video driver:
```
sudo apt-get install xserver-xorg-video-intel
```

i use compizfusion w/ intel 945GM with the intel driver and it works great!

---

### Post by derby007 on 2007-07-15
Cheers, i'll give it a go, is there much diff with the i810 & the intel driver? ie. i'm running both Edgy & Fiesty versions. Also have you tried AWN < avant-window-navigator > ?

---

### Post by derby007 on 2007-07-17
Just to say after I used the 'xserver-xorg-video-intel' driver, i was also able to get more screen resolutions working, ie. i can now use the 1152x864 option.

---

### Post by walkerk on 2007-07-18
with the intel driver it allows xorg to control your screen resolution..

you said you're having problems with compiz fusion?

first... through synaptics remove everything compiz related (search compiz).. now beryl related (search beryl)..

follow this guide by [Vorian]("http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion").

now if you want to theme compiz fusion (which i am sure you do) install emerald:
```
sudo apt-get install emerald emerald-themes libemeraldengine0
```

let me know..

---

### Post by walkerk on 2007-07-18
> **derby007 said:**
> Cheers, i'll give it a go, is there much diff with the i810 & the intel driver? ie. i'm running both Edgy & Fiesty versions. Also have you tried AWN < avant-window-navigator > ?

sure.. im using the latest svn.. [check out this website for the newest svn .deb]("http://syzygy42.tuxfamily.org/dists/feisty/avant-window-navigator/").. should be 227. do this only after you have compiz fusion working..

---

