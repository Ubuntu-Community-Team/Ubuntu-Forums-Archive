---
title: "how do i get my mounted drive to show up under &quot;computer&quot; ?"
date: 2005-07-18
forum: Desktop Environments
---

### Post by brian g on 2005-07-18
i've mounted hdb1 to /mnt/wd120
and i'd like it to show up as a drive when i click on "Computer" just like "Filesystem".
I've had this working before with a previous Ubuntu install but I can't seem to get it to happen with this one.

i've tried *sudo mount -a*
the line for the drive in the /etc/fstab is */dev/hdb1	/mnt/wd120	vfat    iocharset=utf8,umask=000   0       0*

thanks in advance.

---

### Post by brian g on 2005-07-19
[QUOTE=brian g]i've mounted hdb1 to /mnt/wd120
and i'd like it to show up as a drive when i click on "Computer" just like "Filesystem".
I've had this working before with a previous Ubuntu install but I can't seem to get it to happen with this one.

i've tried *sudo mount -a*
the line for the drive in the /etc/fstab is */dev/hdb1	/mnt/wd120	vfat    iocharset=utf8,umask=000   0       0*

thanks in advance.[/QUOTE]
 anyone?

---

### Post by Omnios on 2005-07-19
I think it counts on how you set up you fstab. I had my vfat drive mounted as owner root and groups as user and the drive showed up oautomaticly using a ftab of.

```
/dev/hda2       /media/vfat     vfat    rw,users,gid=users,umask=000,       0       0
``` 

 Currently I have my username as owner in order to install wine onto it and the drive does not show up in computer any more. Hope this helps.

cheers

---

### Post by oneybm on 2005-07-19
Here's what my Windows partition gets mounted as under /etc/fstab...

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

Now it doesn't show up under my computer and I couldn't figure out how to do that so I just made a link on my Desktop named Windows XP with /media/windows as the URL inside of it.  Doesn't do exactly what you want; however, I can say it works.

---

### Post by brian g on 2005-07-20
[QUOTE=Omnios]I think it counts on how you set up you fstab. I had my vfat drive mounted as owner root and groups as user and the drive showed up oautomaticly using a ftab of.

```
/dev/hda2       /media/vfat     vfat    rw,users,gid=users,umask=000,       0       0
``` 

 Currently I have my username as owner in order to install wine onto it and the drive does not show up in computer any more. Hope this helps.

cheers[/QUOTE]
thank you very much.

---

