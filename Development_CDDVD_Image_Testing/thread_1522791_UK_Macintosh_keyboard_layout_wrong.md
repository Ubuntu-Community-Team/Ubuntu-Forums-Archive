---
title: "UK Macintosh keyboard layout wrong"
date: 2010-07-02
forum: Development CD/DVD Image Testing
---

### Post by tpg on 2010-07-02
Hi - I've just tried installing Alpha 2 into a Virtualbox VM (host OS X). After selecting United Kingdom - Macintosh for the keyboard layout, I've found that the key containing "§" and "±" is mapped to give "<" and ">" symbols (in the test box within the installer).

Is this a known bug, or if not, what should I file it against? Cheers.

---

### Post by tomynho on 2010-07-07
I don't think this is a bug. 
For example, in Slovak keyboard layout under Win XP & 7, to get the ' character you have to press Alt Gr + P. Under Ubuntu you have to press Alt Gr + J I think.
There are different ways of entering special characters under different operating systems. 
It's not only Mac OS X vs. Ubuntu issue.

---

### Post by simosx on 2010-07-07
> **tpg said:**
> Hi - I've just tried installing Alpha 2 into a Virtualbox VM (host OS X). After selecting United Kingdom - Macintosh for the keyboard layout, I've found that the key containing "§" and "±" is mapped to give "<" and ">" symbols (in the test box within the installer).

Is this a known bug, or if not, what should I file it against? Cheers.

There is an option in the keyboard indicator applet to show who character is expected for each key on the keyboard. Check there if indeed the Linux GB Mac layout has those characters.

It's possible that this could be a bug in virtualbox in the way it interprets keycodes and the way the guest Linux receives them. If the layout is correct and virtualbox is to blame, file a bug report similar to [http://www.virtualbox.org/ticket/7022](http://www.virtualbox.org/ticket/7022)

---

### Post by glasen on 2010-07-09
Try booting the kernel with the option "hid-apple.iso_layout=0". 

This option disables the hard-coded ISO-layout of the keyboard-driver.

---

