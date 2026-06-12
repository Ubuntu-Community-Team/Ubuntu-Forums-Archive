---
title: "2D No Go"
date: 2005-10-21
forum: Gaming &amp; Leisure
---

### Post by Mizutsuki on 2005-10-21
I'm a pretty green newb when it comes to linux.  I've been running Breezy for about a month now, and I'm having an issue with 2D graphics applications moving extremely slowly.  Screensavers run at about 2 FPS, and when I dosboxed Monkey Island 2 I had similar results.
I'm running on an IBM Thinkpad T22: 900 MHz Pentium III and an S3 Savage IX8 (AGP 2X 8MB RAM.)
I realize with my hardware I'm not going to be running Doom 3, but I thought I'd be able to run Doom 1!
Any thoughts?
Thank you.

---

### Post by Perfect Storm on 2005-10-21
Most of the screensavers are 3D related, make sure that the screensaver you picked are a non-3D.
To run things on emulators takes its told. Have you tried running monkey Island on [http://www.scummvm.org/](http://www.scummvm.org/)

How much ram do you got?

---

### Post by Mizutsuki on 2005-10-21
Thank you,
That's a good suggestion about SCUMMVM, it certainly works much better than dosbox, but it's still not at 100% speed when at full screen.  Strange, that.  That it should get progressively slower when I increase the display size.  I don't really understand what that all means...
Anyway, I've got 256 MB or RAM,
Anything else you might want to know about the laptop is here:
[http://www.thinkwiki.org/wiki/Category:T22](http://www.thinkwiki.org/wiki/Category:T22)
Thank you again.

---

### Post by Perfect Storm on 2005-10-21
Have you tried to see if the a kernel-686 gives any improvement?

sudo apt-get install linux-686 linux-image-686

---

### Post by Mizutsuki on 2005-10-21
I installed it, but no change, any other ideas?
Thank you.

---

### Post by Mizutsuki on 2005-10-21
Oops... nevermind this.

---

### Post by Mizutsuki on 2005-10-23
Bump

---

### Post by Perfect Storm on 2005-10-24
Sorry, I don't what else to suggest. But I suspect it have to do with your Savage card.

---

### Post by fragmental on 2005-11-03
use system monitor or "ps -a u" to make sure that something isn't taking up a lot of cpu cycles or memory.  If nothing is, make sure you have the best savage drivers and that agp is working.  You could also consider dumping the savage.  $24.99 gets you a geforce 2 ti, shipped, at [http://3btech.net/nv.html](http://3btech.net/nv.html).

I would assume it was the memory or cpu before the card, though.  Might want to run memtest.  More ram couldn't hurt.  There might be some unneeded process you might want to kill.

---

### Post by slux on 2005-11-03
Changing a video card on a laptop isn't going to work now, is it? :)

The probable cause for this is that the Xorg drivers for the Savage are poor. There might be some options not enabled in Xorg.conf for it that would make it a bit faster, you need to check the driver documentation. You could just google for problems with similar video cards and might stumble upon a solution.

---

