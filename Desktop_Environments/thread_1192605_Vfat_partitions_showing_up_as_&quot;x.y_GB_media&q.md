---
title: "Vfat partitions showing up as &quot;x.y GB media&quot; despite volume labels being set [9.04]"
date: 2009-06-20
forum: Desktop Environments
---

### Post by Fafnir on 2009-06-20
I've recently installed Jaunty on a new computer and am having problems getting the labels of a couple of old FAT32 partitions to display correctly. Here's my /etc/fstab:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults                          0  0  
# / was on /dev/sda1 during installation
UUID=0fe06c8b-c4ad-49f8-8ce2-e9229fbe5ad3  /                 ext3         relatime,errors=remount-ro        0  1  
# /home was on /dev/sda3 during installation
UUID=322eb190-d71a-4627-afda-a328e3d3e6aa  /home             ext3         relatime                          0  2  
# swap was on /dev/sda2 during installation
UUID=1b30ecb2-5b4f-48d1-8259-ecc40f3233c0  none              swap         sw                                0  0  
# swap was on /dev/sdb6 during installation
UUID=06ee4e1c-abe7-4914-a27b-5865e5c3238f  none              swap         sw                                0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8             0  0  
/dev/fd0                                   /media/floppy0    auto         rw,user,noauto,exec,utf8          0  0  
/dev/sdb1                                  /media/oldwin     vfat         users                             0  0  
/dev/sdb3                                  /media/oldbuntu   ext3         errors=remount-ro,user            0  0  
/dev/sdb4                                  /media/windows    ntfs         nls=iso8859-1,ro,users,umask=000  0  0  
/dev/sdb5                                  /media/data       vfat         users                             0  0  
/dev/sdc1                                  /media/SEAGATE    vfat         users,user                        0  0  
/dev/sdc2                                  /media/encrypted  crypt_LUKS   noauto,owner                      0  0  

```

The devices I'm having problems with are /dev/sdb1 and /dev/sdb5. They each automount fine on boot, but show up on the desktop and in the Nautilus Places menu as "30.0 GB Media" rather than "oldwin" and "data". This obviously causes some confusion between the two. This happened with Hardy as well on my old installation/computer, and I'd quite like to kill it now if possible while I've got a fresh installation to play around with.

The two partitions show up in Nautilus with the correct labels when I start it with root privileges by typing "gksudo nautilus" in the terminal. Bizarrely, they **don't** show up in Nautilus correctly if I login as root via the GUI and start Nautilus normally.

What I've tried:

- Relabelling the volumes with mtools to oldwin and data respectively. The relabelling goes through without errors and mlabel -s returns the right labels, but they're still displayed as 30.0 GB Media.

- Chowning and chgrping /dev/sdb1 and /dev/sdb5 to my account. This has no effect on the volume labels displayed (even on unmounting and remounting), and when I restart the computer the ownerships revert to root. Gksudo nautilus gives me the correct labels even when the volumes are owned by me.

I really haven't found any guidance on what to do when the label is valid but Nautilus decides to ignore it - any chance of a hint?

Thanks in advance!

---

### Post by ajgreeny on 2009-06-20
Try labeling the partitions with gparted.  It has always worked for me on fat32 or ntfs partitions, though I just use tune2fs for ext3 partitions.  There are similar cli utilities to tune2fs for both fat32 and ntfs partitions, but I haven't bothered to look into them.

---

### Post by Fafnir on 2009-06-20
I've already tried changing the partition labels - mtools does for vfat what tune2fs does for ext3. Going in in gparted, /dev/sdb1 and /dev/sdb5 are indeed labelled oldwin and data as desired. Changing the label in gparted doesn't help either, so it's not a defect in mtools.

tl;dr: I already labelled the partitions, but Nautilus is ignoring the labels for some reason unless I run it as root.

---

