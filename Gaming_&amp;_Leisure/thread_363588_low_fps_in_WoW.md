---
title: "low fps in WoW"
date: 2007-02-17
forum: Gaming &amp; Leisure
---

### Post by somerthing on 2007-02-17
i installed wow:tbc and i can actually play without using -opengl.. infact using -opengl screws up the graphics and makes it unplayable

i've been trying many tweaks and editing many files to try and raise the fps in warcraft but i'm unable to pass 6 fps..

are there any tips for raising the fps?
i've tried the regedit tweak       
and also the launcher.sh tweak with worse results

maybe my laptop at its limit?
915gm chipset, 128mb video ram, 512mb ram

my video driver, i810, is up to date.
something maybe worth mentioning 
i get this message in terminal alot: 
libGL warning: 3D driver claims to not support visual 0x5b
and yes, glxinfo says direct rendering: yes

---

### Post by hikaricore on 2007-02-17
Yea it's your video card/drivers.  I had an integrated intel on my motherboard, I got 4fps when I was lucky and the ground textures were screwed up all to hell.  I upgraded to an Nvidia card, but I know for a laptop that isn't easy/possible.

You may try shutting down all unneeded services INCLUDING gdm and X.  Then using the launcher tweaks from a command terminal, which will launch X on a new screen (Ctrl+Alt+F4 for me) and you can play from there a little better than before.  You'll need to either run the launcher script with sudo or as root.  Hope this helps.


--Aaron

---

### Post by maxamillion on 2007-02-17
> **hikaricore said:**
> Yea it's your video card/drivers.  I had an integrated intel on my motherboard, I got 4fps when I was lucky and the ground textures were screwed up all to hell.  I upgraded to an Nvidia card, but I know for a laptop that isn't easy/possible.

You may try shutting down all unneeded services INCLUDING gdm and X.  Then using the launcher tweaks from a command terminal, which will launch X on a new screen (Ctrl+Alt+F4 for me) and you can play from there a little better than before.  You'll need to either run the launcher script with sudo or as root.  Hope this helps.


--Aaron

I don't have any experience with WoW on any platform, but doesn't it need X to run?
.... just a thought.

---

### Post by hikaricore on 2007-02-18
> **maxamillion said:**
> I don't have any experience with WoW on any platform, but doesn't it need X to run?
.... just a thought.

Yes and the launcher script launches a separate X session.  So there is no need to be running gnome and gdm and everything else + your main X session while trying to maximize resources for WoW.  :)

---

