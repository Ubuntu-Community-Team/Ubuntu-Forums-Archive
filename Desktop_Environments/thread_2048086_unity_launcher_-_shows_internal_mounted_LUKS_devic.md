---
title: "unity launcher - shows internal mounted LUKS devices (even the one for /)"
date: 2012-08-26
forum: Desktop Environments
---

### Post by ghost_zero on 2012-08-26
Hello, 

I just finished installing Ubuntu 12.04 on my new SSD and I also setup encrypted root and home partitions.

I have now configured everything correctly so far. However, all those mounted encrypted partitions are visible in the Unity launcher although they are mounted to / and /home

I don't want to disable the device icon display in the launcher completely, as I want to see e.g. a memory stick displayed there, however, I really don't want drives that are mounted on boot up displayed there.

Can I somehow remove certain devices from the launcher or actually why are the displayed in the first place? After all they are configured in fstab and crypttab

---

### Post by CtrlGee on 2012-09-17
> **ghost_zero said:**
> Hello, 

I just finished installing Ubuntu 12.04 on my new SSD and I also setup encrypted root and home partitions.

I have now configured everything correctly so far. However, all those mounted encrypted partitions are visible in the Unity launcher although they are mounted to / and /home

I don't want to disable the device icon display in the launcher completely, as I want to see e.g. a memory stick displayed there, however, I really don't want drives that are mounted on boot up displayed there.

Can I somehow remove certain devices from the launcher or actually why are the displayed in the first place? After all they are configured in fstab and crypttab

Hi ... Did you discover a fix for this?

Same situation ... I don't want a LUKS-encrypted home partition showing up in the Launcher or Nautilus. I find a lot of solutions that mention removing *all* mounted drives or mounting partitions under /mnt ... but that is not what I want.

---

### Post by Frogs Hair on 2012-09-17
See the link . [http://askubuntu.com/questions/159029/how-to-hide-mounted-partitions-and-devices-from-unity-launche](http://askubuntu.com/questions/159029/how-to-hide-mounted-partitions-and-devices-from-unity-launche)

---

### Post by CtrlGee on 2012-09-18
> **Frogs Hair said:**
> See the link . [http://askubuntu.com/questions/159029/how-to-hide-mounted-partitions-and-devices-from-unity-launche](http://askubuntu.com/questions/159029/how-to-hide-mounted-partitions-and-devices-from-unity-launche)

Thanks for the link ... but the fix hides *all* devices. I just want to hide my internal LUKS-encrypted /home partition ... and let external devices show up as per usual.

All the fixes I have been able to find either hide *all* devices or involve mounting the device under /mnt.

Is there any way to hide a single, specified device? Perhaps using the UUID? Thanks for any help.

---

### Post by hmalissa on 2012-09-28
> **ghost_zero said:**
> Hello, 

I just finished installing Ubuntu 12.04 on my new SSD and I also setup encrypted root and home partitions.

I have now configured everything correctly so far. However, all those mounted encrypted partitions are visible in the Unity launcher although they are mounted to / and /home

I don't want to disable the device icon display in the launcher completely, as I want to see e.g. a memory stick displayed there, however, I really don't want drives that are mounted on boot up displayed there.

Can I somehow remove certain devices from the launcher or actually why are the displayed in the first place? After all they are configured in fstab and crypttab

Similar situation here. I'm running a level-1-RAID that is mounted at boot-time with a mount-point somewhere inside my home directory. The users aren't even permitted to mount or unmount it. 
But for some reason unity shows it, along with CDs, USB-sticks, etc. In particular, the unmount-button doesn't make any sense here. I'd like to hide it from the launcher, for the user it should be nothing more than a directory.
My / mount-point or other default ones are not shown, however. How does unity determine which ones to show and which ones to hide from the launcher? Is it something inside /etc/fstab?

---

