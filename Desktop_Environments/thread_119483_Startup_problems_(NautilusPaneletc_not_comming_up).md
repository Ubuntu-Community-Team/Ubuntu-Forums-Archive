---
title: "Startup problems (Nautilus/Panel/etc not comming up)"
date: 2006-01-19
forum: Desktop Environments
---

### Post by fireonyx on 2006-01-19
I have been having some problems on startups.  Every now and then, when I leave my laptop on w/o power and battery runs out, when I try to restart the computer, it will start x fine.  I can log in like normal, (where it says enter username/pw).  But then it just goes to a brown screen with a mouse pointer and sits there.  The Ubuntu box that starts nautilus/the panel/etc doesnt start up.  Which leaves pretty much nothing to do.  I have control-alt-backspace, tried all the different variations, none of them gets me going.

On a (hopefully) unrelated issue, on the startup, it says that 8139cpp or something like that isnt compatible, and to use 8139too.  Also, I would like it to not connect to the time server? ntf. whatever on startup.  Where do I go to edit those things?

Thanks

Fireonyx

---

### Post by fireonyx on 2006-01-20
One thing I have noticed...  when I do have this problem, I can modprobe -r ndiswrapper, and then login perfectly ok... Another thing is that this missing desktop thing is that it happens only when I have the same wireless network avaliable as what was saved in the network manager.

Any ideas other then getting rid of NDIS?

---

### Post by carlosqueso on 2006-01-20
It may be your ndiswrapped card...what wireless card do you have? (use lspci to show the chipset) and what does ```
ndiswrapper -l
``` show?

---

### Post by kuriharu on 2006-01-20
I have exactly the same problem on my laptop, and I don't have ndiswrapper installed (I've given up on wireless on Linux -- it just doesn't work).

Last night, I changed themes and my login screen for GNOME. The new login page comes up and I log in, but then I get the brownish yellow screen with a mouse pointer and that's it. No Nautilus, no desktop.

---

### Post by fireonyx on 2006-01-21
My wireless card is : 0000:05:02.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

Not sure if my statement of how I got around it makes sense, let me describe it again.

When I go into Network Management, there is a network there that it saves (not sure how it decides which one to keep in there...).  Whenever I boot up and that is the network that I am in, all my nautilus/panel/etc doesnt start up, leaving me with a brown screen and a mouse.  Nothing to click on, nothing shows up /w right clicking.  Makes life difficult.  The trick to getting around this is by starting the fail-safe terminal, and doing a sudo modprobe -r ndiswrapper.  Then I log out of the terminal, log in as normal.  Everything comes up like normal.  Then I can go back in and do a modprobe ndiswrapper, and get wireless to run fine.  

When I boot up in an area where the network listed in network management isnt avaliable, everything boots up just fine.  (Except when I am trying to get suspend to memory to work, but I think that is an entirely different issue.)

And from Kurihari's post, it looks like this isnt just me.  Ill be posting this in the ndis support forum (if I can find it).  Maybe they might know whats going on.

Fire Onyx

EDIT : Oh, and ndiswrapper -l shows : 

Installed drivers:
bcmwl5          driver present, hardware present

---

