---
title: "RAID 0 Grub install fails"
date: 2006-04-26
forum: Desktop Environments
---

### Post by keirnna on 2006-04-26
I'm new to ubuntu, and it has been a year or so since my last work with Linux. I am a little rusty, so please be patient with me. I have a Gigabyte P4 Titan motherboard that has 4 onboard SATA channels. I think they are using a Silicon Image chipset. Two are set for RAID 0 in the hardware RAID; however, linux never recognized the drives as 1 drive. I've experienced this problem with Fedora core before. So I just created a software RAID in the Ubuntu set-up.

Both drives in the RAID array are 10,000 RPM 37GB WD Raptor HD's. I formated two partitions on each, and set them both up for use on "linux software raid". There is 1 35GB and 1 2GB partition on each drive. I combined those to create two "software" RAID arrays. 1 70GB drive that I formated in ext3, and set the mount point to /, and another 4GB partition set for SWAP. 

Everything seemed to be going well until I was informed grub failed to load, lilo also wouldn't load so I chose the next option that was "do not load a boot loader on the MBR." I was then given this message and told to reboot: 

you must use the /vmliuz kernel on partition /dev/md0 with flag root=/dev/md0

or something similar to this

I tried GAG, but it doesn't recognize my RAID. How do I get my system to boot up?

---

### Post by lha on 2006-04-26
Grub cannot boot from raid0 and as far as I know, neither can lilo. You'll have to put kernel on a partition that is accessible to grub. (Or lilo, if you wish.) A recommended option is to make a small raid1 device and use it as /boot, then commit the rest of drives to raid0 devices.

---

### Post by keirnna on 2006-04-26
That is good to know now. Is there anyway I can use a live cd or something to boot my system? I don't want to reload it. It would be very helpful if there was a warning stating that grub and lilo can't boot a RAID 0 device. I know Fedora core warned me about this. Iha, thanks a lot for the very quick responce.

---

### Post by lha on 2006-04-26
[QUOTE=keirnna]That is good to know now. Is there anyway I can use a live cd or something to boot my system? I don't want to reload it. It would be very helpful if there was a warning stating that grub and lilo can't boot a RAID 0 device. I know Fedora core warned me about this. Iha, thanks a lot for the very quick responce.[/QUOTE]
I have seen a warning when I installed on a raid device. Maybe it has been removed.

I guess you could use a cd or an usb-drive to contain boot loader and kernel+ram image, but do you really want to use cd/usb drive to boot Ubuntu? If you have other hard drives, you could put kernel there. Another option is to resize your swap partitions and create a /boot partition there.

---

