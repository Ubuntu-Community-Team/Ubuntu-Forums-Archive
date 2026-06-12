---
title: "Samba after hibernation."
date: 2006-02-07
forum: Desktop Environments
---

### Post by mrkslntbob on 2006-02-07
Samba is working fine, on my laptop.

But, when I hibernate, then come back, and re-connect to the network, samba isn't working.

I have tried restarting samba, /etc/init.d/samba restart, as well as, /etc/init.d/samba stop && /etc/init.d/samba start

I have also tried many variations of stopping and restarting networking, but i can't get samba to work again without rebooting.

Has anyone else been able to do this?

Thanks.

---

### Post by Iowan on 2006-02-07
[QUOTE=mrkslntbob]
...samba isn't working.
QUOTE]I'm curious if Samba has actually stopped or has it just dropped off the radar?  Does **smbd **and **nmbd** show up on a **sudo ps -ae**?

---

### Post by soulestream on 2006-02-07
are you running the samba server on your laptop or just mounting a share?

if your are just accessing a share, how are you mounting it?

is it in /etc/fstab?



soule

---

### Post by mrkslntbob on 2006-02-09
[QUOTE=soulestream]
are you running the samba server on your laptop or just mounting a share?

if your are just accessing a share, how are you mounting it?

is it in /etc/fstab?

soule[/QUOTE]

I'm not mounting a share, just going to 'Places->Network Servers' in Gnome.
Maybe i should try mounting it.

---

### Post by mrkslntbob on 2006-02-09
[QUOTE=Iowan][QUOTE=mrkslntbob]
...samba isn't working.
QUOTE]

I'm curious if Samba has actually stopped or has it just dropped off the radar?  Does **smbd **and **nmbd** show up on a **sudo ps -ae**?[/QUOTE]

smbd shows up, nmbd doesn't, perhaps i need to kill the old process?

---

