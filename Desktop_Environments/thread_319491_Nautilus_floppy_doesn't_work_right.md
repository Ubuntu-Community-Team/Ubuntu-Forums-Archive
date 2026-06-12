---
title: "Nautilus: floppy doesn't work right"
date: 2006-12-15
forum: Desktop Environments
---

### Post by red_hax0r on 2006-12-15
When put a floppy in the drive and doubleclick on the floppy disk in "computer" (computer:///)  it mounts but then goes to the root directory.  If I click back or just mount the floppy normally and then double-click on the icon, it works fine.  

I could of course just mount normally all the time, but what would be the convenience of this?

This happens with two Edgy installations that I have.  I wasn't using Dapper long enough to notice if this happened with it too.  It's something wrong with Nautilus obviously.  

I was hoping there was a workaround or an updated package or patch or something.  

Something as simple as a configuration file edit would be helpful.

---

### Post by sabitha on 2006-12-15
i´ve got this too nautilus on edgy. perhaps this is bug for nautilus on edgy and will be fix someday.

---

### Post by po0f on 2006-12-15
red_hax0r,

Post the contents of you /etc/fstab file.  It most likely contains a line like this:
```
[FONT="Courier New"]/dev/           /media/floppy   auto        rw,user,noauto  0       0[/FONT]
```

If so, change it to this:
```
[FONT="Courier New"]/dev/fd0        /media/floppy   auto        rw,user,noauto  0       0[/FONT]
```

---

### Post by red_hax0r on 2006-12-16
I think sabitha is right, it is a bug, but here's my fstab anyway: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=46ab55e3-1c25-4fbc-8b9c-a71a7c9393e4 /               ext3    defaults,erro$
# /dev/hda1
UUID=80806BE5806BDFE0 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/hdb1
UUID=DCCB-0451  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=9712972d-9e9c-454d-b161-f25855a85fbd /media/hdb2     ext3    defaults     $
# /dev/hdb4
UUID=cbd8a551-6823-4cee-84f0-c313d04dacaa none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0           /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by Phlosten on 2006-12-16
I just noticed today that my fstab was incorrect with regard to the floppy disk drive. It was missing the fd0 part.
Must be a common issue.

---

### Post by paparucino on 2006-12-16
> **Phlosten said:**
> I just noticed today that my fstab was incorrect with regard to the floppy disk drive. It was missing the fd0 part.
Must be a common issue.
My gstab is wrong too. I didn't noticed it before since I have no occasion to use floppy on my home pc.

Is it to be marked as a bug?

---

