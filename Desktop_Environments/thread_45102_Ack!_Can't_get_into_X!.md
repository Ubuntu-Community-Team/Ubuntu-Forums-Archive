---
title: "Ack! Can't get into X!"
date: 2005-06-28
forum: Desktop Environments
---

### Post by hypersonic5 on 2005-06-28
Linux just froze while I was installing some updates using synaptic. I think I was installing the new Kernel update. Anyway, I had to hard reset it and when it booted back up I couldnt get X to start up so I could get into KDE. I tried to copy down the error message:

---------------------------------------

Fatal: model nvidia not found
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module
(EE) NVIDIA9)): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
No screens found

X10: fatal IO error 104 (connection reset by peer) on X Server ":0.0"
after 0 requests (0 known processed) with 0 events remaining

----------------------------------------


Does anybody have any idea how to fix this problem? I REALLY need to get back into my desktop because I have a lot of important files that I can't stand to lose. If anybody can help me, I will be eternally grateful

Thanks in advance,

~hyper

---

### Post by hypersonic5 on 2005-06-28
If it helps, my graphics card is an Nvidia Geforce FX 5900. My system is an nforce2 with an Athlon XP 3200+ and 1024 MB ram. If you need more info, ask me. I need to be able to startx and get back to using my computer normally ASAP.

---

### Post by supahfly on 2005-06-29
[QUOTE=hypersonic5]If it helps, my graphics card is an Nvidia Geforce FX 5900. My system is an nforce2 with an Athlon XP 3200+ and 1024 MB ram. If you need more info, ask me. I need to be able to startx and get back to using my computer normally ASAP.[/QUOTE]
 normally you have a backup of your xorg.cong when you installed your nvidia drivers ...
it is in /var/backups/xorg 
place it back in /etc/X11/xorg.conf 
I have the same problem, canot get nvidia drivers to work

---

### Post by jerrykenny on 2005-07-26
Hypersonic,   trouble is your nvidia module no longer fits your kernel ( since you've updated your kernel)

You should still have a pc working at the command line, so login as root and give the root password . . . . 

Then you have 2 options . . . 

1\    type       apt-get remove nvidia-glx           type yes at the prompts, this will remove the module, . . . . then reboot,  wait for all the failed X-server pallaver etc,  then login as root to the command line and type

                apt-get install nvidia-glx         once its done you should be able to restart x  with either the simple "gdm"   or "startx" commands.

2\  If above wont work,  login as root to the command line, type

             nano /etc/X11/xorg.conf

find the bit where your graphics chip driver is defined , it'll say "nvidia",   replace that with   "nv"     press   "Control  + X" simaultaneosluy,  and answer y to the prompts to save, and overwrite the existing file, and you can then start X (albeit without 3d support)

       Good Luck

---

### Post by charlieg on 2005-07-26
[QUOTE=jerrykenny]apt-get remove nvidia-glx . . . . then reboot[/QUOTE]
This isn't windows, you shouldn't have to reboot.  After upgrading the kernel, reinstalling the nvidia components should work, shoudn't it?

I guess I'm used to changing kernels + binary modules in Gentoo, where it's all determined by where /usr/src/linux points to.  I wouldn't have thought it'd be much different in Ubuntu.

---

### Post by jerrykenny on 2005-07-27
We seem to have lost hypersonic . . . . 

I reckon from previous experience (of being in exactly the same pickle) that the reboot is necessary . . . Baffled as to the ins and outs of why,  possibly suggest that when I tried (without rebooting) the original nvidia module was merely resurrected. . . .

---

