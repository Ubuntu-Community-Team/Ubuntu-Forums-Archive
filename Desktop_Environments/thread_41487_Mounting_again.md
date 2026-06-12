---
title: "Mounting again"
date: 2005-06-13
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-13
When I re-boot. All the mount points vanish from my places menu. That was quite annoying. Also they're all renamed to things like 

76G Hard Drive: 76G Media instead of data or win2k

Grr

Also if i rename my cd-roms something good like cd-rw and dvd-ram loads of things stop working cos they're looking for the old mount points (why not the hdc & hdd tags which are static?)

---

### Post by Dave_is_sexy on 2005-06-13
Er.. I now can't red any mounted drives (unless i'm in root nautilus). Naturally. Because I must've changed something (sarcasm - i swear it just randomly decides these things)

Fstab says:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               reiserfs defaults        0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/hda7        /mnt/cache  ntfs    ro,user,auto  0       0
/dev/hda2        /mnt/win2k  ntfs    ro,user,auto  0       0
/dev/hdb1        /mnt/data  ntfs    ro,user,auto  0       0
/dev/sda1        /media/softdrive  auto    rw,user,auto  0       0

and before i logged off, it was the same, but worked. A

---

### Post by Takis on 2005-06-14
Are you doing automatic (boot-time) mounts for these extra drives? If so, the root user is mounting them and doesn't let anyone read from his (her?) folder. Try setting ```
/dev/hda2 /mnt/win2k ntfs ro,user,auto 0 0
``` to ```
/dev/hda2 /mnt/win2k ntfs ro,user,auto,umask=0222 0 0
```

---

### Post by Eximius on 2005-06-14
hello.
i have 2 hdd one is ntfs and i`m tryin` to mount it like you said ^
and other is fat32.can you help to configure my fstab to mount them auto when i boot... ](*,) 
thnx in advance  ;-)

---

### Post by Andrei on 2005-06-14
U need to open fstab from a terminal as root...eg. 

```
sudo gedit /etc/fstab
```

In there...on a new line type:

```
/dev/<hd someting><tab><mount point><tab><file system><tab>uid=<insert your user here>,umask=0222<tab>0<tab>0
```

do this for each of ur drives that u want to mount

...be aware that u can't write to your NTFS drive...no matter how hard u try :)

hope that helps

---

### Post by andlinux21 on 2005-06-25
I know you cant write to NTFS drives but if you wanted to copy say backgrounds from that drive to the Ubuntu drive would it let you do that?

---

### Post by j0ma2 on 2005-06-26
[QUOTE=Dave_is_sexy]76G Hard Drive: 76G Media instead of data or win2k[/QUOTE]

Hi,

Any solution to this? I would also like my Partitions as "names" not as "XX GB Hard Drive".

Thank you.-

---

### Post by Dave_is_sexy on 2005-06-26
Yeah my partitions have those stupid names too. Didn't used to, but they do now  :-?

---

### Post by godzero on 2005-06-26
[QUOTE=andlinux21]I know you cant write to NTFS drives but if you wanted to copy say backgrounds from that drive to the Ubuntu drive would it let you do that?[/QUOTE]
 yes.
Reading works fine.

---

### Post by Clouseau__ on 2008-04-28
> **j0ma2 said:**
> 
Any solution to this? I would also like my Partitions as "names" not as "XX GB Hard Drive".


I'm also having this problem. Big deal for me ... I'm a control freak :D

Any help would be appreciated

---

