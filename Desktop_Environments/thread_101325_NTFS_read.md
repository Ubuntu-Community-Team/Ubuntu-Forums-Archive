---
title: "NTFS read"
date: 2005-12-09
forum: Desktop Environments
---

### Post by Rochvellon on 2005-12-09
Ok, so I've got support for NTFS all worked up, but I can't acess the folder I mounted the partition on (/windows). I keeps saying that "I don't have permission to read file:///windows":

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=4323&stc=1&d=1134158303[/IMG]

Help?

---

### Post by Rackerz on 2005-12-09
Navigate to /etc/fstab/ using Konqueror and post the contents of fstab here.

---

### Post by Rochvellon on 2005-12-09
[quote=Rackerz]Navigate to /etc/fstab/ using Konqueror and post the contents of fstab here.[/quote] Ok, here it is:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda5 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda7 /home ext3 defaults,atime,auto,rw,dev,exec,suid,nouser 0 2
/dev/hda1 /windows ntfs defaults,uid=0,gid=0,auto,ro,users 0 0
/dev/hda6 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0
```

---

### Post by jjmckay on 2005-12-09
change the uid=0 to the uid # of your account login or a login that you want to have access to the volume.  remove the gid= entry unless you want to set gid.  Or vice versa.   I use uid=1000 for my login.  You can find your UID in /etc/passwd.

After you do that, do a 'umount /windows' then a 'mount -a'.

---

### Post by Rochvellon on 2005-12-10
Thank you! Sorry for the delay on the anwser, but I still have to sleep... 8-)

Strangely, kubuntu didn't recognize "sudo unmount /windows", is that something I have to do as non-sudo? Well, no problem, I just rebooted the computer. :grin:

---

### Post by Adrian on 2005-12-10
[QUOTE=Rochvellon]
Strangely, kubuntu didn't recognize "sudo unmount /windows", is that something I have to do as non-sudo?[/QUOTE]

The name of the command is actually "umount" and not "unmount". Maybe that explains things :)

---

### Post by Rackerz on 2005-12-10
unmount would be more sensible i would of thought :S.

---

### Post by Rochvellon on 2005-12-10
Yeah, I agree... Thank you!

---

