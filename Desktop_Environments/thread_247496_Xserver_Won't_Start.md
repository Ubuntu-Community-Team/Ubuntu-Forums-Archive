---
title: "Xserver Won't Start"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Paul41 on 2006-08-30
I am having a problem with my Xserver starting with the 2.6.12-26-686 Kernel.  Everything was working fine until last night when I started getting errors.  I had installed the Kubuntu-desktop and tried it for a while then removed it.  After I removed it Kubuntu was still showing up when I booted so I reinstalled the kernel and that fixed that problem, but caused an Xserver problem.  I was initially getting the following error:
> Error locking authority file /home/psanders1/.Xauthority
I checked and the file was owned by root so I changed the owner to me.  After I did that I started getting this error:
> fatal server error:
no screens found
XIO: fatal IO error 104 (connection reset by peer) on Xserver ":0.0"
after 0 requests (0 known processed) with 0 events remaining
I have tried to go back to an old version of the xserver because I know that was a problem, but I still have the same problem.  I also tried to switch to run-level 3 to see if that helped, but once agiain I still had the same problem.  I just tried to remove the 2.6.12-26-686 Kernel then reinstall it to see if that made any difference but no luck.

I am able to boot with the 2.6.12-25-656 Kernel fine so I am very confused now as to what is happening.

---

### Post by s_groening on 2006-08-31
Did you by any chance install the update for 'xserver-xorg' at the point when you encountered the problem?

Try booting into rescue mode by pressing 'esc' at the very beginning of your machine's boot process to access the Grub menu and choosing the recovery mode for your kernel.

Type in your root password when asked and you'll log in as root.

run: 

[FONT="Courier New"]apt-get update && apt-get dist-upgrade[/FONT]

If errors are returned, try running:

[FONT="Courier New"]apt-get -f install[/FONT]

...which should in turn cure the decease :)

---

### Post by Paul41 on 2006-08-31
I did not install any upgrades to 'xserver-xorg' before the problem started.  

I will try your suggestion as soon as I can.  Lightning took out my cable at home (and therefore my internet) last night and they are saying it probably be tomorrow before they can get it back on :mad:

---

### Post by Paul41 on 2006-08-31
apt-get update && apt-get dist-upgrade didn't update or download any packages.  It also did not return any errors.  I tried to run apt-get -f install anyway and it also did not download or update anything.

So the problem is still there.  X starts fine with the 2.6.12-25-686 Kernel, but not the 2.6.12-26-686 Kernel.  Any more ideas?

---

### Post by Paul41 on 2006-08-31
Anyone?

---

### Post by Paul41 on 2006-09-06
I have now tried to reinstall the dependency files, but that didn't work either.  Can anyone think of anything else I could try.  I am running out of ideas.

---

### Post by Paul41 on 2006-09-14
Now I tried to reconfigure Xserver with sudo dpkg-reconfigure xserver-xorg. I didn't figure this would make a difference since X works fine with the 2.6.12-25-686 Kernel, but I tried anyway.  Turns out I was right, the 2.6.12-26-686 Kernel still won't work with X. ](*,)

---

### Post by TSP on 2006-09-14
Wich error did you get? check the Xlog and post it here

---

### Post by Paul41 on 2006-09-14
Do you know the location of the log?

---

### Post by Paul41 on 2006-09-14
Is this the log you need to see?

---

### Post by Paul41 on 2006-09-15
Sorry, for some reason the log didn't attach to my last post.

---

### Post by Paul41 on 2006-09-15
After seeing this line is the log
> (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
I tried to reinstall nvidia-kernel-common but still no luck.

---

### Post by Paul41 on 2006-09-18
I just got a update for the Linux kernel and the new kernel is having the same problem.  So the 2.6.12-25-686 kernel is still the only one that will boot.

---

### Post by Paul41 on 2006-09-18
I just tried to install the 386 kernel to see what would happen and X won't start with it either.  I am able to use the computer fine, but this problem is still getting very anoying!

---

### Post by nbound on 2006-09-18
I was having the same problem, reinstalled nvidia driver like im meant to after kernel upgrade first time and it didnt work... yet strangely i tried it again and it did (using new kernel now) - the only thing that i did different was extract installer to a different folder. :confused:

---

### Post by Paul41 on 2006-09-18
OK it is working now.  I went to try to reinstall the Nvidia driver again and noticed that linux-restriced-modules-2.6.15-25-686 was installed, but the restricted modules were not installed for the other kernels.  I installed them and that fixed the problem.  :D

---

### Post by nbound on 2006-09-19
hmmm strange... ive removed the restricted modules on my PC because they interfere with the nvidia driver (the one from nvidia themselves). :confused:

---

