---
title: "[SOLVED] Install linux with old breezy live cd, please help!"
date: 2008-12-06
forum: General Help
---

### Post by badhorsie on 2008-12-06
Hi, i had an electrical problem and my windows instalation in one of my hard disks does not boot, so i ran Ubuntu 5.10 breezy live CD to recovery my hardisk, i want to format it and install the latest ubuntu on it, but my problem is that i cannot burn cds on a live session (i tried but i think its not possible since i have only one dvd drive), so i came out with another idea. I had another empty unpartitioned hard disk so i formatted a piece of it to FAT32. I dont have windows installation CD nor boot disk nor floppy drive or anything, the only thing i have is an Ubuntu breezy live CD (i dont have the installation CD).

 Can I install a linux distribution (any) on that unpartitiones hard disk FROM the live sesion so that i reboot the PC and starts from that HD? Then i could burn the DVD. Is this possible? Obviously i have an internet connection and i can download things. Thanks

---

### Post by badhorsie on 2008-12-06
sorry it duplicated..

---

### Post by badhorsie on 2008-12-07
anyone?.. please

---

### Post by CatKiller on 2008-12-07
[This page]("https://help.ubuntu.com/community/Installation/FromLinux") might have information that will help you. You should be able to use the Breezy live cd as your environment to download a Hardy (8.04.1 LTS) or Intrepid (8.10) iso file to use for the installation.

[This one]("https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet") might also be useful. I'm not entirely sure how one installs GRUB to the hard drive from the Breezy Live cd, but it's certain to be possible.

Failing that, you can get cds sent to you, or buy them to get them quicker, or download and burn the iso on another machine. You might also find that there's a Linux magazine that has an install cd on.

I hadn't realised quite how much of a step forward combining the live and install cds was until I thought about your problem.

Good luck!

---

### Post by glotz on 2008-12-07
You could also try running the LiveCD with toram kernel parameter to free the disk drive. Don't remember if breezy came with a dvd burning software.

---

### Post by oldos2er on 2008-12-07
Use unetbootin.

---

### Post by badhorsie on 2008-12-11
Well, i finally found a solution..

-First i tried to install untebootin, but since it asked me to reboot my computer (on a live session) that was not possible

-Then i tried to do an installation via Netboot: I installed GRUB on the hard disk, then copied de linux and initrd.gz files from the intrepid distro on the /boot directory, booted muy computer, loaded the files and typed "boot", it worked.

I tried like 10 times to download the files ,but no matter which server i selected there was always some package taht couldn,t be downloaded, or a 404 or a weird network error. This was very stressful for me, i tried for a week and i felt like grabbing a hammer and smashing the monitor. :lolflag: 

-Copied the contents of the live cd and the images, did the same as above but it didn't worked, i got some kernel panic error. Though im sure that i could download de ubuntu distro .iso and make it work, but i didnt tried (below) 

-Finally a copuple of hours ago a found buried in pile of old dusty cds, the installation cd that some years ago got shipped. Finally a could install linux on my hard disk.. what a relief

Thank you very much guys, though i installed with a installation cd, i learne a lot about linux a shell scripting triying to do the netboot install (technichally i was succesful in this point but some servers or my crappy 256k internet connection failed me).  Cheers

---

