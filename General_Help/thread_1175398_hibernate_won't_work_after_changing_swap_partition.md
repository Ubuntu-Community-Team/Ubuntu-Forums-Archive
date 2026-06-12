---
title: "hibernate won't work after changing swap partition"
date: 2009-06-01
forum: General Help
---

### Post by AopicieR on 2009-06-01
Hi, 

I've resized my swap partition with gparted and the disk number got changed from /dev/sda5 to /dev/sda6 in the process. I've updated the /etc/fstab and the /etc/initramfs-tools/conf.d/resume, but when I try executing pm-hibernate, the screen just turns black for a second and then returns to the normal system. s2disk gives 
s2disk: Could not use the resume device (try swapon -a). Reason: No such device
I've followed instructions found at [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637), namely 
> 
1, determine your swap with 'fdisk -l'
2, do mkswap on your swap partition - RECORD THE UUID WHICH THIS COMMAND
OUTPUTS
3, now use this UUID to put into fstab and resume
files...(RESUME=UUID=<the-swap-partition-uuid-from-vol_ID
should go in /etc/initramfs-tools/conf.d/resume
4, update-initramfs -u
5, reboot normally after this finishes

swapon -s gives 
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	5116628	0	-1

I don't now what else I could try, it just won't work.
Thank you very much for any suggestions.

---

### Post by AopicieR on 2009-06-01
Ok, I solved it. The steps are as follows:
1) Run dpkg-reconfigure uswsusp. This gave me an error message and deleted my swap device.
2) Create it again using mkswap /dev/sda6 and swapon /dev/sda6.
3) Run dpkg-reconfigure uswsusp again. Check that /etc/uswsusp.conf contains the right label.
4) Put RESUME=/dev/sda6 in /etc/initramfs-tools/conf.d/resume and also /dev/sda6 in /etc/fstab.
5) Run update-initramfs -u.
Now it works again, the uswsusp step seems to have been the crucial one.

---

