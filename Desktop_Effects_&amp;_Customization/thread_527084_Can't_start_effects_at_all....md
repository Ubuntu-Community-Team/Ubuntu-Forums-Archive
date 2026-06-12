---
title: "Can't start effects at all..."
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by Alexis Phoenix on 2007-08-16
Okay, I've been playing with my new Dell laptop with Ubuntu on it for a while now, but I can't get desktop effects to work.

The machine is a dual core turion AMD64 Inspiron 1501 with 1GB of RAM, a nice fat hd and a huge battery.  It has an ATI card (I forget which and can't check since I'm at work.

It seems the ATI fglrx driver doesn't support compiz (and disables 3d rendering when "composite" is loaded) and the free ati driver doesn't have 3d hardware support - so no matter what I do I can't have funky desktop effects to impress my friends!

(as an aside, I'm running with the composite extension disabled as this gives a snappier desktop, and lets me have a virtual mouse cursor in qemu/kvm)

If there's a solution to this - can anyone please tell me!! (even if it's a really slow solution - what happened to that "looking glass" 3d java desktop that came out a while ago?)

tia
Alexis

---

### Post by kellemes on 2007-08-16
fglrx works fine with Xgl. I have 3d-stuff and everything with the fglrx-driver.
You have to google or search the forum for setingup fglrx with Xgl.
It may take some fidling but it'll work.

---

