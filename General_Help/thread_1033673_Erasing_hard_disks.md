---
title: "Erasing hard disks"
date: 2009-01-07
forum: General Help
---

### Post by 3pinner on 2009-01-07
I have a couple of older hard drives I want to erase, then reformat for future use.
Any good products available for this in the repositories?

Can I just use shred; and if so what would be the command to erase an entire drive (and not that's running Ubuntu!)

Thanks!

---

### Post by bc90021 on 2009-01-07
BE CAREFUL IF YOU FOLLOW THE BELOW ADVICE.  PLEASE MAKE SURE TO DOUBLE CHECK THE DRIVE YOU ARE OPERATING ON.

If you boot from a Linux CD, or can attach the drive to a machine which is running Ubuntu, you can use DD.

An example of this would be (if the drive you want to completely erase is /dev/sdb):

dd if=/dev/zero of=/dev/sdb

This says to copy all zeroes to that drive.  That will essentially set the drive to factory default, erasing all partitions and data.

Again, MAKE SURE YOU GET THE RIGHT DRIVE.  The command "sudo fdisk -l" can list the drives that are connected to your machine.

---

### Post by donkyhotay on 2009-01-07
> **bc90021 said:**
> BE CAREFUL IF YOU FOLLOW THE BELOW ADVICE.  PLEASE MAKE SURE TO DOUBLE CHECK THE DRIVE YOU ARE OPERATING ON.

If you boot from a Linux CD, or can attach the drive to a machine which is running Ubuntu, you can use DD.

An example of this would be (if the drive you want to completely erase is /dev/sdb):

dd if=/dev/zero of=/dev/sdb

This says to copy all zeroes to that drive.  That will essentially set the drive to factory default, erasing all partitions and data.

Again, MAKE SURE YOU GET THE RIGHT DRIVE.  The command "sudo fdisk -l" can list the drives that are connected to your machine.

This will prevent almost anyone from reading the drive, however it is still possible to be read with special forensic tools used by certain government agencies. If you are absolutely paranoid about someone reading your drive will want to actually run
```
dd if=/dev/urandom of=/dev/sda
```
about 5 times or so and then run
```
dd if=/dev/zero of=/dev/sdb
```
to wipe the drive (this is what my local linux computer recycling center does).

//edit: DO NOT RUN THE ABOVE CODE UNLESS YOU KNOW WHAT YOU'RE DOING AND ARE CERTAIN YOU HAVE THE RIGHT DRIVE SELECTED, IT *WILL* WIPE OUT ALL YOUR DATA.

---

### Post by bullium on 2009-01-07
Darik's Boot And Nuke. [http://www.dban.org/](http://www.dban.org/) I've been using it old drives for years and it does it's job perfectly.

---

### Post by dcstar on 2009-01-07
There is a package in the repositories just for this called **wipe**.

This is also worth reading: [http://blogs.zdnet.com/storage/?p=129](http://blogs.zdnet.com/storage/?p=129)

---

### Post by 3pinner on 2009-01-07
> **bullium said:**
> Darik's Boot And Nuke. [http://www.dban.org/](http://www.dban.org/) I've been using it old drives for years and it does it's job perfectly.

thank you all for the suggestions!
I looked at this product, and will download and use that. I have another old computer that has windows xp on it. I'll install my old drives in that and nuke 'em!
Thanks!

---

