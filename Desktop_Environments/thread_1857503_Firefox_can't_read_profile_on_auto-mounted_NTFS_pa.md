---
title: "Firefox can't read profile on auto-mounted NTFS partition"
date: 2011-10-10
forum: Desktop Environments
---

### Post by RMOP on 2011-10-10
Weird, but that's all I can figure. See my extended solilquy on "Firefox .parentlock not deleted" for background. I thought I had this licked.

When I auto-mount the NTFS data partition on which my (shared) Firefox Profile is stored, FF seems unable to access the partition. If I remove the lines in /etc/fstab to disable auto-mounting, I can then (upon reboot) manually mount the partition via Nautilus before starting FF, and FF opens normally

What in my /etc/fstab would mount my partition so as to interfere with FF's ability to read the profile?

UUID=A04A69F04A69C41E	/media/NTFS_Data	ntfs-3g	defaults,locale=en_US.UTF-8	0	0

FWIW: NTSF-Config placed the above line between the line which mounts my ext4 partition and the line which mounts my swap partition. ALSO, probably not of consequence is that the underscore "_" in the name of the folder is, in fact, a space. NTFS-Config used an underscore instead of a space when writing to /etc/fstab, but it does mount the partition.

---

### Post by lovinglinux on 2011-10-10
I am not sure, but is worth verifying if AppArmor is not preventing Firefox from accessing the shared partition. This is usually the case with similar setups.

I would also like to point that since Firefox 4, it has a built-in Sync feature that can synchronize bookmarks, passwords, tabs, history and settings. So unless you have a specific need like sharing extensions databases and files, I would recommend using sync.

---

### Post by RMOP on 2011-10-10
> **lovinglinux said:**
> I am not sure, but is worth verifying if AppArmor is not preventing Firefox from accessing the shared partition. This is usually the case with similar setups...

Thanks for the reply. Not familiar w AppArmor, and can't help but wonder how it would prevent FF from accessing the partition when it is auto-mounted but not when I manually mount it using Nautilus. In the present case, I'd rather solve the problem directly, if possible, than side-step it by using a FF feature I've not found necessary in the past.

---

### Post by RMOP on 2011-11-05
Well, a little trolling and I did finally find the answer. The partition has to be automounted so as to give USERS R/W ability, which is NOT the default. Here's the line that worked (thanks to the fstab entry in Ubuntu documentation):

UUID=A04B69F04A69D41D	/media/NTFS\040Data	ntfs-3g	auto,users,uid=1000,gid=100,dmask=027,fmask=137,UTF-8	0	0

I can unmount this as a user, and FF has R/W access as well, which solved the .parentlock problem (a red herring).

Adding the SPACE in the name via \040 was a nice touch, with thanks and credit going to:

[http://www.webmasterworld.com/forum40/674.htm](http://www.webmasterworld.com/forum40/674.htm)

---

