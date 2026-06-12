---
title: "Random jumbled fonts in all apps"
date: 2009-05-27
forum: General Help
---

### Post by insertnewsn on 2009-05-27
Hey everyone..

Ever since I upgraded to Jaunty, my fonts will randomly become scrambled and jumbled. I say randomly because this bug might occur right when I turn my laptop on, or it might take 2-3 hours to show itself.

It looks as if it's a keyboard/font issue, as some letters will replace others ('a' will replace 'o', etc.)

I've attached a screenshot to show exactly how annoying this bug can get...

Please note that the only way I've been able to fix this is by logging out or by a clean restart.

Any help anyone could give would be greatly appreciated!

Thanks.

---

### Post by insertnewsn on 2009-05-30
Bump!

---

### Post by insertnewsn on 2009-06-03
..Still having the problem :-(

Bump!

---

### Post by barbus on 2009-10-06
Hi, I'm having the same problem as described here. In my case it's an old IBM ThikPad R31 with i830 graphics. I did some googling on the subject and have so far come up with that it's connected with graphics driver using graphics hardware to cache already rendered glyphs (apparently it's a widely used performance improvement that's part of a lot of VGA drivers). Sadly it's mostly happening to people using KDE but all solutions have been connected with graphic drivers and Xorg so what's to stop it from happening in GNOME, right?

I've so far used CentOS on heaps of hardware and have never seen issues like this, so it could also be connected with Ubuntu's "near-bleeding-edge" philosophy (Fedora people showed up often with these issues in my search). The PC dual boots XP which works fine.

To describe the problem: the "scrambled" glyphs progressively take more and more characters from a character set at given font size. And when subpixel smoothing is used they have these brown and green areas, probably linked to antailiasing being used. When restarted (or X restarted) the issue dissapears only to slowly creep back in until most text on one's screen is crap.

Anyeay, what I haven't found in my search is a way to disable this glyph-caching feature in Ubuntu. The version I use is 9.04

Also, when we're at it, since mine is an old computer, how does one disable useless eyecandy (like that annoying desktop background transition "animation" which hogs my PC to a near-halt.

---

### Post by StuartN on 2009-10-06
There is some discussion here [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059)

> **barbus said:**
> Also, when we're at it, since mine is an old computer, how does one disable useless eyecandy (like that annoying desktop background transition "animation" which hogs my PC to a near-halt.

System->Preferences->Appearance, Visual Effects tab, None.

---

