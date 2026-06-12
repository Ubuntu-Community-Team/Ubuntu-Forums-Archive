---
title: "GParted questions/issues."
date: 2006-05-04
forum: Desktop Environments
---

### Post by tht00 on 2006-05-04
I'm running Dapper, but I'll put this here as it isn't really (or shouldn't be) a Dapper-related.

When running GParted from the terminal, this is printed in the terminal:
```
Error: Unable to open /dev/hdc - unrecognised disk label.
Warning: Unable to open /dev/hdc read-write (Read-only file system).  /dev/hdc has been opened read-only.
```

I can't resize the partition when it's mounted, though it can see how full it is.  Unmounted, the option becomes available, but I can't actually change anything (buttons on the dialog are locked), so it seems related to it being opened read-only.  Also, unmounted, I can no longer see how full the drive is (where on my other hard drive, this isn't the case.

Here's my fdisk output:
```
Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9726    78124063+  83  Linux
/dev/hdb2            9727       19929    81955597+   f  W95 Ext'd (LBA)
/dev/hdb5            9727       19674    79907278+   b  W95 FAT32
/dev/hdb6           19675       19929     2048256   82  Linux swap / Solaris

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         829     6658911    b  W95 FAT32
/dev/sda2             830        4865    32419170    f  W95 Ext'd (LBA)
/dev/sda5             830        4865    32419138+   b  W95 FAT32

```

Thoughts? Fixes?

Thanks,
Tom

---

### Post by dpm on 2006-05-04
If you post your /etc/fstab file people will have some more information to help you.

---

### Post by tht00 on 2006-05-04
Oh, and it's the hdb5 partition in particular I'm trying to resize.

fstab attached.

---

### Post by louis_nichols on 2006-05-04
What exact command are you using to open gparted? One reason for not leting you change partitions might be that you don't open it with root privileges.

Beside that, the console output is puzzling. /dev/hdc is actually a cd-romm drive. Are you trying to change /dev/hdb or /dev/sda ?

---

### Post by tht00 on 2006-05-04
[QUOTE=louis_nichols]What exact command are you using to open gparted? One reason for not leting you change partitions might be that you don't open it with root privileges.

Beside that, the console output is puzzling. /dev/hdc is actually a cd-romm drive. Are you trying to change /dev/hdb or /dev/sda ?[/QUOTE]

I open it using 'sudo gparted', and I'm trying to edit /dev/hdb5 -- the other partitions seem to want to cooperate... it would have let me change the size of the swap partition, also on hdb.

I had a DVD in the drive, and the error went away when that was removed... I figured it may have been related... guess not.

Here's some screenshots... maybe this will clear it up:
Screenshot 1:
/dev/hdb5 not mounted, started up gparted, and listed the properties of hdb5.  There is an error there I failed to mention.
"Unable to read the contents of this filesystem!  Because of this some operations may be unavailable. Did you install the correct plugin for this filesystem?"

It is a fat32 drive, ~75 GB.  The FAT partitions on my other hard drive doesn't have this problem, though, they are smaller.

Screenshot 2:
Resize/Move dialog.  All the controls are locked.  Not much to see.

Screenshot 3:
When I mount the hdb5 partition and refresh gparted, the error goes away... but, of course, I can't do anything to it while it's mounted, which brings me back to unmounting it and I'm back to where I was in the first screenshot.

---

### Post by louis_nichols on 2006-05-04
hm... :-k I haven't used gparted all that much, so please excuse me if my suggestions ar just that and everything might be a matter of trial and error.

I'm thinking, since you want to change the partition table on the same drive where your Linux is running from, this might be the reason. If so, the solution is to do all this froma  LiveCD of somekind. The web is full of them.

---

### Post by tht00 on 2006-05-04
[QUOTE=louis_nichols]hm... :-k I haven't used gparted all that much, so please excuse me if my suggestions ar just that and everything might be a matter of trial and error.

I'm thinking, since you want to change the partition table on the same drive where your Linux is running from, this might be the reason. If so, the solution is to do all this froma  LiveCD of somekind. The web is full of them.[/QUOTE]

Ok. I thought about doing that, and I think I'll try it...though..  I don't think that being on the same drive is the issue, as it let me unmount my swap partition next that one, and it would let me resize it.

Hopefully it'll bypass any problems I'm having here.

---

### Post by tht00 on 2006-05-04
Unfortunently, I've got the same thing... though, the Ubuntu Beta LiveCD looks nice. :D 

I might be able to get by without having to resize that partition... though I'm now curious as to why this is happening, so I know how to handle it later on.

Does anyone know if the gparted 'format' feature destroys the data on the partition, or does it convert the partition, attempting to preserve data?  (I'm assuming the former, but just wondering.)

Oh, and interestingly... my /dev/sda5 partition (also FAT32) is acting up now as well on this liveCD... but the /dev/sda1 partition seems to be fine (which is another FAT32 partition).

Any ideas why gparted is discriminating against 2 out of 3 FAT32 partitions?  The only thing the 2 have in common is that they lay in the 'extended' area of the hard drive, whatever that means.  The only other difference is size.  The little one (~6 gigs) is recognized.  The others (~31 and ~76GB) aren't.

---

### Post by louis_nichols on 2006-05-04
Sorry, dude, I'm in the dark here. Out of ideas. I've run into similar problems before. the lesson I learned was: if a tool don't work, try another one. :)

I can see why you're curious about why this is happening, but I don't really think there is a way to find out. This is really deep stuff, partitions and filesstems.

The last resort would be to just do a tar backup of everything and re-partition and re-format everything, with the desired dimensions.

Oh! And, the greatest thing: [LVM]("http://www.tldp.org/HOWTO/LVM-HOWTO/index.html") I use it and it's fantastic! resizing partitions (well.. equivalents) becomes just a matter of entering 2 commands in terminal, without even unmounting anything. Doesn't run on winblows though.

---

