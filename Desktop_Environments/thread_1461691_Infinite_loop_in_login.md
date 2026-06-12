---
title: "Infinite loop in login"
date: 2010-04-24
forum: Desktop Environments
---

### Post by SamuraiCrow on 2010-04-24
Hello, I've just installed Xubuntu 9.10 on my dad's Dell Dimension L800r with 192 megs of RAM, a Radeon 7000 PCI graphics card with 64 megs of video RAM.

After installing all of the package upgrades and one package other than what was added by default, the system rebooted fine.  Before the last reboot I changed 3 things:  Set the default video mode to 1024x768 at 60 Hz scan rate, installed the printer drivers for his HP PSC 1110, and added two launchers to the panel at the top of the screen.  Now when I rebooted from that point onward, the GDM login prompts me for his name and password and after I enter them it loads for a while and eventually pops up the username and password prompt window again.

First off, I doubt that merely adding launchers to a panel caused the problem.  That leaves changing resolutuions and installing printer drivers as the two culprits.  Since it should boot up without problems upon the event of a printer driver mixup, I suspect changing resolutions was the problem.

How do I fix it?  I can only access the root command prompt from the recovery-mode login from GRUB.  From there I can type startx to get into the desktop but I'm still logged in as root.  How do I change the resolution settings for the user account?

--edit--
Solved.  I typed su user from the root prompt and startx got me in.

Now for my next question:  What would cause GDM to mess up that way?

---

