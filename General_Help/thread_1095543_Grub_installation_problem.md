---
title: "Grub installation problem"
date: 2009-03-13
forum: General Help
---

### Post by WhiteDragon4Ever on 2009-03-13
I have a comp with Windows XP on it and I would like to install grub as my boot loader. So i boot to a live cd of Ubuntu and then go to cmd line. I type sudo grub and now I'm in grub. I am trying to find my hd info with this command find /boot/grub/stage1 but i says File Not Found.

What I am trying to run is this command:

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

Grub has never been installed on this comp. So, it is a new install for grub. Any help would be nice.

---

### Post by circa82 on 2009-03-13
Do you have Ubuntu or another Linux distro installed on the hard drive already? If so, you'll first need to mount the 'root' partition of that install so that GRUB can be configured. That would be the reason you're getting the 'file not found' error. 

If you don't have Linux installed already; can you maybe explain a bit more cause I don't quite follow.

---

### Post by WhiteDragon4Ever on 2009-03-13
No, I do not have a linux distro installed at all. All i have is Win XP on my box. I need grub installed on it so that I can have it point to a hyper-visor (Xen) and I do not wan to use Windows boot loader.

I read in different areas that you should be able to do a grub install from a live cd of Ubuntu. So, that is what I am trying to do.

---

### Post by RedSingularity on 2009-03-13
Grub stage 1 cant be found because there is no stage 1.  You dont have a linux distro installed.  I am not sure if you can install grub on a windows only computer.

I suppose you can do the "root" and "setup" step.  Root (hd0,0)  Setup (hd0)

---

### Post by circa82 on 2009-03-13
Neither 'root' nor 'setup' would actually work since there is no 'root' directory and no stage1 or 1_5 files to 'setup'. 

WhiteDragon4Ever: Technically, there are two separate 'installs' for GRUB. The first install is actually installing the GRUB package itself and all it's configuration files. The second install is installing GRUB to the MBR or boot sector of a particular hard drive. That would be the 'root' and 'setup' commands. You're trying to setup GRUB without actually having it installed. 

I don't use XEN or any VM for that matter, so I'm not sure if there is a better solution. However; for GRUB to work you would need a small partition on the hard drive where you could install the GRUB package to. You could do that from a Live CD using GParted for partitioning and then using apt-get for the install. Then you could run 'find /boot/grub/stage1' and actually find it and run the 'root' and 'setup' commands.

---

### Post by WhiteDragon4Ever on 2009-03-13
Thank you guys for the info it has been helpful. How do you use apt-get to install grub?

---

