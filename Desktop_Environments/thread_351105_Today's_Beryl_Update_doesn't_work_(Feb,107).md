---
title: "Today's Beryl Update doesn't work (Feb,1/07)"
date: 2007-02-01
forum: Desktop Environments
---

### Post by rsambuca on 2007-02-01
Just tried updating today from the notification icon as there were a bunch of new beryl updates.  One file couldn't load and now my beryl isn't working.  Anyone else?

Edit:  the update that gives an error is "beryl-plugins".  It gives the following error:  E: /var/cache/apt/archives/beryl-plugins_0.1.9999.1~0beryl1_i386.deb: trying to overwrite `/usr/lib/beryl/libimgjpeg.so', which is also in package beryl-plugins-extra

---

### Post by jdtate101 on 2007-02-01
Just remove the packages labeled "extra" prior to doing the upgrade. It seems as if these extra plug ins have now been merged into the main packages.

---

### Post by LostShootingStar on 2007-02-01
The problem is all over the board today...i was lucky enough to have everything go smoothly. Its probably just a placebo effect, but Beryl actually seems a bit more stable after the upgrade

---

### Post by Ryba on 2007-02-01
I don't know. Seems faster, smoother, more stable and still locks up most all of my opengl games when using beryl as the window manager.

Overall I'd say it is a nice improvement over the release a few weeks back. I just wish I could play games like Neverwinter without switching to metacity before doing so.

---

### Post by aidanr on 2007-02-01
i had the same error yesterday or the day before, it was just a matter of removing beryl-plugins-extras, reinstalling bery-plugins and then installing beryl-plugins-extras again

Ryba, do a "killall beryl" before running your games and then after exiting the game right click on the beryl icon and reload window manager, or create a script that automates that, it'd look something like

#!/bin/bash
killall beryl &&
cd /path/to/game/folder
./game &&
beryl &

---

### Post by Boule on 2007-02-01
I haven't try the update yet, will do so when I get home...
Do u guys alos have problems watching videos ? They lag in full screen when beryl is running, I have to switch to metacity...

---

### Post by ComplexNumber on 2007-02-01
> **Boule said:**
> I haven't try the update yet, will do so when I get home...
 Do u guys alos have problems watching videos ? They lag in full screen when beryl is running, I have to switch to metacity...
 thats because beryl uses much more resources than metacity (ie its heavier on the CPU and GPU).



------------------------

nope. i installed the updates about 2 or 3 hours ago and beryl works fine for me. i don't run beryl by default, but i tested it to see whats new. everything works fine. i did get that error, though....but it hasn't affected anything.

---

### Post by xpod on 2007-02-01
Thats 2 different pcs i`ve updated beryl on now and although i had all kinds of issues on the earlier machine today this ones been reasonably ok.Only prob so far is the annotate plugin not working it seems.

I had decided to wait a few days to update this one but itchy fingers got the better of me.:D 
I run a different nvidia driver on the 2 machines so i`m wondering if mabey changing the others driver might fix it`s issues?

I have to say though, I`ve also found enlightenment and thats also a very nice bit of kit.
Theres just sooo much to choose from and i`m like a big kid in a sweet shop.:biggrin:

---

### Post by Malac on 2007-02-01
I just ran the update twice and that seemed to sort out the error.
All works fine now.
[ATTACH]24333[/ATTACH]

---

