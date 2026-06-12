---
title: "Mounting samba shares at bootup"
date: 2006-06-03
forum: Desktop Environments
---

### Post by jlhughes on 2006-06-03
I have added two samba shares to fstab

//GIGHZ/HD2backup /media/GIGHZ_HD2backup smbfs guest,uid=1000 0 0
//GIGHZ/fireweb /media/GIGHZ_fireweb smbfs guest,uid=1000 0 0

When I do sudo mount -a both drives are added.

When I reboot the system, neither drive is added at bootup.

After rebooting  I must sudo mount -a to get the drives mounted.

What do I need to change in order to have the two drives mount when the computer is booted.

Thanks

---

