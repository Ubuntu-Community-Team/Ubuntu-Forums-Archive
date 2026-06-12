---
title: "Installing games with Steam on a NTFS partition in Ubuntu 14.04"
date: 2014-04-13
forum: Gaming &amp; Leisure
---

### Post by slovenskyweb on 2014-04-13
Is it possible to install games with Steam to a NTFS partition from an Ubuntu 14.04?

---

### Post by oldrocker99 on 2014-04-13
Yes, provided you mount the NTFS partition. Make a folder (Why not "Steam?") and then, within Steam, go to **View/Settings**. Under **Downloads**, you'll see **Content Libraries**, where you can use multiple drives.

I have my main Steam folder on a separate internal drive, and, until I click on that drive in a file manager, Steam doesn't see it. Once the system knows that the drive is there (that is, listed in /media/username/), which, as I said, can be added by clicking on its icon in a file manager, the pale "uninstalled" list in my Steam Library turn into "ready to play."

To mount other drives at startup, you'll have to learn how to edit the /etc/fstab file, which is another task entirely, and there are lots of tutorials on Ubuntuforums.org to help you do some under-the-hood work with your system. What I've advised will allow you to play with your Steam folder on an NTFS partition.

I would NOT mix Windows and Steam games in the same folder, BTW.

---

### Post by Ranko Kohime on 2014-04-14
You may run into some permissions issues using NTFS.  NTFS does not support *nix-style permissions, which may result in your games being non-executable.  I honestly haven't played with NTFS enough to know, though.

---

### Post by adgsfuzwe on 2015-01-25
I'm another user with the same problem. The solution is easy: You have  to mount a partition with "exec". I didn't wanted to change my old  partitions or the fstab-file, so I created a new partition with ext4.  BTW the old partition I used for Steam games was NTFS. I use Ubuntu  14.10 64-bit and the newest Steam. After I created a partition with the  GUI of gnome-disk-utility (a really great program [http://wiki.ubuntuusers.de/Laufwerksverwaltung](http://wiki.ubuntuusers.de/Laufwerksverwaltung)),  I clicked on the partition, then on these 2 circles, then on mounting  options edit, then in the first line I switched the button to OFF. There  is a line which contains "nosuid,nodev,nofail,noauto,x-gvfs-show", just  add ",exec" and click ok. Then use Steam.

---

