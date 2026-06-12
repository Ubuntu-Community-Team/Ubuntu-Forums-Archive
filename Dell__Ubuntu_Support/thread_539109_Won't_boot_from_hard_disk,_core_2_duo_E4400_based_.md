---
title: "Won't boot from hard disk, core 2 duo E4400 based system"
date: 2007-08-30
forum: Dell  Ubuntu Support
---

### Post by u12345 on 2007-08-30
I have a new core 2 duo e4400 based system from Dell. I installed ubuntu 7.04 server version, install went through fine but it won't boot from the hard disk. I see the "Grub message, countdown" and then it just stays blank. If I use the repair option in the install menu, I can open a shell, change the password, look at the directories, etc. I was also able to re-install Grub to (hd0) but this did not help in booting from the hard disk. I tried the desktop version 7.04 but this seems to boot fine from the CD but then won't allow me to login as it keeps saying session timed out. It does not seem to recognize the login on the hard disk. 

Appreciate any info on how to get over this problem.

---

### Post by Kubunteando on 2007-09-01
Have you tried the Live CD?

This will check whether the kernel is running fine on your machine.

There has been several kernel updates in Feisty after the CDs were released, so one try can be to boot in "recovery mode" and update Feisty from the shell.

With connection to the Internet issue:

- sudo apt-get update
- sudo apt-get upgrade

This should download and install all the updates from the repositories, including the kernel updates.

Once finished, reboot and check how it goes.

---

