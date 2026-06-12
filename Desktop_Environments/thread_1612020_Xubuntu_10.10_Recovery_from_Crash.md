---
title: "Xubuntu 10.10 Recovery from Crash"
date: 2010-11-02
forum: Desktop Environments
---

### Post by metallica1973 on 2010-11-02
I installed Xubuntu 10.10 on a penstick and made some changes to FSTAB. Now I get a 

[php]initramfs[/php]

and a command prompt and I cannot load the kernel. 

I added this to fstab to optimize my penstick

[php]
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /tmp/.cache tmpfs defaults,noatime,mode=1777 0 0
shm /dev/shm tmpfs nodev,nosuid,size=6G 0 0 
and then ran this to take out journaling:
[/php]

[php]
 tune2fs -o journal_data_writeback /dev/sdb5
  tune2fs -O ^has_journal /dev/sdb5
  e2fsck -f /dev/sdb5
  dumpe2fs /dev/sdb5|more  
[/php]

Can I use the Xubuntu 10.10. install cdrom to get to the command prompt to make some changes? Help

---

### Post by Barriehie on 2010-11-02
SHould be able to.  Open a terminal and mount your drive and make the changes.  (or uncomment the lines in fstab you changed. ;) )

---

### Post by metallica1973 on 2010-11-03
I booted from the cdrom and could not mount it through the gui. It would error. How can it be mounted via the mount command:

[php]mount /dev/sda1 /media/volume_name[/php]

---

### Post by Barriehie on 2010-11-03
> **metallica1973 said:**
> I booted from the cdrom and could not mount it through the gui. It would error. How can it be mounted via the mount command:

[php]mount /dev/sda1 /media/volume_name[/php]

What error(s) did you get?
```

mount -t *type* /dev/sda1 /media/voume_name
```

---

### Post by metallica1973 on 2010-11-05
I just formatted them machine for it had issue. thanks

---

