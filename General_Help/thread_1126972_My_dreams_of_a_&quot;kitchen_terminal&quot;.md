---
title: "My dreams of a &quot;kitchen terminal&quot;"
date: 2009-04-15
forum: General Help
---

### Post by Vunutus on 2009-04-15
I've been pondering the idea of a kitchen computer for a while now. It would be used for grocery inventorying, recipes, music, and the odd video or two.

The basic idea from a technical standpoint is this:

Build a VERY barebones computer and mount it somewhere hidden in the kitchen. It would have no cd drive, no hard drive, no keyboard, no mouse, none of the standard peripherals. Pretty much only a motherboard, CPU, RAM, and a wireless NIC. All interfacing with it would be done via a touch-screen monitor (with some on-screen keyboard software for when typing is needed). Now the cool thing (in my opinion, at least) is that all the software and heavy lifting will be done on another (more powerful) computer (theoretically inside some VirtualBox image).

Other than sharing an idea that I find cool, my justification for posting this is that I also have a few questions.

1. Is there a better way to redirect video output of a virtualbox image than a visual SSH session?
2. What are the minimum possible specifications that such a computer should have?
3. What distro of Linux should I use for the computer in question? It has to be very low in bloat and also support graphical SSH sessions.

EDIT:

4. Is there a such thing as a cheap touch screen monitor?

---

### Post by hikaricore on 2009-04-15
You would need some sort of drive just to boot to at the very least...  like a usb thumb drive for example.  :)

---

### Post by Vunutus on 2009-04-15
> **hikaricore said:**
> You would need some sort of drive just to boot to at the very least...  like a usb thumb drive for example.  :)

That's what I planned on doing for the OS. No need to mount a big and noisy hard drive just to store 500MB or less of data. Thumb drives are generally bad for long term OS storage, but if it ever craps out it's not like they are hard to replace.

---

### Post by Spritegeezer on 2009-04-15
I am building precisely the same sort of machine but with some extras.  It uses an mini ITX form factor motherboard.  The case, with power supply is 8" x 9" x 2".  It has 1 Meg of RAM and a 120 G Toshiba hard drive. The display is a 10.4" 12volt unit with a touchscreen.  I'm using a tiny Solidtex keyboard (10").  I have a TP-Links usb wireless g adapter.  I'm running Ubuntu 9.04 and it works like a charm.  The only problem I'm facing is getting the touchscreen drivers on board.  They are written for non-Debian based Linux and I need to learn the differences in installation techniques. I want to use it for recipes in the kitchen without paper.  Wish me luck.

---

