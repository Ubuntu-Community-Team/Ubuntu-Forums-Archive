---
title: "Samba Shares on Desktop"
date: 2006-07-03
forum: Desktop Environments
---

### Post by J0s3ph on 2006-07-03
Hello

I have two samba shares mounted in fstab but I'm not a great fan of the share icons.

[IMG]http://i61.photobucket.com/albums/h78/J03_photos/sambashares.png[/IMG]

The content of /etc/fstab is as follows...
Beginning==========
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2    /mnt/hda2-60gb ntfs  nls=utf8,umask=0222 0    0
/dev/hdb1    /mnt/hdb1-200gb ntfs  nls=utf8,umask=0222 0    0
192.168.1.101:/home/joseph /mnt/101-joseph nfs rw 0 0
//192.168.1.12/d /mnt/12-d smbfs username=Administrator,password=vanhalen,fmask=777,dmask=777 0 0
//192.168.1.12/e /mnt/12-e smbfs username=Administrator,password=vanhalen,fmask=777,dmask=777 0 0

End==========

Is there a way of preventing the samba share icons appearing on the desktop?

Thanks

---

### Post by Kilz on 2006-07-05
[QUOTE=J0s3ph]Hello

I have two samba shares mounted in fstab but I'm not a great fan of the share icons.

[IMG]http://i61.photobucket.com/albums/h78/J03_photos/sambashares.png[/IMG]

The content of /etc/fstab is as follows...
Beginning==========
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2    /mnt/hda2-60gb ntfs  nls=utf8,umask=0222 0    0
/dev/hdb1    /mnt/hdb1-200gb ntfs  nls=utf8,umask=0222 0    0
192.168.1.101:/home/joseph /mnt/101-joseph nfs rw 0 0
//192.168.1.12/d /mnt/12-d smbfs username=Administrator,password=vanhalen,fmask=777,dmask=777 0 0
//192.168.1.12/e /mnt/12-e smbfs username=Administrator,password=vanhalen,fmask=777,dmask=777 0 0

End==========

Is there a way of preventing the samba share icons appearing on the desktop?

Thanks[/QUOTE]

Yes I think its possible if you mount them someplace else like your /home/username directory insted of /mnt

---

### Post by J0s3ph on 2006-07-06
Thanks for the reply. I'll try it very soon.

---

### Post by ruien on 2006-07-07
Another way is not to have volumes shown on desktop. Start gconf-editor and choose Apps and scroll down to nautilus>desktop. Here you can turn on and off what to show on yur desktop. Try it out. It updates your desktop realtime so can see what you want to show or not.

Hope this helps you out.

---

### Post by J0s3ph on 2006-07-16
Sorry for not getting back to this.

Thank's for informing me about gconf-editor. :)

---

