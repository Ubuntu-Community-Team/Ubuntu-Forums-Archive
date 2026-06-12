---
title: "PCI: Failed to allocate mem resource #6:10000@fe000000 for 0000:01:00.0"
date: 2006-09-28
forum: Desktop Environments
---

### Post by Narrf on 2006-09-28
This morning my Dapper desktop on my old Dell, was booting perfectly, but tonight it won't boot at all. As far as I'm concerned, nothing has changed on the system, which is the most puzzling! :confused: 

I choose a kernel from the Grub boot loader and the kernel uncompresses. Then I get a "Failed to allocate mem resource #6 error#". 

```

<< -- boot sequence from Grub selection -- >>
Uncompressing Linux... Ok, booting the kernel.
[17179574:776000] PCI: Failed to allocate mem resource #6:10000@fe000000 for 0000:01:00.0
mount: Mounting /dev/hdb1 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: no suce file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
```

It then 'dumps' me to a Busybox prompt.

Booting from a 6.06 Live CD I can successfully manually mount /dev/hdb1 and the file structure looks in place. Interestingly during the Live CD boot, you can see the same error message (e.g. Failed to allocated mem.....) flash by before the system continues to boot. That makes me think it might previously have been being displayed and I never noticed it before.

I've run several commands to collect the information I thought might be relevant and included their output below.

```
ubuntu@ubuntu:~$ /bin/lspci | grep 01:00
0000:01/00.0 VGA compatible controller: nVidia Corporation NV5MG4 [RIVA TNT2 Model 64/model 64 Pro] (rev 15]

```

```
ubuntu@ubuntu:~$ /bin/cat /var/logs/dmesg | grep 01:00
[4294670.418000] Boot video device is 0000:01:00.0
[4294670.438000] PCI: Failed to allocate mem resource #6:10000@fe000000 for 0000:01:00.0 
```


```
ubuntu@ubuntu:~$ /usr/bin/lshw -businfo | grep 01:00
pci@01:00.0		display		NV5M64 [RIVA TNT2 Model 64/model 64 Pro]
```

```

ubuntu@ubuntu:~$ /usr/bin/lshw -C display
WARNING: you should run this program as super-user
  *-display
	description: VGA compatible controller
	product: NV5m64 [RIVA TNT2 Model 64/model 64 Pro]
	vendor: nVidia Corporation
	bus info: pci@01:00.0
	version: 15
	size: 32MB
	width: 32 bits
	clock: 66MHz
	capabilities: vga bus_master cap_list
	resources: iomemory:f5000000-f5ffffff iomemory:fc000000-fdffffff irq:10

```

Everything was pointing me to the video card, but I replaced that with another card (an old 3dFx Voodoo card I have loafing around) and get the same result.

I've checked out all settings in BIOS I thought might be connected, and checked the BIOS logs and interupt settings. Nothing was reported in the logs and all the interupts seemed to be available and not in conflict.

Lastly, to add insult to injury, the Wife's Windows XP install on hda1 starts up no issue! [-( 

Am totally lost as to what to try next and am all Googled out of ideas! ](*,) 

Help appreciated.
Thanks,
Narrf

---

