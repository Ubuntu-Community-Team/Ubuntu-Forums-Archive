---
title: "struggling to mount floppy drive"
date: 2005-12-26
forum: General Help
---

### Post by ccman on 2005-12-26
I have type in "sudo/mnt/floppy"  followed by "cd/mnt/floppy" in the console/command in an attempt to mount the floppy in Ubuntu. The response prompted by this  command line is "command not found" followed by "no such file or directory" or alternatively by " can't find floppy in /etc/fstab/or etc./mtab. Please advise if I should reinstall unbuntu or if there is another way to fix this problem. Man:confused: thanks.:confused:

---

### Post by Danielle on 2005-12-26
when someone has helped you maybe they can tell you if this command will work:
sudo mount -t vfat /dev/fd0 /media/floppy0

don't do it now wait for someone who knows what they're talking about to tell you to do it becuase you might have to make some directories first.

the reason i'm giving you the command is because it worked for me but it seems i'm the only person it has worked for and i made it up myself :rolleyes:

---

### Post by Danielle on 2005-12-26
i forgot to say this is how i unmount the drive```
sudo umount -t vfat /dev/fd0 /media/floppy0
```it's important to unmount before taking the floppy out. the others ways 
```
mount /media/floppy0 
```
and
```
umount /media/floppy0
``` 
don't work for me.

---

### Post by Albinodrew on 2005-12-27
[QUOTE=Danielle]when someone has helped you maybe they can tell you if this command will work:
sudo mount -t vfat /dev/fd0 /media/floppy0

don't do it now wait for someone who knows what they're talking about to tell you to do it becuase you might have to make some directories first.

the reason i'm giving you the command is because it worked for me but it seems i'm the only person it has worked for and i made it up myself :rolleyes:[/QUOTE]

I could not access my floppy drive and that command did it.

Thank you.

---

