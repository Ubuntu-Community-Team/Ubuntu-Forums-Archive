---
title: "Formating a hard drive. What options?"
date: 2006-01-10
forum: General Help
---

### Post by MJSOnline on 2006-01-10
Hi all.

I want to format my 2nd hard drive to ext3, but the options below confusse me.

System > Admin > Disks > Select hard drive > Choose Format > Ext3 > then what?  /boot, mtn?  

What do they all mean?

What do I do?

Thanks.
Matthew

---

### Post by Leif on 2006-01-10
try using gparted

---

### Post by Red Knuckles on 2006-01-10
[QUOTE=Leif]try using gparted[/QUOTE]

For a noobie [just a few hours in Ubuntu and 9months in Linux] how do I create a partition or multiple partitions [It's a 320GB drive brand new] with gparted?:confused:

On mine the options to create a new, resize, etc are greyed out and inoperable. Which reminds me Ubuntu never asked me to create a root password [been using Fedora Core 4 on another drive] and I'm unable to become root in terminal using 'su' or su -'. Hmmm...

---

### Post by Leif on 2006-01-11
the problem may be that you're running from the harddisk partition you want to edit, and linux won't let you do that quite that easily. if you have the livecd, you could boot using that and then do the formatting. or download something like knoppix, which comes with disk editing tools by default.

once you've created the partition, you'll have to edit /etc/fstab to mount it. if you want help with that, let me know when you get to that point.

as for root, see [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

