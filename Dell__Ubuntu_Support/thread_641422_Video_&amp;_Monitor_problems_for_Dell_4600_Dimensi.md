---
title: "Video &amp; Monitor problems for Dell 4600 Dimension"
date: 2007-12-15
forum: Dell  Ubuntu Support
---

### Post by dbrilliant on 2007-12-15
I have a Dell Dimension 4600 series 2.8 GHz PC with a ATI Saphire Radeon Pro 1650 (512 4/8X AGP, 1.4Ghz core clock) video card. The funny thing is at first the live cd worked and Ubuntu 7.10  installed perfectly the first few times, meaning after updating Ubuntu 7.10, the restricted ATI drivers did not work and I forgot to make a backup of xorg.conf file. A couple weeks later I had to install a new monitor (Acer 20" 2500:1). Now the Live CD won't let me do anything.. I have heard about a possible problem w/ Ubuntu 7.10 restricted drivers & hard resolution issues through the grapevine.
Anyone have a problems like these? Any help would greatly be appreciated.

---

### Post by dtgolder on 2007-12-16
I'm having a problem with a Dell PowerEdge 400SC...video works fine on initial install, but when I change resolutions I get a black striped box (looks like a UPC code) in the top left of the screen.

Interesting...I do a screen print and it's not there...so it's a monitor problem. Anyone have any idea?

---

### Post by dtgolder on 2007-12-16
Ok, this is really weird...was going to try some different things, so I opened a terminal and pasted in: sudo dpkg-reconfigure xserver-xorg and hit enter

BUT--when it gave me the next terminal line (asking for my pw) the UPC box went away!

I never put in my sudo pw so the command never executed, but it solved the issue...

(Now I'd love for someone to be able to explain that one)

---

### Post by dtgolder on 2007-12-16
Ok, now rebooted and the UPC code returns!

BUT--opening a terminal window (and typing anything in it seems) 'fixes' the issue.

Anyone have any ideas? (More an annoyance than anything)

---

### Post by michaelmrtn on 2007-12-17
DELL ACCOUNT - hi sa lahat ng trucast ky sir bryan, sir manny, kuya don, glaiza, irish, gerald, jay, jorbel, almar, ron,jade at gem.. more power to u guyz dont stop scoring!!!!!!!!!!!!!!!!!!!!!

---

