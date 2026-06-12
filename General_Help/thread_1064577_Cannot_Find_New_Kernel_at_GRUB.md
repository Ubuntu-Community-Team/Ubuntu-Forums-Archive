---
title: "Cannot Find New Kernel at GRUB"
date: 2009-02-09
forum: General Help
---

### Post by ProNux on 2009-02-09
Hi Guys,

I have many kernels installed, as I checked using Synaptic.  But during GRUB at boot, only about 2 kernels are displayed.

I remember last time that I removed a kernel like 2.6.24-23 using Synaptic (linux-headers).  Now, I have re-installed the latest kernels but I cannot find it at boot time.

My running version is

```
wong@wong-laptop:~$ uname -r
2.6.24-22-generic
wong@wong-laptop:~$
```

---

### Post by plucky on 2009-02-09
> **ProNux said:**
> Hi Guys,

I have many kernels installed, as I checked using Synaptic.  But during GRUB at boot, only about 2 kernels are displayed.

I remember last time that I removed a kernel like 2.6.24-23 using Synaptic (linux-headers).  Now, I have re-installed the latest kernels but I cannot find it at boot time.

My running version is

```
wong@wong-laptop:~$ uname -r
2.6.24-22-generic
wong@wong-laptop:~$
```

Open a terminal and post output of ```
cd /boot
ls -l
```

If the latest kernel is configured in the /boot directory,you will have to update the menu.lst file to boot it.The command ```
sudo update-grub
``` will do this for you.


Good Luck

---

### Post by ProNux on 2009-02-09
Hi there,

here's the output

```
wong@wong-laptop:/boot$ ls -l
total 54920
-rw-r--r-- 1 root root  422667 2008-08-21 12:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root  422838 2008-10-22 11:12 abi-2.6.24-21-generic
-rw-r--r-- 1 root root  422838 2008-11-25 06:47 abi-2.6.24-22-generic
-rw-r--r-- 1 root root   80049 2008-08-21 12:46 config-2.6.24-19-generic
-rw-r--r-- 1 root root   80062 2008-10-22 11:12 config-2.6.24-21-generic
-rw-r--r-- 1 root root   80062 2008-11-25 06:47 config-2.6.24-22-generic
drwxr-xr-x 2 root root    4096 2009-02-09 23:34 grub
-rw-r--r-- 1 root root 7449371 2008-10-26 04:07 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7833457 2008-10-27 02:43 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root 7463568 2008-11-07 19:56 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7463596 2008-10-29 22:47 initrd.img-2.6.24-21-generic.bak
-rw-r--r-- 1 root root 7879707 2009-01-21 00:50 initrd.img-2.6.24-22-generic
-rw-r--r-- 1 root root 7879564 2009-01-18 21:56 initrd.img-2.6.24-22-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 18:06 memtest86+.bin
-rw-r--r-- 1 root root  905170 2008-08-21 12:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root  905617 2008-10-22 11:12 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root  905617 2008-11-25 06:47 System.map-2.6.24-22-generic
-rw-r--r-- 1 root root 1921464 2008-08-21 12:46 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root 1920760 2008-10-22 11:12 vmlinuz-2.6.24-21-generic
-rw-r--r-- 1 root root 1921176 2008-11-25 06:47 vmlinuz-2.6.24-22-generic
```

Sorry, there are three kernel versions, not two.  But when I check Synaptic, other newer versions like 2.6.24-23.48 are marked as installed.  I tried 
```
sudo update-grub
```
and reboot but still the same.

By the way, if you ask me why I post this thread is in relation to my unstable WLAN, which, running on Live Intrepid Ibex, is very stable.  It is based on Ralink's RT2501USB(RT73) driver.

Thanks.

---

### Post by plucky on 2009-02-09
Well from that list,the latest kernel has not been installed.

From a terminal ```
sudo apt-get update
``` and see what the update manager picks up.

If there are updates then ```
sudo apt-get upgrade
``` to install them.

Also when it comes to install grub,do not accept the default,but select the option to upgrade the menu.lst file.

> But when I check Synaptic, other newer versions like 2.6.24-23.48 are marked as installed.


What did you search for? You need to search for **linux-image**

Good luck

---

### Post by ProNux on 2009-02-09
Actually, I already done

```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```

as what I read but still the same. :(

My system before is automatically updated whenever new kernels are available.  But after installing one kernel (can't remember the version), my WLAN started  its instability, so I removed that specific kernel, but my WLAN remained unstable.  Has this something to do with it?


@ Synaptic, I checked "linux-headers", not "linux-images".

Thanks...

---

### Post by ProNux on 2009-02-10
Finally I got it.

I might have uninstalled before the main linux-image.  I just reinstalled.  Now the grub is okay.

I still have one problem - unstable RT73 WLAN.  Anyway, thanks for the help.:)

---

