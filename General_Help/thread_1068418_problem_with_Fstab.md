---
title: "problem with Fstab"
date: 2009-02-12
forum: General Help
---

### Post by Arminius on 2009-02-12
ok I have an external usb drive called ext backup1
and I must not have unmounted it from xp right before I made the switch to ubuntu, cause ubuntu keeps saying cannot mount volume, I've been lead to belive that if I manually edit the fstab and enter it in it will solve the problem?

here is what my fstab looked like before changes
"# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d98c10f7-a7de-471a-a784-dcc81f568bab /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9d4ece89-85d9-4e2b-a003-cc082d34839e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0"

and at the very end after the cdrom I put

# /dev/sdc1
UUID=4C14CB3514CB20B6           NTFS

at which point the usb icon vanishes completely, and will only reappear when u delete the entry I made, so what am I doing wrong?

---

### Post by dcstar on 2009-02-12
> **Arminius said:**
> ok I have an external usb drive called ext backup1
and I must not have unmounted it from xp right before I made the switch to ubuntu, cause ubuntu keeps saying cannot mount volume, I've been lead to belive that if I manually edit the fstab and enter it in it will solve the problem?
.........

You should not need to put external drives in fstab, they are mounted automatically by the system.

If Ubuntu cannot mount it, then do a fsck on it as it is probably marked as a "dirty" filesystem due to a previous incorrectly performed unmount:

```
sudo fsck -y /dev/whatever-your-drive-is
```

---

### Post by Arminius on 2009-02-12
ok I typed sudo fsck -y /dev/Ext Backup1

and I got 
fsck 1.41.3 (12-Oct-2008)
Usage: fsck.ext2 [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list

then it returned me to where I was at the start, and my usb still won't mount? I tried using -p instead, still nothing? so anything else?

---

### Post by 2hot6ft2 on 2009-02-12
> **Arminius said:**
> ok I have an external usb drive called ext backup1
and I must not have unmounted it from xp right before I made the switch to ubuntu, cause ubuntu keeps saying cannot mount volume, I've been lead to belive that if I manually edit the fstab and enter it in it will solve the problem?

here is what my fstab looked like before changes
"# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d98c10f7-a7de-471a-a784-dcc81f568bab /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9d4ece89-85d9-4e2b-a003-cc082d34839e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0"

and at the very end after the cdrom I put

# /dev/sdc1
UUID=4C14CB3514CB20B6           NTFS

at which point the usb icon vanishes completely, and will only reappear when u delete the entry I made, so what am I doing wrong?
Well, first thing I see is this "an external usb drive called [COLOR="Blue"]ext backup1[/COLOR]" spaces should not be used in volume names otherwise you'll have problems instead try using either a dash or an underscore"-_".

Next is: "I must not have unmounted it from xp right". Best thing to do is plug it into a windows pc and change the volume name while you're at it and unmount it using the "Safely Remove Hardware" feature.

Third I would suggest using the ntfs-config tool to add it to the fstab file then edit the file and add the UUID if you so desire. You can install ntfs-config with
```
sudo apt-get install ntfs-config
```
then it will be in
Applications>System Tools>NTFS-Configuration Tool

Make sure the drive you want to auto mount is UNMOUNTED then open up the NTFS-Configuration Tool then select the drive you want and click Apply in the next window select enable write support for which ever it is (internal or external) and click OK. All done

Now it will auto mount with read/write support after you reboot.

That should fix you up.

---

### Post by punx45 on 2009-02-12
it wont be listed with the volume label in /dev.   since it is a usb disk, it will be sda, sdb, etc, depending on what else is there.    so try that.

---

### Post by dcstar on 2009-02-12
> **Arminius said:**
> ok I typed sudo fsck -y /dev/Ext Backup1

and I got 
.......
then it returned me to where I was at the start, and my usb still won't mount? I tried using -p instead, still nothing? so anything else?

Ok, install the **ntfsprogs** package and then use the **ntfsfix** utility on the drive instead of fsck.

---

### Post by Arminius on 2009-02-13
> Next is: "I must not have unmounted it from xp right". Best thing to do is plug it into a windows pc and change the volume name while you're at it and unmount it using the "Safely Remove Hardware" feature

thanks 2hot6ft2 that worked perfectly, it's still BS that ubuntu can't easily make it it's own, I had to waste time setting xp up on another drive.

---

### Post by Neural oD on 2009-02-13
you could have used: sudo ntfsmount device mount_point -o force

---

### Post by jerome1232 on 2009-02-13
> **Arminius said:**
> thanks 2hot6ft2 that worked perfectly, it's still BS that ubuntu can't easily make it it's own, I had to waste time setting xp up on another drive.

lol, it's bs that Linux had problems with a closed source microsoft file system?

Well truth be told there are two ways to deal with that from ubuntu, install ntfsprogs and run ntfsfix on the drive or just force the mount. The reason Ubuntu doesn't do this by default is probably because someone decided it's best to not attempt mounting a file system that could be dirty or damaged, especially since we have no tools that can do much in the way of repairing a ntfs disk, ntfsfix has very limited capabilities in repairing nt file systems.

---

