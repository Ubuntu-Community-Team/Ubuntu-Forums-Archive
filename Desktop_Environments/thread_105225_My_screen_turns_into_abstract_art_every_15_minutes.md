---
title: "My screen turns into abstract art every 15 minutes"
date: 2005-12-17
forum: Desktop Environments
---

### Post by Azmodan on 2005-12-17
I ran Ubuntu without any major problem since Hoary.  I decided to switch to Kubuntu to see what it was like.  So I did a clean install and everything seemed to be okay.

Except that every 15 minutes (on average, the phenomenon is random), my screen turns into something that looks more like abstract art than my desktop.

I included a screenshot.

Any idea what can cause this and how I can solve it ?

Thanks

---

### Post by MetalMusicAddict on 2005-12-17
Can you give details about your video setup? What video card are you running?  Dual-Monitor? Have you edited you xorg.conf at all? What kind of monitor? Etc...

---

### Post by mcmuffy on 2005-12-17
The last time I got that sort of effect was when a graphics card overheated due to a dodgy fan which caused the card to crash.

---

### Post by Eazy© on 2005-12-18
I had simular problems. 
Once I installed Nvidias graphic driver for my nvidia 6600gt agp from synaptic the problem disappeared.

---

### Post by ace2005 on 2005-12-18
I've just got to ask, how did you take the screenshot if you're desktop screwed up, if its hardware related you wouldn't be able to use something like ksnapshot and the picture looks too good to be a photo.

---

### Post by Azmodan on 2005-12-18
I restarted the computer this morning and the problem is still there.  I did a sanity check with Knoppix and there isn't any problem with it.

My video card is an NVIDIA GeFORCE 6200 branded MSI NX6200TC.  I'm unsure about my monitor but it's a LG.

nvidia-kernel-common is installed and nvidia-glx too.  But things using openGL doesn't work.

Any diagnostics you need ?

---

### Post by Azmodan on 2005-12-18
[quote=ace2005]I've just got to ask, how did you take the screenshot if you're desktop screwed up, if its hardware related you wouldn't be able to use something like ksnapshot and the picture looks too good to be a photo.[/quote]

Ksnapshot missed the panel at the bottom which was visible.  As is anything that is redrawn on the screen but after a few seconds it disapears again.  So by moving the mouse around, I can see buttons.

---

### Post by Azmodan on 2005-12-18
Bump.

Help ?

Edit : I got my monitor model it's LG Flatron ez T710MH

---

### Post by aysiu on 2005-12-18
There's no way it's the screensaver...?

---

### Post by MetalMusicAddict on 2005-12-18
Now that I think of it. I did have my screen do that when the GFX card went up.
Your 15 mins could be because thats how long it takes to overheat.

---

### Post by Azmodan on 2005-12-18
[QUOTE=MetalMusicAddict]Now that I think of it. I did have my screen do that when the GFX card went up.
Your 15 mins could be because thats how long it takes to overheat.[/QUOTE]

It used to be 15 minutes but now it's more like one.  Instant effect if I use Kmail.  I tried to reinstall plain Ubuntu to see what it would give.  It's safe from that problem but nothing 3D will work while it used to work out of the box before.

I think you are right and my video card is busted.  Still under warranty however.

---

