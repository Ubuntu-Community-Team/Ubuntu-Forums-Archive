---
title: "Drive Shortcuts in 'Computer'"
date: 2005-07-20
forum: Desktop Environments
---

### Post by Phixion on 2005-07-20
Hi there, how can I get my hard drive shortcuts in 'Computer'?

I can make shortcuts on my desktop easy enough but can't make them in 'Computer'.

My drives are mounted in /media/

Also, how do i go about activating DMA on my drives, and how do I know if the drives support it?

Many thanks

---

### Post by Majlo on 2005-07-20
Hi ..

Add word users 

From my /etc/fstab

/dev/hda1       /media/windows  vfat    **users**,exec,iocharset=utf8,umask=000   0       0

---

### Post by Phixion on 2005-07-20
[QUOTE=Majlo]Hi ..

Add word users 

From my /etc/fstab

/dev/hda1       /media/windows  vfat    **users**,exec,iocharset=utf8,umask=000   0       0[/QUOTE]

Thanks very much! do you know how I can change the names of them?

---

