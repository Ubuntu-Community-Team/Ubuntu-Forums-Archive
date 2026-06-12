---
title: "Minecraft On 11.10"
date: 2011-12-29
forum: Gaming &amp; Leisure
---

### Post by Kodeine on 2011-12-29
Salutations!

So I got into minecraft once. Played it for ages, went out of it and now I'm getting back into it once again. But I seem to be having some trouble. I keep getting an isosceles triangle of black on one side of the minecraft screen. [http://www.fayp.com/vi-nZ3XOk.png](http://www.fayp.com/vi-nZ3XOk.png)

I have the javajdk-6 package installed not the seven one. Is that what I need? I've tried changing all the different options but it did not affect the triangle in any way.

Thanks bye!

---

### Post by a2j on 2011-12-30
do you have the right gpu driver installed? is that gpu powerful enough?

---

### Post by Kodeine on 2011-12-30
> **a2j said:**
> do you have the right gpu driver installed? is that gpu powerful enough?

There is no drivers in use. My computer uses that sandy bridge onboard Intel graphics rather then a PCI video card.

---

### Post by Dlambert on 2011-12-30
Maybe install latest Mesa drivers.

---

### Post by Kodeine on 2011-12-31
> **Dlambert said:**
> Maybe install latest Mesa drivers.

How do you do that? 'Additional drivers' doesn't give any options to install different drivers? It just says 'There are no proprietary drivers in use on this system'.

---

### Post by Perfect Storm on 2011-12-31
> **Kodeine said:**
> How do you do that? 'Additional drivers' doesn't give any options to install different drivers? It just says 'There are no proprietary drivers in use on this system'.

Linux Intel drivers are open source so they are installed by default.

---

### Post by Kodeine on 2011-12-31
Okay so I installed optimine which is a modification that alters minecraft goings on for a better FPS. Before trying the game after installing the mod I turned the fog off and changed some other features to make MC run smoother. Behold the isosceles triangle was gone. Out of curiosity I turned the settings I altered back and after turning the fog back on I unwittingly turned that isosceles triangle back on. So it seems the fog was the culprit?

But just as one problem goes another eventually took it's place. Now there's loads of little black dots on the screen. Some textures are also a tad funny. [http://www.fayp.com/vi-mVUPWl.png](http://www.fayp.com/vi-mVUPWl.png) I recall seeing this same problem in another thread. Anyone know the fix?

---

### Post by Kodeine on 2012-01-04
Only gonna bump once. Anyone have any information regarding this problem? Usually these dots (their not always black, depends on what texture their appearing on) appear after a minute or so when first starting the game. If I close MC and restart it sometimes the dots come on straight away but sometimes they wait for the minute before coming on again.

Someone else has had these problems and seems to think it's the drivers that are at fault.

---

### Post by CrammitTheFrog on 2012-01-07
Are you running a mod?  If so, which one?  Your latest picture doesn't look like plain Minecraft.

---

### Post by Mars11 on 2012-01-08
It does that with mine too, completely vanilla Minecraft. I think it has to do with the Intel Graphics Drivers and I hear that the Linux 3.2 Kernel has some better ones so if anyone knows how to upgrade that would be nice.

---

### Post by Coarch on 2012-02-03
Same, lots of black dots.  Doesn't change with different versions of Minecraft, tried 1.1 - 1.9.  Any ideas?

---

### Post by Mars11 on 2012-02-03
I updated to the 3.0.15 or something kernel and the problem is gone. I think it's just the drivers.

---

### Post by regor210 on 2012-02-03
Coarch

Open up a terminal, like xterm and cut and past or type this in

 $ lspci -vmk | grep -A 8 -B 2 VGA

without the $ and post it

also try this
$ sudo apt-get install mesa-utils
$ glxgears
and post your FPS.

---

