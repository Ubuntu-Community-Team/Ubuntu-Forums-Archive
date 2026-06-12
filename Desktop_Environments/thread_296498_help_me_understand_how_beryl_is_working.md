---
title: "help me understand how beryl is working"
date: 2006-11-09
forum: Desktop Environments
---

### Post by shrndegruv on 2006-11-09
Hi

installed ubuntu edgy, coming from gentoo.  I have a two year old laptop with an ati m300 card.

I followed the guide off of the edgy tips and tricks page for installing xgl/beryl.  This guide has you set up an xgl desktop session, and it also has you put beryl in the gnome-session settings.  When I start the xgl session, it comes up fine, but as soon as you try anything the screen gets all distorted and becomes unusable.  

When I start a normal gnome session, however, beryl works fine, with all effects.  Its really amazing and blows my mind.  I have xgl working on my gentoo desktop, but I get better performance on the inferior laptop.

What I suspect is happening is ubuntu installed the open source radeon drivers, and some sort of composite manager, and beryl is running off those.  Is this correct?

If beryl works when started the gnome, why wont the xgl desktop session work?

thanx.

---

### Post by mannheim on 2006-11-09
I'm no expert, but --- I think Beryl can use one of two underlying mechanisms to support its effects: either xgl or aiglx. Your explanation seems correct: the open-source radeon drivers now support aiglx, and beryl will use aiglx if it doesn't find xgl. That is probably what is happening.

---

### Post by shrndegruv on 2006-11-10
but why wont it work when I try to start xgl?

---

### Post by dbd on 2006-11-13
can you post your /etc/X11/xorg.conf

Have you actually installed any drivers, and which ones (which guide did you use)? Also, what is the output of:
fglrxinfo

---

### Post by igknighted on 2006-11-13
well if he has beryl running off of AIGLX I'm gonna go out on a limb and guess that fglrx info will return a bad command, he is using the 'radeon' driver.

---

