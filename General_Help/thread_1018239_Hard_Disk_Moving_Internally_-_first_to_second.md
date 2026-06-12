---
title: "Hard Disk Moving Internally - first to second"
date: 2008-12-21
forum: General Help
---

### Post by Fahim123 on 2008-12-21
Hi Guys,
  I need some help I have 160gb hard disk in that i have windows xp (40gb) and Ubuntu (40gb) i bought another 250gb hard disk (internall one) now i want to move only ubuntu from my 160gb to 250gb leaving the windows xp untouched and not to disturb the grub how to do this.

---

### Post by unutbu on 2008-12-21
Here is one way:

Install Ubuntu on the 250GB drive using a LiveCD. 

In step #6 "Migrate documents", the installer will give you the option to migrate your home account from Ubuntu (40GB) to the new drive.

In step #7, click the Advanced button and tell the installer to install GRUB on (hd1) also known as /dev/sdb, the 250GB drive). 
By doing this, you'll need to tell the BIOS to boot the second drive when you want to boot Ubuntu.

If you'd like to discuss more boot arrangement options, please answer the following questions:

[list]
[*]Do you plan on keeping Ubuntu or some Linux distro on the first hard drive?
[*]Are the two drives always going to be together? Do you care if booting relies on both drives being present? (and that the machine would not boot if one of the drives were removed).
[/list]

You could then re-download packages as you need them, or use this guide
[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)
to grab the packages from Ubuntu (40GB). 
Don't do this unless your new Ubuntu is the same version as your old Ubuntu.

If you use abhiroopb's method, you would boot the Ubuntu on the 40GB partition, mount the 250GB partition, substitute a directory on the 250GB drive for ~/dpkg-repack. That way, the packages will be created on the 250GB drive where you'll have more space. Then boot Ubuntu on the 250GB drive and install the packages.

By the way, now is a good opportunity to make one or two additional partitions: A separate home or data directory, and a back up partition of the same size as your data directory. The Ubuntu OS partition should fit comfortably in 20 GB.

---

### Post by Fahim123 on 2008-12-21
thank you verymuch Untubu i will first try it out.

---

