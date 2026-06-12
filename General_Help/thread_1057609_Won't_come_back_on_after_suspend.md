---
title: "Won't come back on after suspend"
date: 2009-02-02
forum: General Help
---

### Post by themagicmanfromtrent on 2009-02-02
Hi all,

Some problems with power settings on my laptop.

I have a Dell XPS M1530, and I like it set so that when I close the lid, nothing happens. I got this to work, but when I open it back up again, the touchpad stops working and I'm forced to use an external mouse or reboot.

Another problem is I can't put the laptop to sleep (suspend), and when I try to turn it back on, it simply gives me a blinking underline light in the top left corner.

Any suggestions?

Danny

---

### Post by lunchbox910 on 2009-02-02
I have this same problem as well. To go further, if my screen saver is on long enough for it to hibernate or sleep or whatever ever, I can't bring it back I have to reboot. I'll be tracking this for a good solution if anyone has one.

---

### Post by jespdj on 2009-02-02
What video card do you have an what video driver are you using?

It seems that there's a problem with nVidia driver version 180.xx which causes this with some Linux kernel versions.

I'm using nVidia driver 177 on my M1530, it works much better than 180 (besides the not waking up from suspend, I get other problems with driver 180 like parts of the screen not being refreshed properly and sometimes graphics artifacts).

---

### Post by themagicmanfromtrent on 2009-02-03
> **jespdj said:**
> ...like parts of the screen not being refreshed properly and sometimes graphics artifacts...

Yeah,  I get that as well. Not only that, Ubuntu is really laggy. I have an 8600 GT. Admittedly, it's not the best of cards, but it should be able to handle the desktop effects like a walk in the park...

The reason I know there's something wrong with ubuntu, is because Vista Ultimate + Aero boots significantly faster than ubuntu does. Ubuntu takes absolutely ages.

I have Compiz, Awn and screenlets installed, so i don't expect it to load in 10 seconds, but it shouldn't take a minute and a half...

I'll try to rollback the drivers to 177, but I don't think that's my only problem here...

---

### Post by themagicmanfromtrent on 2009-02-07
badabump

---

