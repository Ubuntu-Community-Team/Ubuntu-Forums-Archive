---
title: "No icons in Dash"
date: 2011-05-09
forum: Desktop Environments
---

### Post by vaibhav on 2011-05-09
Yesterday I upgraded from Lucid to Natty. I'm having this issue where I don't see any icons in the Dash menu. There are only "Browse the Web", "View Photos", "Check Email" & "Listen to Music" icons which work correctly.
But on clicking "Media Apps", "Internet Apps", "More Apps" and "Find Files", nothing happens.
Search also doesn't work, e.g. typing "calc", I expect the "Calculator" app icon to show up, but doesn't happen.

How do I resolve this?

Thanks.

---

### Post by silvagroup on 2011-05-11
I have the same problem I see there have been many views and no response with a remedy.
I am thinking probably something to do with video driver.
I have a late model nvidia, how about you?

---

### Post by SpaceMaster on 2011-05-11
I'm having the same problem on my desktop, a massive Dell Precision.

late model NVidia GeForce card.  Tried running the version 173 (recommended) driver (which is what is running and working on my laptop), but all that does is make my menus and window borders vanish.  

To top it off, even when I install the proprietary drivers, I still don't get 3-D acceleration.  In fact, even flash plug-ins for web browsers (Abobe for both Chrome and Firefox) run choppily, and when I full-screen them it starts what should be the bottom at the middle of the screen.

The system does seem to run *marginally* better in Gnome, but I have no 2-D or 3-D acceleration at that point.

Compounding on all of this, X-server crashes after I resume from a Suspend state.  And by crashes, I mean my screen fills with colorful space-tartans from Cosmic Celts traveling back in time to warn me not to ever hit that button to upgrade from 10.10 to 11.04 (a few days too late, sadly).

---

### Post by vaibhav on 2011-05-11
Mine is Intel onboard. It's two year old laptop.
I don't have other graphics problems: 3D works correctly. It's just the Dash menu that is having problems.

---

### Post by mc4man on 2011-05-11
If the "Media Apps", "Internet Apps", "More Apps" and "Find Files" and search don't work than make sure that these packages are installed
unity-place-applications
unity-place-files

---

### Post by Frogs Hair on 2011-05-11
> **SpaceMaster said:**
> I'm having the same problem on my desktop, a massive Dell Precision.

late model NVidia GeForce card.  Tried running the version 173 (recommended) driver (which is what is running and working on my laptop), but all that does is make my menus and window borders vanish.  

To top it off, even when I install the proprietary drivers, I still don't get 3-D acceleration.  In fact, even flash plug-ins for web browsers (Abobe for both Chrome and Firefox) run choppily, and when I full-screen them it starts what should be the bottom at the middle of the screen.

The system does seem to run *marginally* better in Gnome, but I have no 2-D or 3-D acceleration at that point.

Compounding on all of this, X-server crashes after I resume from a Suspend state.  And by crashes, I mean my screen fills with colorful space-tartans from Cosmic Celts traveling back in time to warn me not to ever hit that button to upgrade from 10.10 to 11.04 (a few days too late, sadly).

I use an 8400 GS and though the 173 driver is offered so is the Nvidia current 270 .41 . I installed the 173 driver by mistake once and It does not work , even with my 8 series card . I had the same choppy video . when I realized my mistake and installed the Nvidia current every thing woks fine.

---

### Post by vaibhav on 2011-05-11
> **mc4man said:**
> If the "Media Apps", "Internet Apps", "More Apps" and "Find Files" and search don't work than make sure that these packages are installed
unity-place-applications
unity-place-files
Thanks! That worked.

---

