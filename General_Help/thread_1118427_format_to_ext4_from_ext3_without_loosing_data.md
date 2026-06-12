---
title: "format to ext4 from ext3 without loosing data?"
date: 2009-04-07
forum: General Help
---

### Post by sansa dude on 2009-04-07
I'm running Ubuntu 9.04 beta and want to take advantage of the speed increase but I'm still on ext3 so is there some sort of way i can format to ext4 without loosing all my data? Or will i have to copy everything to an other disk and just copy it all back once it is formated?

---

### Post by Tim Sharitt on 2009-04-07
Short answer: You will probably be better off backing up your data and starting with a fresh ext4 filesystem.

Now for the long answer. It is technically possible to update an existing ext2 or ext3 filesystem to ext4.

To change an ext2 files system to ext3

(Replace /dev/sdXY with the block device you are working with)
```
tune2fs -j /dev/sdXY
```

To change from ext3 to ext4
```
tune2fs -O extents,uninit_bg,dir_index /dev/sdXY
```

After running that command you'll need to run e2fsck to fix some of the disk structure which tune2fs has modified
```
e2fsck -fD /dev/sdXY
```

After doing this new files will be created with ext4's extents format, but existing files will remain unchanged.

I have also heard that resize2fs can corrupt file systems which have been converted.

Edit: I should also note that once you go through with these steps, you will no longer be able to mount the file system as ext3.

---

### Post by epswinde on 2009-04-07
As far as I know, any reformat will cause data loss.  I have not used ext4, but this is true for ext2/ext3.  If you're really hell bent on using ext4, then your best bet is to back everything up, reformat, and then restore the partition from your backup.

Hope this helps.

edit: you can safely ignore this message, I seem to have posted just after Tim (above), and he knows more than I do about this.  I would, however, still recommend backing up your data before doing any file system alterations.

---

### Post by Tim Sharitt on 2009-04-07
> **epswinde said:**
> 
edit: you can safely ignore this message, I seem to have posted just after Tim (above), and he knows more than I do about this.  I would, however, still recommend backing up your data before doing any file system alterations.

Yes, backing up your data is a good bet which ever way you go :P

---

