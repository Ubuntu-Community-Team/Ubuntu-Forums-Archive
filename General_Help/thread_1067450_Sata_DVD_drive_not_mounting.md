---
title: "Sata DVD drive not mounting"
date: 2009-02-11
forum: General Help
---

### Post by mistere23 on 2009-02-11
I just put in a Sata DVD rw drive that I know works in a windows system.  
Sometimes an icon appears on the desktop showing the disc icon in the dvd but other times it doesnt.  

When the icon does come up I cant play the dvd in VLC or movie player.

sudo lshw -C disk shows:

```
 *-disk                  
       description: ATA Disk
       product: MDT MD2000JB-00R
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 20.0
       serial: MDT-MCANK5973951
       size: 186GiB (200GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=69205244
  *-cdrom
       description: DVD-RAM writer
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=open
```

I tried deleting the line in fstab as suggested in another thread but I think that just made things worse because the system hung for a while after I rebooted trying to figure out what to do....:confused:
I also cleared the 70-persistent-cd.rules file as someone suggested but that din't fix anything either.

Can anyone give me some ideas?

---

