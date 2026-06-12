---
title: "Uninstalling Kubuntu"
date: 2006-02-21
forum: Desktop Environments
---

### Post by Athean on 2006-02-21
Hey,

Don't get me wrong, I love kubuntu. It's been very useful to me for the time being, but due to business reasons I need to reinstall windows.

Unfortunately, I'm not a computer technician nor do I have much knowledge at all in partitions / reformats. I have an install disc for windows, but when i set it in, I get the following partition problem

"Partition size 1 not enough."

Take note I'm using an intel x86 2.4 GHZ, 256 mb ram, 40 GB hd computer.

What would be wrong with the partition? My guess is that it removed the operating system but not the partition data.

Therefore, my question is : How would i uninstall kubuntu and reinstall windows on this computer?

Sorry for bugging =P

---

### Post by sdr_ar on 2006-02-21
Hi. It seems that your problem is that your free disk space isn't enough to install Windows.
You are right, you uninstalled Kubuntu, but you didn't resized the partitions. The idea would be to use something like "fdisk" that comes with the "boot disk" of Windows, and eliminate the Linux partition ext2/3 and then resize the partition for Windows to fit all the disk.
Other idea would be to use the Kubuntu installer to manage your partitions, but not install Kubuntu. And I think that this is the easier one.
Contact me if you have any problem.

Regards

---

### Post by sdr_ar on 2006-02-21
Of course, using the Kubuntu installer you have to eliminate the Linux Partition, and the Linux Swap partition, and then resize the Windows partition. 

Contact me if you have any problem.

---

### Post by Athean on 2006-02-22
Sorry to bug again, but could you do this step by step? i have the kubuntu installer only so could you guide me through what to do? :(

---

### Post by sdr_ar on 2006-02-25
Well, first of all, set up your pc (in the BIOS) to boot from CD. Put the Kubuntu installer CD into de drive and reboot.
Then, when the installer starts, continue with the steps until the step in wich that the installer asks you to manage (or set) your partitions. 
Well, first of all, select the linux (ext2 or ext3 file system) and select the erase (or delete, I don't remember how it is exactly) button. Then do the same with de Linux Swap partition. Then, select the Windows partition and resize it to take all the free disk space. At last, accept all the changes, and next reboot the pc (don't continue with the steps of the installer), enter in the BIOS, configure your pc to boot from your hard disk, take off the Installer CD, and reboot.
Any question, ask me.
Regards.

---

