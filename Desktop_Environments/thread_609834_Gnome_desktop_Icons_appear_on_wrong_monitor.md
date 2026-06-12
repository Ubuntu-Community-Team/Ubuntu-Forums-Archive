---
title: "Gnome desktop Icons appear on wrong monitor"
date: 2007-11-11
forum: Desktop Environments
---

### Post by thelost on 2007-11-11
Anyone else found setting up dual monitors as frustrating as I have? Well that's the price I guess for choosing Linux.

Currently any newly created files on my Desktop are appearing on my secondary monitor, how can I change this?

---

### Post by Tristan Schmelcher on 2007-12-05
I have the same problem. I'm using an up-to-date gutsy install with NVIDIA TwinView with the primary monitor on the right. "Clean up by name" puts all desktop icons on the left monitor. New icons always show up there too.

Are you using TwinView or two separate X screens? I think I'm going to file a bug.

---

### Post by thelost on 2007-12-05
is your primary monitor a flatscreen and your secondary (the one the icons appear on) a CRT? I read somewhere that it was a 'feature' that the CRT monitor was always treated as the first and therefore icons will always appear there if you happen to have a TFT+CRT setup.

someone correct me if I am talking baloney!

---

### Post by Tristan Schmelcher on 2007-12-05
Nope, mine are both flatscreens. Specifically, the primary monitor is my laptop's built-in LCD, and the secondary monitor is my Sony LCD TV.

---

### Post by Jhongy on 2008-04-29
Same problem here. 

The LCD/CRT assumption is incorrect. Everything else is OK -- my primary monitor is on the right, and behaves properly, apart from icon placement.

I believe Gnome just likes to create new icons as close to the top-left of the desktop as possible, which places them on the left screen, which in our case is the wrong screen -- they should be on the primary monitor.


I can see no gconf options to modify this behaviour -- the only thing I can think of is to reverse screen positions, ("leftOf" to "rightOf"), which of course is far from ideal 
My experience with Gnome is that they probably won't want to be bothered to fix this :-(

If anyone manages to file a bug, or find a patch, please post.

J

---

