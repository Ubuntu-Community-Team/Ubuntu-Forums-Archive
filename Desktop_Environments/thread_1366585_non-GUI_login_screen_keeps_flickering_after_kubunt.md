---
title: "non-GUI login screen keeps flickering after kubuntu splash"
date: 2009-12-28
forum: Desktop Environments
---

### Post by virtualexplorer on 2009-12-28
Hi,

I have Ubuntu 9.10 installed as dual boot system with windows xp. I used it for nearly 2 months, it was working good. Today I just happen to mess with the driver files in order to learn something myself. I downloaded the via chipset driver .tgz file from the via website and tried installing the drivers for the graphic. It did give some errors while installing but I continued installing. It asked me to reboot the system. I rebooted, I got the GRUB where I selected Linux(windows is working alright at the moment). When Linux tries to load, first the KUBUNTU splash screen with its loading bard appears and then a Text based login screen appears with the name of my computer example- **x's Login:**

and this keeps flickering. I am not able to access the login manager and the OS. If i try to boot using live cd...m not able to mount my linux partition and access in order to edit anythng. I guess this is something related to XServer. 

Plz some one help me either rollback to previous driver if possible or help me fix this problem.

Thanks

---

### Post by Howie Spitz on 2009-12-28
Have you tried to boot a (Recovery Mode) selection from GRUB?
Or just used the text based session to login as your regular user?

---

### Post by virtualexplorer on 2009-12-29
In my grub, I have only two options that are windows and linux. The others I had removed becoz there are other ppl in my family who use the computer and they often get confused which one to select. So I had removed the recovery mode option from the grub. I never login from text mode... It takes me to GUI login screen, but rite now it shows me a login screen of my computer name and it keeps flickering. m not able to type anythng there.

When I press Esc key m able to goto text based login screen and able to login to my id there. at non-GUI.

---

### Post by virtualexplorer on 2009-12-29
Well, my problem is SOLVED. I booted from live cd and mounted my linux partition on to it. I deleted the xorg.conf file from /etc/X11/ and rebooted the system without the live cd and it worked. :)

---

