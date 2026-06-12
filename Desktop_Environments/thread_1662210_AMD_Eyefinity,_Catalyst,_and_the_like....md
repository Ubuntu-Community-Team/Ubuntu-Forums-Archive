---
title: "AMD Eyefinity, Catalyst, and the like..."
date: 2011-01-07
forum: Desktop Environments
---

### Post by PadreAdamo on 2011-01-07
This is my very first post here. I just recently got aboard this new horizon called Ubuntu and I love the journey thus far. I am having one issue at the moment and it's with Ubuntu and AMD eyefinity (3-monitors).

This setup works fine in Windows allowing me to play games in 5760x1200 resolution. I'm having trouble duplicating this effect in Ubuntu. I launch World of Warcraft and two of my monitors turn off while displaying it only on one. Does anyone know how to force Eyefinity to work?

Again, I'm not sure of the formalities here and if I need to post any conf files or logs. Any help is greatly appreciated.

Thank you,
-Padre

---

### Post by 0004tom on 2011-01-08
This will be some kind of limitation in xorg and wine. There are a few things you can try tho.

1. Have you tried changing the resolution in WoW?
2. You could have wine run in windowed mode and set up a desktop that spans all your monitors

Sorry I can't be anymore of a help here, But I don't play games in linux lol

---

### Post by PadreAdamo on 2011-04-12
It's been quite some time since I posted. I have been trying to install 11.04 Ubuntu beta but ran into some issues, which I submitted some bug reports. 

I'm about to start reinstalling Ubuntu 10.10. It seems, after extensive research with Eyefinity in Ubuntu, is how the windows are drawn. I need to specify resolutions of each monitor as they span in xorg conf.

Can someone post their xorg conf with Eyefinity spanning three monitors in the virtual resolution of 5760x1200? 

Thanks!
-Padre

---

### Post by rockstar2577 on 2011-05-15
^ This please.

---

### Post by devguy on 2011-05-27
I have the same issue.  "Eyefinity" in Linux is nothing more than 3 monitors working at the same time, each with their own individual resolution.

I'd like it to be like in Windows where there is "one" very wide resolution monitor.

---

### Post by devguy on 2011-07-03
So, I did get the desired effect I was looking for (more or less).  One has to select the single desktop (multiple display) option for every single monitor in CCC.  Then, reboot, and in CCC, turn off the Tear-free option, and then enable Xinerama.  Reboot again.

Now, I can stretch a single window across three monitors.  Unfortunately, here are the limitations:
[LIST]
[*]tear-free option causes major flickering on accelerated windows
[*]maximize window button only maximizes to local monitor (actually not a negative limitation IMHO)
[*]cannot have more than one accelerated input on top, or beneath, any other window
[*]still  no eyefinity bezel correction options
[*]can only log in with the "Ubuntu Classic (no effects)" option, otherwise X restarts (so no Unity)
[*]only one taskbar is drawn, which makes windows stretched across two or more displays show parts of the desktop where the taskbars are not
[*]fullscreen applications show my resolution as 4800x912 (should be 4800x900)
[/LIST]

Some pics have been uploaded for proof and example.  Achieved on Ubuntu 11.04 x64 with Catalyst 11.6 with a Radeon HD 6950.

---

