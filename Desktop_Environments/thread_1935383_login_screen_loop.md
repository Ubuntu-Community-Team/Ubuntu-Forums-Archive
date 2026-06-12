---
title: "login screen loop"
date: 2012-03-04
forum: Desktop Environments
---

### Post by bbb13 on 2012-03-04
I changed the default kde login screen from system settings->workspace appearance->splash screen to one called KubuntuVision and now everytime the system boots , lkubuntuvision splash screen loops eternally.it loads,then it seems to restart,then it loads again. Any way to get back to the default from the terminal or live cd? Thnx in advance

---

### Post by Tiganjero on 2012-03-04
Which version are you using?

Cheers,
George

---

### Post by bbb13 on 2012-03-04
kubuntu (pure) 11.10. My system is a sony vaio vpcej, intel i3, nvidia geforce 410m, 4gb DD3

---

### Post by Tiganjero on 2012-03-04
If you were able to boot into your system you could use this command
```
sudo update-alternatives --config usplash-artwork.so
```
where you'd be asked to choose an alternative splash screen. Or
```
sudo update-alternatives --config default.plymouth
```
which would change back to the default one. **_But_**, since you're not able to to do so, we'll have to something a bit different. So, the first step is booting from a live cd. Once you've done that, you'll have to mount your linux partition *_[SIZE="1"](if it's not mounted already)[/SIZE]_*. Execute
```
sudo fdisk -l
```
which should return something like
```
Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb4ba

Device Boot Start End Blocks Id System
/dev/sda1 * 1 524 4208006 83 Linux #this is the one you need since it has a little * under 'Boot', meaning it's your primary partition
/dev/sda2 525 1044 4176900 83 Linux
```
After getting the info you need, in this case */dev/sda1*, you should execute the next command changing the values respectively
```
sudo mount /dev/sda1 /mnt
```
That will mount your primary partition to the folder */mnt*.
***_Note_*** that in the remaining of this post the path to your linux partition will be referred to as */mnt* which you should also replace with */path_to_partition*, in case it was already mounted.
What you should do now is open up ***/mnt/etc/default/grub*** and change
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```
then run
```
echo 'manual' | sudo tee /mnt/etc/init/lightdm.override
```
Once you've done that open up ***/mnt/etc/kernel-img.conf*** and append this to it
```
postinst_hook = update-grub
postrm_hook = update-grub
do_bootloader = no
```
So just to explain everything and sum it up, we've mounted the partition if it was missing, disabled quiet splash so we can see the output of grub loading and added automagical grub updating.
_What do we do now?_ Reboot and eject the cd. Now you should see a whole bunch of text instead of the splash screen and probably boot normally. Although, on the off chance that the problem persists, we can still see where the error is, where it's failing. ***Post back the results and good luck!***

Cheers,
George

---

### Post by bbb13 on 2012-03-06
after doing a fresh install of kubuntu, i never tried to change the splash screen but when i turned off vsync from system settings - desktop effects, oops that did the trick and the splash screen loop started immediately again. so i'm guessing that was the problem before. so what do i do? do i try the things you mentioned in the above post?

---

### Post by bbb13 on 2012-03-12
only a fresh install solved the problem.

---

