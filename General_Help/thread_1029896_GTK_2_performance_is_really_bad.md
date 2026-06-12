---
title: "GTK 2 performance is really bad"
date: 2009-01-03
forum: General Help
---

### Post by elli222 on 2009-01-03
I have a very strange problem.
I mean really strange.
Even stranger when i look at my hardwere specs
I just can't belive it!

Memory:
4 x 2GB corsair dominator DDR 2

Processor:
AMD Phenom X4 Black edition

Motherboard:
ASUS M3N-HT Deluxe/Mempipe (nForce 780i Chipset)

Graphics:
(Currently)
nForce 780i onboard. 3D acceleration working fine (i can run compiz AND nexuiz!)

But for some extremely strange reason, my gtk 2 performance is really crap.

With very little running , no compiz, no games, i can drag a sole terminal window about and see more of them on the nautilus desktop.

The refresh rate and overall performance of any gtk 2 app is really bad.

Also, this simple game that uses gtk 2 and gnome development libaries, runs incredibly slowly and is very unresponsive. The game is Word war vi

And, funnily enough, a 32 bit system with a 1.50 GHz intel CPU runs the game a lot faster.

1.50 GHz is less than one of my four cores (apparently)

This just doesn't add up. It defies logic.

It was using the same up-to-date libraries as my ultra-high-spec computer.
WHAT THE HELL!?
I really want to fix this! Can somebody please help me?
I love this game! I like GTK 2! I hate what its doing to me!

[Word war VI webpage]("http://wordwarvi.sourceforge.net")
This is the website of the game

If you want to test:
You will need port audio 1.9 (not 1.8) and devel files 
Also libvorbis (and devel files)
And libgnome (and devel files)
then make and ./wordwarvi (there is no configure script)

Please help!

---

### Post by elli222 on 2009-01-05
Ive noticed something even more confusing.
Running the very same program on the same setup over a XRDP/VNC connection works fine. Which means that something is poorly configured or some kinda hardware problem.

I will take a peek at my xorg.conf and see if anything is futzed up in there

---

### Post by elli222 on 2009-01-05
Ive noticed something even more confusing.
Running the very same program on the same setup over a XRDP/VNC connection works fine. Which means that something is poorly configured or some kinda hardware problem.

I will take a peek at my xorg.conf and see if anything is futzed up in there

---

