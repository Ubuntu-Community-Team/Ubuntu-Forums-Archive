---
title: "What are my options - Ati 4770"
date: 2009-06-10
forum: General Help
---

### Post by randyklein99 on 2009-06-10
I didn't want to hijack any of the various threads regarding Ati's vid cards and driver setup, so I'm starting this thread to see what kind of options are available to ATI 4770/Jaunty owners who are trying to get it working.

Here's how I see it after reading as many threads as possible:

- It seems the open source drivers in Jaunty, both the stable release drivers (ati) and RadeonHD, don't fully support this new card yet.  Would upgrading the kernel, xorg, or anything else help with this? If so, any links on how to attempt any of those?

- Catalyst 9.5 doesn't seem to work well with Jaunty's kernel.  I've read that you can patch it so it does, any good how-to's for the experimental types?

It also appears that these fixes are mutually exclusive since you'll need to upgrade to get open-source working, but patch (or downgrade) to get closed source working.

Am I missing anything or am I just exposing my complete newbness on this matter.

---

### Post by fdmille on 2009-06-11
You seem to be correct.  I just installed a Sapphire HD 4770 vga card in my Ubuntu 9.04 32-bit machine to replace a Sapphire X550 vga card.  When I booted again I installed the ATI/AMD proprietary driver from the Hardware Drivers menu.  All good until I logged out as recommended and got the black screen of death.  From this point I had to boot in recovery mode and install envyng from the command line and install the ATI drivers from envyng.  I was then able to get the graphic login screen, but lost my dual screens.

---

### Post by Evontroy on 2009-06-11
My Radeon 4830 is working just fine with the Catalyst 9.5 drivers. Is there an issue with Linux and the Radeon 4770 that I am unaware of?

---

### Post by fdmille on 2009-06-17
The ATI 9.6 drivers are now available and seems to work much better for me.  See the Jaunty [installation guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide").

---

### Post by randyklein99 on 2009-06-18
that sounds like some good news.  i'll have to try that when i get a chance. thanks for the update.

---

### Post by randyklein99 on 2009-06-19
Installed the 9.6 drivers.  I can now logout and switch users without locking up.  That's a huge improvement.  Oh and all with Compiz on.

However, the initial login and initial switch, after entering the password, you get a blue background with quickly flashing black bar randomly on the screen for about 15 seconds and then you get the desktop.  Switching back to a user though does not experience this flashing.  Any clues on how to fix that? Or is wait until 9.7???

---

### Post by randyklein99 on 2009-08-04
> **randyklein99 said:**
> 
However, the initial login and initial switch, after entering the password, you get a blue background with quickly flashing black bar randomly on the screen for about 15 seconds and then you get the desktop.  Switching back to a user though does not experience this flashing.  Any clues on how to fix that? Or is wait until 9.7???

9.7 has the same issue.  And occasionally lockups with VLC.  I see that the RadeonHD driver now has 2d acceleration support for the 4770, so I'm going to try that.

---

