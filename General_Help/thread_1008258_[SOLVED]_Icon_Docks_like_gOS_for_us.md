---
title: "[SOLVED] Icon Docks like gOS for us"
date: 2008-12-11
forum: General Help
---

### Post by CrusaderAD on 2008-12-11
I've tried a few icon docks for Ubuntu and few actually work. Simdock works ok, but the background is always messed up (blacked out). Is there anything like the gOS dock? Maybe it's just an incompatibility with my graphics card? Any recommendations?

---

### Post by PocketDog on 2008-12-11
gOS uses the 'Engage Dock'. I've got AWN which works ok I suppose. Or did, till I disabled it...

---

### Post by CrusaderAD on 2008-12-11
I tried AWN but it doesn't work. When I launch it, it brings up a blank window for a split second and then exits. I'm trying to remember what the terminal said... I think it advised me to edit my Compwiz or something like that and enable advanced graphics, which I can't do cause my graphics card is a pos. Anyone know a work around?

---

### Post by PocketDog on 2008-12-11
[This page](http://linuxowns.wordpress.com/2008/05/08/the-best-and-worst-docks-for-ubuntu/) mentions Wbar which doesn't need a compositing manager so should be ok on your machine. I've never used it myself

---

### Post by Hyper Tails on 2008-12-11
I been wanting a dock too that has a gos feel
I had a dock thought But it didn't feel right

---

### Post by CrusaderAD on 2008-12-11
> **PocketDog said:**
> [This page](http://linuxowns.wordpress.com/2008/05/08/the-best-and-worst-docks-for-ubuntu/) mentions Wbar which doesn't need a compositing manager so should be ok on your machine. I've never used it myself

Wbar looks promising... I'll give it a shot. Great article. Thanks!

---

### Post by CrusaderAD on 2008-12-11
Wbar doesn't seem to launch... terminal says this:

Using /usr/share/wbar/dot.wbar config file.
Using a Super Bar.

---

### Post by PocketDog on 2008-12-11
I found this concerning Wbar, [http://www.murga-linux.com/puppy/viewtopic.php?p=127662](http://www.murga-linux.com/puppy/viewtopic.php?p=127662) I'll have a go at getting it to run later

---

### Post by PocketDog on 2008-12-11
Ignore that previous post. From terminal if I run ```
wbar -above-desk
``` then it still says 'using super bar', but it actually appears. Without '-above-desk' it seems to appear only when it wants to.

---

### Post by CrusaderAD on 2008-12-11
Sweet it worked! It's under my bottom panel tho... how do you move it?

---

### Post by PocketDog on 2008-12-11
I don't use a bottom panel so it's not in the way for me. try ```
wbar --help
``` for some command line options. e.g. ```
wbar -above-desk -vbar -pos left
``` which looks ace!  :-D

---

### Post by CrusaderAD on 2008-12-11
> **PocketDog said:**
> I don't use a bottom panel so it's not in the way for me. try ```
wbar --help
``` for some command line options. e.g. ```
wbar -above-desk -vbar -pos left
``` which looks ace!  :-D

Thanks Again!

---

