---
title: "update and dpkg errors"
date: 2009-05-27
forum: General Help
---

### Post by colsandurz on 2009-05-27
Hello,

when I try to update I get this error.

```

$ sudo apt-get update
Hit http://security.ubuntu.com jaunty-security Release.gpg
...
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

When I try run that command I get this error

```

$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-restricted-modules-2.6.28-11-generic (2.6.28-11.15) ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
dpkg: error processing linux-restricted-modules-2.6.28-11-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-11-generic; however:
  Package linux-restricted-modules-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.11.15); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
dpkg: subprocess post-installation script returned error exit status 1


```

I think I know what's going on here.  /boot is on a separate partition that's 50 MB.  

```

$ sudo du -hs /boot
36M	/boot

```

```

$  ls -la /boot
total 36669
drwxr-xr-x  4 root root    1024 2009-05-27 11:13 .
drwxr-xr-x 21 root root    4096 2009-05-04 13:58 ..
-rw-r--r--  1 root root  508385 2009-04-01 18:46 abi-2.6.27-11-generic
-rw-r--r--  1 root root  507665 2008-11-04 16:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  529118 2009-04-16 23:41 abi-2.6.28-11-generic
-rw-r--r--  1 root root   91358 2009-04-01 18:46 config-2.6.27-11-generic
-rw-r--r--  1 root root   91364 2008-11-04 16:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   96795 2009-04-16 23:41 config-2.6.28-11-generic
drwxr-xr-x  2 root root    1024 2009-05-04 13:58 grub
-rw-r--r--  1 root root 8206330 2009-05-04 13:51 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8162351 2009-03-23 19:02 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 7516474 2009-05-04 13:58 initrd.img-2.6.28-11-generic
drwx------  2 root root   12288 2009-03-23 18:41 lost+found
-rw-r--r--  1 root root  128796 2009-03-27 13:15 memtest86+.bin
-rw-r--r--  1 root root 1031799 2009-04-01 18:46 System.map-2.6.27-11-generic
-rw-r--r--  1 root root 1029585 2008-11-04 16:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1456232 2009-04-16 23:41 System.map-2.6.28-11-generic
-rw-r--r--  1 root root    1074 2009-04-01 18:48 vmcoreinfo-2.6.27-11-generic
-rw-r--r--  1 root root    1073 2008-11-04 16:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1074 2009-04-16 23:43 vmcoreinfo-2.6.28-11-generic
-rw-r--r--  1 root root 2249232 2009-04-01 18:46 vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2244464 2008-11-04 16:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 3501776 2009-04-16 23:41 vmlinuz-2.6.28-11-generic


```

Do I just need to delete some of this old stuff?  If so, can I just delete it, or should is there a procedure I should follow?

will I be fine if I do something like this?
```

$  sudo rm -rf /boot/*2.6.27-11*

```

Thanks for any help.

---

### Post by Pidgin on 2009-05-27
Use your package manager to remove related packages:
```
linux-headers-*
linux-headers-*-generic
linux-image-*-generic
linux-restricted-modules-*-generic
```

---

### Post by SOULRiDER on 2009-05-27
Be careful not to remove the kernel you are curently using! Just remove the older kernels.

---

### Post by colsandurz on 2009-05-27
so I should run this command:

```

$ sudo apt-get remove --purge linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic linux-image-2.6.27-7-generic linux-restricted-modules-2.6.27-7-generic

$ sudo apt-get remove --purge linux-headers-2.6.27-11 linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic

```

So this will tell apt to remove the old kernel only.  Since the one I'm using is 2.6.28-11

---

### Post by Bender2k14 on 2009-05-27
> **colsandurz said:**
> so I should run this command:

```

$ sudo apt-get remove --purge linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic linux-image-2.6.27-7-generic linux-restricted-modules-2.6.27-7-generic

$ sudo apt-get remove --purge linux-headers-2.6.27-11 linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic

```

So this will tell apt to remove the old kernel only.  Since the one I'm using is 2.6.28-11

Looks ok to me.

Also, you can just try autoremoving packages with
```
sudo apt-get autoremove
```
or use the System -> Administration -> Computer Janitor.

---

### Post by colsandurz on 2009-05-28
This still isn't working.  That is, none of these commands work:

neither
```

$ sudo apt-get remove --purge linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic linux-image-2.6.27-7-generic linux-restricted-modules-2.6.27-7-generic

$ sudo apt-get remove --purge linux-headers-2.6.27-11 linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic

```

nor
```
sudo apt-get autoremove
```

I am getting a message now that says "Software Index is Broken" ... run this command

```

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-restricted-modules-2.6.27-11-generic linux-restricted-modules-2.6.27-7-generic
0 upgraded, 0 newly installed, 2 to remove and 54 not upgraded.
6 not fully installed or removed.
After this operation, 4444kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157244 files and directories currently installed.)
Removing linux-restricted-modules-2.6.27-11-generic ...
rmdir: failed to remove `/lib/modules/2.6.27-11-generic/volatile/': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.27-11-generic
dpkg: error processing linux-restricted-modules-2.6.27-11-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-restricted-modules-2.6.27-7-generic ...
rmdir: failed to remove `/lib/modules/2.6.27-7-generic/volatile/': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.27-7-generic
dpkg: error processing linux-restricted-modules-2.6.27-7-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-restricted-modules-2.6.27-11-generic
 linux-restricted-modules-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

It's possible the machine was rebooted or something during the upgrade to jaunty.  (this is a lab machine, I'm not a round it all the time)  Does anyone know what to do if that was the case?

Thanks

---

### Post by nebileix on 2009-05-28
Did u try resizing the /boot partition with gparted?

---

### Post by colsandurz on 2009-05-28
no.  But I really want to avoid that since this machine dual boots and changing partition sizes could mess up another OS.

Should I remove the old kernel stuff from /boot?  (2.6.27 etc)

---

### Post by nebileix on 2009-05-28
Well, if you have any space to spare in ur root partition, I think u can create another bigger /boot partition and copy those files over just to fix these issue first. There might be a better way but i can't think of any now.

---

### Post by Bender2k14 on 2009-05-28
If you boot to Recovery Mode, one of the options helps you free disk space.  Try that.

---

### Post by colsandurz on 2009-05-28
I just did this:

```

$ rm -rf /boot/*2.6.27*

```

Now everything works fine.  I probably should have done that earlier, but it seemed a little risky to me, so I wanted to be sure.

---

### Post by Bender2k14 on 2009-05-28
The package manager might complain about problems in the future.  It thinks that some packages are still installed but you have manually removed most (if not all) of the files for those packages.  I have never done that before, so I am only guessing at what would happen.

---

### Post by nebileix on 2009-05-29
> **Bender2k14 said:**
> The package manager might complain about problems in the future.  It thinks that some packages are still installed but you have manually removed most (if not all) of the files for those packages.  I have never done that before, so I am only guessing at what would happen.

Yeah... most likely it'll... try apt-get with the -f switch.

---

