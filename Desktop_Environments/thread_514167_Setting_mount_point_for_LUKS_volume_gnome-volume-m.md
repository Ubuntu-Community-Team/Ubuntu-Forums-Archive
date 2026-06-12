---
title: "Setting mount point for LUKS volume gnome-volume-manager"
date: 2007-07-31
forum: Desktop Environments
---

### Post by reignbow on 2007-07-31
Hi!

I'm running Edgy and using a LUKS-encrypted external USB hard drive. When I plug it in, gnome-volume-manager pops up a dialog asking for the passphrase, then mounts it to /media/usbdisk. 

I'd rather have it mounted to /media/$MOUNTPOINT, though. Does anyone know where I can set this? As far as I recall, I should be able to set this with hal in some way. However, the command

```
sudo hal-set-property \ 
--udi `hal-find-by-property --key volume.uuid --string $UUID` \
--key volume.mount_point --string $MOUNTPOINT
```

does not seem to produce any permanent effect.

---

