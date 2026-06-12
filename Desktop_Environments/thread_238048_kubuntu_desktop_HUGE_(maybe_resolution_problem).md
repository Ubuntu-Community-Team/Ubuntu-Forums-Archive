---
title: "kubuntu desktop HUGE (maybe resolution problem)"
date: 2006-08-17
forum: Desktop Environments
---

### Post by abloylas on 2006-08-17
Hi!
I've been using Kubuntu 6.06 since it came out and I've been very happy with it. Then all of a sudden when I booted my machine one fine morning the monitor settings were all messed up. For no apparent reason. I don't think I've done anyting stupid myself.

It's like the desktop cannot fit on the screen anymore. I can get to everything by moving the mouse around, which makes the desktop move around too. Could somebody please help me fix this and maybe explain what has happened and why? I'm sort of a semi-noob when it comes to Linux.

Thanks in advance

abloylas

---

### Post by rejser on 2006-08-17
sounds wierd, have you tried alt+ctrl and +/- which you can change resolution och your xorg-server with?

---

### Post by abloylas on 2006-08-17
> **rejser said:**
> sounds wierd, have you tried alt+ctrl and +/- which you can change resolution och your xorg-server with?

I just tried typing that on the command line and all I get is (arg: -1). Nothing happens. I'm not sure I understand what you mean.

---

### Post by Lunar_Lamp on 2006-08-17
He means that you should try holding down the ctrl and alt keys on your keyboard, and presing the "+" [plus] or "-" [minus] keys to try and change the resolution of your screen.  You should do this not in any particular window. :)

---

### Post by abloylas on 2006-08-17
No cigar. Nothing happens when I do that:(

---

### Post by abloylas on 2006-08-17
Ok. It seems something messed up my xorg.conf. This kind of worries me because I have no idea what did it. I managed to get it fixed by running

sudo dpkg-reconfigure xserver-xorg

I answered a bunch of questions I didn't understand _at all_. But my resolution seems fine now. The new xorg.conf and the one I backed up before messing with the reconfiguring are quite different, which worries me too. But we'll see what happens.

When I initially installed Kubuntu everything worked fine, until now, no questions asked, by default. Is there a way of generating a sort of default xorg.conf again without having to answer weird questions? Any ideas? I'm kind of proud of having fixed this myself, but like I said, the xorg.conf diff worries me. xorg.conf is a scary file.

---

