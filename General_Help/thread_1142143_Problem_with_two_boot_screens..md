---
title: "Problem with two boot screens."
date: 2009-04-28
forum: General Help
---

### Post by szenith on 2009-04-28
Okay, so I installed Ubuntu 9.04 beta off a live disk a little while ago starting it in Windows XP. When I started the disk in XP it asked me to reboot, and whether I would like it if it made a boot screen for me to select the Ubuntu installer. I was lazy and didn't want to go into BIOS and set it up to boot from the CD, so I said yes and let the installer create a boot screen. So I rebooted and selected Ubuntu instead of Windows XP and installed it fine. I have been using Ubuntu and am enjoying it a lot. 

But the thing is, is I have two boot screens now for if I want to log onto Windows, which I just do if I want to play games. There is the regular Ubuntu boot screen which asks if I want to log onto Ubuntu in safe mode or regular and whatnot or if I want to log onto Windows XP. If I select Ubuntu it takes me straight to Ubunti without any problem, but if I select Windows XP off of that screen it takes me to another boot screen that asks me to again pick between Windows XP and Ubuntu, the same one I used for the installer. I'm wondering, how do I get rid of that second boot screen? I think it might be linked to the installer, but I'm not sure. But really I don't want two boot screens and I don't want someone who is using my computer to get confused and use that screen to get into Ubuntu because it might take them to the installer. Well, I just want to get rid of that second boot screen.

Any ideas on how to get rid of it? Again it was a boot screen created by the Ubuntu live CD when I loaded in Windows for it to boot off of the Ubuntu 9.04 beta CD rom. Any help would be appreciated, thank you!

edit: this is SOLVED, since I solved it myself, but I can't figure out how to get the title to say [SOLVED]..

---

### Post by szenith on 2009-04-29
Anyone have any idea of how to help with this? I know it's a question involving WINDOWS so you may now want to help..but if someone could that would be appreciated!

---

### Post by szenith on 2009-04-29
Also, to add, this is not a Wubi install, Ubuntu is installed on ext3.

And the first boot screen, which is fine, is GRUB.. but I don't know what the second one is.

---

### Post by szenith on 2009-04-29
Actually, I just fixed this problem. I edited out the Ubuntu part in boot.ini, GRUB still works fine and I'm able to get into Ubuntu, I just got rid of that second boot screen.

---

