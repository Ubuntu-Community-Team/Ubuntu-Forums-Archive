---
title: "Uninstall and Fix Bootloader"
date: 2009-03-30
forum: General Help
---

### Post by herbjr on 2009-03-30
Hello All. I have looked around the forums and as well as google but could not find what I am looking for exactly.

I am dual booting XP along with Ubuntu. I have XP installed on my main PC hard drive and Ubuntu on a 200GB partition of my 500GB external drive. When my PC loads, it runs the GRUB boot loader. If my external hard drive isn't plugged in, the boot loader errors and I can not run windows. To fix this, I want to delete the GRUB boot loader and remove the whole partition of Ubuntu so I can reinstall it inside windows without the use of that boot loader.

Can anyone help me do this step by step? If worst comes to end, I may result to wiping my whole computer and start fresh.

---

### Post by nmartinsvr on 2009-03-30
hi, to uninstall the boot loader, just take a floppy of old win98 and do a "fdisk /mbr".

---

### Post by Hobgoblin on 2009-03-30
If you have an XP boot disk then boot from that, load the recovery console and enter

fixboot
fixmbr

Then reboot and use the XP computer management/disk management utilities to remove the Ubuntu partitions.

---

### Post by cariboo on 2009-03-30
Instead of reinstalling, why not fix your problem. 

Boot from your Windows install CD and go to the recovery console, once there run FIXMBR and FIXBOOT so that you boot to Windows only.

Use the LiveCD to install grub on the MBR of your  on your External drive. Open an Applications-->Accessories-->Terminal and type:

```
sudo grub
```

at the grub prompt type:

```
find /boot/grub/stage1
```

using the result from the above command, it will look something like this:

```
(hd1.0)
```

next:

```
root (hd1.0)
```

then

```
setup (hd1)
```

this should setup grub on your external drive. Next type:

```
quit
```

You should now be able to boot to Windows when the external drive is not connected, and boot Ubuntu when the external drive is connected.

Jim

---

