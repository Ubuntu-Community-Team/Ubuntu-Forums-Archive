---
title: "Ubuntu 9.04 GUI no go at login"
date: 2009-05-17
forum: General Help
---

### Post by doublej on 2009-05-17
Hi

I have been running Ubuntu 9.04 (Jaunty) (updated from 8.10) for a while now but yesterday stupidly updated my ATI graphics card driver and now can not login. All I get is a strange coloured (distorted) display after the initial Ubuntu first screen and nothing works - no keyboard response at all. I can access the Ubuntu files by booting another version of Linux (PCLinuxOS) from a CD. I have found out that Ubuntu does not have an inittab file so I can't change the login default level.

Using PCLOS I copied over the /etc/X11/xorg.conf.failsafe to /etc/X11/Xorg.conf but this made no difference.

Now to add insult to injury when I try to boot I get the message "Profile version not supported by Apparmor module" and the screen freezes. This is during a non-GUI login.

I dual boot and WinXP boots OK and PCLinuxOS from CD displays and works fine. My GRUB menu only has 2 options - Ubuntu and Windows.

Where do I go from here?

Cheers

John

---

### Post by Legace on 2009-05-17
Try this:

> **gocek said:**
> 
Reboot PC, select "Recovery mode" in boot-manager (GRUB) and then go for "root shell" option. 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```

then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.


Btw, I just read that you only have 2 options in GRUB, so you probably don't have recovery option?
If so, then just hightlight the Ubuntu option, then press the "e" button on your keyboard, and edit the kernel strting so it looks like this:

```
kernel		/boot/vmlinuz-2.6.28-11-generic (you might have a UUID here) ro  single[code]

Or just boot into PCLinuxOS, and edit /boot/grub/menu.lst and add a new entry:
[code]title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		4b2e9de2-8fa5-4496-998e-ccf552155c0c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4b2e9de2-8fa5-4496-998e-ccf552155c0c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic
```

Note, replace root=UUID=xxxx with your own UUID. If you don't have a UUID in the normal Ubuntu GRUB entry, just delete the whole root=UUID=xxx thing :)

---

### Post by doublej on 2009-05-17
*Select "Recovery mode" in boot-manager (GRUB)...*

I would if I could but this is not an option in my GRUB menu.

Cheers

John

---

### Post by Legace on 2009-05-17
Btw, I just read that you only have 2 options in GRUB, so you probably don't have recovery option?
If so, then just hightlight the Ubuntu option, then press the "e" button on your keyboard, and edit the kernel strting so it looks like this:

```
kernel		/boot/vmlinuz-2.6.28-11-generic (you might have a UUID here) ro  single
```

Or just boot into PCLinuxOS, and edit /boot/grub/menu.lst and add a new entry:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		4b2e9de2-8fa5-4496-998e-ccf552155c0c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4b2e9de2-8fa5-4496-998e-ccf552155c0c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic
```

Note, replace root=UUID=xxxx with your own UUID. If you don't have a UUID in the normal Ubuntu GRUB entry, just delete the whole root=UUID=xxx thing :)

If you have no idea what I'm talking about, boot into PCLinuxOS and post a copy of /boot/grub/menu.lst here :)

---

### Post by doublej on 2009-05-17
Thanks for your very quick and helpful reply. As I do know what you are talking about I will try what you suggest.

I will let you know how I get on but it may not be for a little while.

Cheers

John

---

### Post by doublej on 2009-05-18
Back again...

While logging in Ubuntu now says: 
Failed to access volume /dev/sdh1 - no such file or directory, NTFS signature is missing
Failed to mount /dev/sdc2 - invalid argument, does not seem to have valid NTFS

Meanwhile, OCLinuxOS booted from DVD finds all devices as follows:
/dev/root     500M   /
/dev/hde4     9.6G     /mnt/hde4      (Ubuntu data)
/dev/hde1     50G      /mnt/win_f     (WinXP Music)
/dev/hdb2     31G      /mnt/win_e     (WinXP Pictures)
/dev/hda1    112G      /mnt/win_c     (win XP OS)
/dev/hde2     14G      /mnt/hde2      (Ubuntu system) 
/dve/hdb1     44G      /mnt/win_d     (WinXP Downloads)

(My classification of devices in WinXP.)

Where do I go from here? My /boot/grub/menu.lst reads:

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4b54caf6-1adc-4962-9bab-cbcd618bd6e3 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4b54caf6-1adc-4962-9bab-cbcd618bd6e3 ro single
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

Regards

John

---

