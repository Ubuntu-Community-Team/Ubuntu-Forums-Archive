---
title: "dosfsck on startup."
date: 2006-07-29
forum: Desktop Environments
---

### Post by Blazeix on 2006-07-29
Hi. I have ubuntu installed and I'm trying to speed up the boot time. I've followed a very good how-to on this forum and it worked well. The only problem I'm having is that dosfsck runs on every single boot. Is it supposed to do that, and can I make it so it runs on every 30 mounts or something, like the normal fsck?

Upon bootup, my system pauses for maybe 10 to 15 seconds on the following line:
```
dosfsck 2.11 12 Mar 2005 Fat32 LFN
```
Thanks for any help!

---

### Post by Tiede on 2006-08-04
Well, Blazeix, I just reinstalled ubuntu and it just has that option by default for me. Every boot, the usplash drops to a terminal with the dosfsck bit...
Anyone has a fix?
I understand it is because fsck is checking every filesystems, but couldn't it be either integrated in usplash or packaged with the normal rootfs check that happens usually after 30 mounts?
I think it's odd that it is happening on a system I have not yet tweaked yet. At least now I don't have to blame myself for my mishaps...

---

### Post by Tiede on 2006-08-05
I wanna point out that the problem is happening with me on a "brand new" linux install. I am finding it somewhat odd to have that problem so early, and think it a very bad impression for any new ubuntu users to come. Seriously, no one has a fix for it?
I went to launchpad to see if there was something related to this problem, what I found was a [ wishlist ](https://launchpad.net/distros/ubuntu/+source/usplash/+bug/38303)for usplash to display some type of progress bar when checking filesystems... Understandably, the drop back to the console is not being viewed as a bug, but a feature.

---

### Post by Blazeix on 2006-08-08
Well, I found a temporary fix. Ubuntu automatically tries to mount every file system it finds, so I removed my windows partitions from etc/fstab. I'll just mount them when I need them, and Ubuntu no longer runs dosfsck on each startup.

---

### Post by Tiede on 2006-08-09
Unfortunately, this won't work for me. I have many documents that I access everytime I am on ubuntu from my windows  partition. My music, my pictures, my office docs, all of 'em are shared between the two, and since I didn't wanna have to download a ext3 bulky program to read my files on windows, I have all my files on a FAT32 partition...

---

### Post by PacShady on 2006-08-17
I'm also looking to turn off this dosfsck thing, which is rather irritating. I have quite a large FAT32 drive that's scanned every startup, which I need enabled constantly so manually mounting when needed isn't an option (for starters, my Firefox/Thunderbird profiles are on there, as are all my main working files). Any ideas?

'Shady

---

### Post by shdgrao on 2006-08-25
Hi. In the /etc/fstab file, change the "1" at the end of each line for "0", in the partitions that you want to escape the check.

---

### Post by kopinux on 2006-08-25
i also changed the fstab's to ubuntuguides one [ubuntuguide]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

it also says '0'

---

### Post by ampop on 2006-09-14
> **shdgrao said:**
> Hi. In the /etc/fstab file, change the "1" at the end of each line for "0", in the partitions that you want to escape the check.

It worked. Thank you.

---

### Post by nikhilk on 2006-09-14
As shdgrao mentioned, edit your /etc/fstab file and change the '1' at the end of each line of your vfat partition to 0.

---

