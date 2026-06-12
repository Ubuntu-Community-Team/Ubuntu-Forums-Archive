---
title: "Error 2 from Grub after kernel upgrades on fresh install"
date: 2008-12-07
forum: General Help
---

### Post by kierenp on 2008-12-07
Hi

I've got an issue regarding kernel upgrades on my system running Hardy. The installation is a fresh install using the alternate CD (ie the text installer). There's only one disk (500Gb IDE) and the system is Ubuntu only (ie not a dual boot etc).

The disk is set up as follows:

```

sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004a715

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   973940624   486970281   83  Linux
/dev/sda2       973940625   976768064     1413720    5  Extended
/dev/sda5       973940688   976768064     1413688+  82  Linux swap / Solaris

```


After the initial install all was fine until I needed to do kernel updates. These install OK (through the update manager) but on reboot I get the "Error 2" message from Grub and the system won't boot using the new kernel. I can then go to the grub menu and select the kernel installed when I first installed Hardy (2.6.24-19) and the system will boot correctly. However, I can't boot using any of the new kernels - I simply get the Error 2 message. This problem seems consistent for any kernel update within Hardy since I have now updated the kernel twice (when prompted by the update in Gnome etc) but I can't boot using any kernel other than the one first installed.

The kernel definitions in my menu.lst from Grub follows:

```

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=4e95989a-fe78-4348-b3aa-b38d50aa30a2 ro quiet splash
initrd          /boot/initrd.img-2.6.24-22-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=4e95989a-fe78-4348-b3aa-b38d50aa30a2 ro single
initrd          /boot/initrd.img-2.6.24-22-generic

title           Ubuntu 8.04.1, kernel 2.6.24-21-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=4e95989a-fe78-4348-b3aa-b38d50aa30a2 ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=4e95989a-fe78-4348-b3aa-b38d50aa30a2 ro single
initrd          /boot/initrd.img-2.6.24-21-generic

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=4e95989a-fe78-4348-b3aa-b38d50aa30a2 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=4e95989a-fe78-4348-b3aa-b38d50aa30a2 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

```

The 24-21 and 24-22 kernels won't boot but the 24-19 kernel will.

I've read a lot on the forums about similar problems being caused by issues with inode sizes (and older versions of Grub not supporting larger sizes) but I appear to be using the smaller inode size anyway (128) so don't think this is the problem.

```

sudo dumpe2fs /dev/sda1 | grep -i "inode size"
dumpe2fs 1.40.8 (13-Mar-2008)
Inode size:               128

```

Grub is installed to MBR on /dev/sda:

```

sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB

```

If anyone could help explain/solve why the system won't boot using the updated kernels I'd really appreciate it.

Thanks in advance.

Kieren

---

### Post by caljohnsmith on 2008-12-07
OK, while you are in Ubuntu, how about posting:
```
ls -l /boot
```
Note "-l" is a lowercase L, not a one; we can work from there if you want. :)

---

### Post by kierenp on 2008-12-07
> **caljohnsmith said:**
> OK, while you are in Ubuntu, how about posting:
```
ls -l /boot
```
Note "-l" is a lowercase L, not a one; we can work from there if you want. :)

Thanks for the reply, here's the output:

```
ls -l /boot
total 53472
-rw-r--r-- 1 root root  422667 2008-08-21 05:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root  422838 2008-10-22 04:12 abi-2.6.24-21-generic
-rw-r--r-- 1 root root  422838 2008-11-24 22:47 abi-2.6.24-22-generic
-rw-r--r-- 1 root root   80049 2008-08-21 05:46 config-2.6.24-19-generic
-rw-r--r-- 1 root root   80062 2008-10-22 04:12 config-2.6.24-21-generic
-rw-r--r-- 1 root root   80062 2008-11-24 22:47 config-2.6.24-22-generic
drwxr-xr-x 2 root root    4096 2008-12-03 08:31 grub
-rw-r--r-- 1 root root 7487231 2008-10-25 15:50 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7049582 2008-10-25 14:32 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root 7488139 2008-11-09 15:23 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7487824 2008-10-28 18:57 initrd.img-2.6.24-21-generic.bak
-rw-r--r-- 1 root root 7485177 2008-12-03 08:32 initrd.img-2.6.24-22-generic
-rw-r--r-- 1 root root 7485146 2008-12-03 08:31 initrd.img-2.6.24-22-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 11:06 memtest86+.bin
-rw-r--r-- 1 root root  905170 2008-08-21 05:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root  905617 2008-10-22 04:12 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root  905617 2008-11-24 22:47 System.map-2.6.24-22-generic
-rw-r--r-- 1 root root 1921464 2008-08-21 05:46 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root 1920760 2008-10-22 04:12 vmlinuz-2.6.24-21-generic
-rw-r--r-- 1 root root 1921176 2008-11-24 22:47 vmlinuz-2.6.24-22-generic

```

---

### Post by caljohnsmith on 2008-12-07
OK, how about trying the following:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install --recheck /dev/sda
sudo apt-get purge linux-headers-2.6.24-21-generic linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic linux-ubuntu-modules-2.6.24-21-generic
sudo apt-get install linux-headers-2.6.24-21-generic linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic linux-ubuntu-modules-2.6.24-21-generic
```
And please post the output of all the above commands. Make sure after everything is done that your menu.lst still lists the 2.6.24-21 kernel, reboot, and try booting the 2.6.24-21 kernel and let me know if anything changes.

---

### Post by kierenp on 2008-12-07
Thanks for the reply. I ran the commands and here's the output:

```

sudo apt-get purge grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5 gcc-3.3-base
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  grub*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 852kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146846 files and directories currently installed.)
Removing grub ...
Purging configuration files for grub ...

```

then

```

sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5 gcc-3.3-base
Use 'apt-get autoremove' to remove them.
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed
  grub
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 385kB of archives.
After this operation, 852kB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com hardy/main grub 0.97-29ubuntu21 [385kB]
Fetched 385kB in 3s (97.2kB/s)
Preconfiguring packages ...
Selecting previously deselected package grub.
(Reading database ... 146800 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu21_i386.deb) ...
Setting up grub (0.97-29ubuntu21) ...

```

then:

```

sudo grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda

```

then:

```

sudo apt-get purge linux-headers-2.6.24-21-generic linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic linux-ubuntu-modules-2.6.24-21-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5 gcc-3.3-base
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  linux-headers-2.6.24-21-generic* linux-image-2.6.24-21-generic*
  linux-restricted-modules-2.6.24-21-generic*
  linux-ubuntu-modules-2.6.24-21-generic*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 135MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146846 files and directories currently installed.)
Removing linux-headers-2.6.24-21-generic ...
Removing linux-restricted-modules-2.6.24-21-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-21-generic ...
Removing linux-ubuntu-modules-2.6.24-21-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Purging configuration files for linux-ubuntu-modules-2.6.24-21-generic ...
Removing linux-image-2.6.24-21-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.24-21-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

```

sudo apt-get install linux-headers-2.6.24-21-generic linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic linux-ubuntu-modules-2.6.24-21-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5 gcc-3.3-base
Use 'apt-get autoremove' to remove them.
Suggested packages:
  linux-doc-2.6.24 linux-source-2.6.24 avm-fritz-firmware-2.6.24-21 nvidia-glx
  nvidia-glx-legacy nvidia-glx-new
The following NEW packages will be installed
  linux-headers-2.6.24-21-generic linux-image-2.6.24-21-generic
  linux-restricted-modules-2.6.24-21-generic
  linux-ubuntu-modules-2.6.24-21-generic
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.6MB/43.0MB of archives.
After this operation, 135MB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com hardy-updates/main linux-image-2.6.24-21-generic 2.6.24-21.43 [18.4MB]
Get: 2 http://gb.archive.ubuntu.com hardy-updates/main linux-headers-2.6.24-21-generic 2.6.24-21.43 [648kB]
Get: 3 http://gb.archive.ubuntu.com hardy-updates/restricted linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.51 [18.6MB]
Fetched 37.6MB in 4min22s (143kB/s)                                            
Selecting previously deselected package linux-image-2.6.24-21-generic.
(Reading database ... 138641 files and directories currently installed.)
Unpacking linux-image-2.6.24-21-generic (from .../linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb) ...
Done.
Selecting previously deselected package linux-ubuntu-modules-2.6.24-21-generic.
Unpacking linux-ubuntu-modules-2.6.24-21-generic (from .../linux-ubuntu-modules-2.6.24-21-generic_2.6.24-21.33_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.24-21-generic.
Unpacking linux-headers-2.6.24-21-generic (from .../linux-headers-2.6.24-21-generic_2.6.24-21.43_i386.deb) ...
Selecting previously deselected package linux-restricted-modules-2.6.24-21-generic.
Unpacking linux-restricted-modules-2.6.24-21-generic (from .../linux-restricted-modules-2.6.24-21-generic_2.6.24.14-21.51_i386.deb) ...
Setting up linux-image-2.6.24-21-generic (2.6.24-21.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done


Setting up linux-ubuntu-modules-2.6.24-21-generic (2.6.24-21.33) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic

Setting up linux-headers-2.6.24-21-generic (2.6.24-21.43) ...

Setting up linux-restricted-modules-2.6.24-21-generic (2.6.24.14-21.51) ...


```

I checked the 24-21 kernel was in the grub menu file and rebooted. This time when I selected the kernel it booted without error and all looks fine.

Thank you so much for all your help. What do you think was wrong and do you think future kernel upgrades will be ok?

Thank you again

Cheers

Kieren

---

### Post by caljohnsmith on 2008-12-07
> **kierenp said:**
> 
I checked the 24-21 kernel was in the grub menu file and rebooted. This time when I selected the kernel it booted without error and all looks fine.

Thank you so much for all your help. What do you think was wrong and do you think future kernel upgrades will be ok?

Thank you again

Cheers

Kieren
I'm glad to hear that worked; did you also try booting your 2.6.24-22-generic kernel? That will give a clue whether it was a problem with Grub or with somehow a misconfigured kernel, because I assume you didn't also purge/reinstall the 2.6.24-22 kernel yet?

---

### Post by kierenp on 2008-12-07
Thanks again for the messages. I tried booting into the 24-22 kernel and got the same error. Booting back into 24-21 was fine again. I assume this perhaps means that something had corrupted the two kernels?

Thanks again

Kieren

---

### Post by caljohnsmith on 2008-12-07
> **kierenp said:**
> Thanks again for the messages. I tried booting into the 24-22 kernel and got the same error. Booting back into 24-21 was fine again. I assume this perhaps means that something had corrupted the two kernels?

Thanks again

Kieren
Yes, that's really strange, because it sounds like it was a problem with the kernels and not Grub; I'm not sure how they could have been misconfigured or corrupted. How about purging/reinstalling the 2.6.24-22 kernel and see if that fixes it as well:
```
sudo apt-get purge linux-headers-2.6.24-22-generic linux-image-2.6.24-22-generic linux-restricted-modules-2.6.24-22-generic linux-ubuntu-modules-2.6.24-22-generic
sudo apt-get install linux-headers-2.6.24-21-generic linux-image-2.6.24-22-generic linux-restricted-modules-2.6.24-22-generic linux-ubuntu-modules-2.6.24-22-generic

```
Let me know if that works for the 2.6.24-22 kernel.

---

### Post by kierenp on 2008-12-08
I purged and reinstalled the 24-22 kernel as suggested:

```

sudo apt-get purge linux-headers-2.6.24-22-generic linux-image-2.6.24-22-generic linux-restricted-modules-2.6.24-22-generic linux-ubuntu-modules-2.6.24-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5 gcc-3.3-base
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  linux-generic* linux-headers-2.6.24-22-generic* linux-headers-generic*
  linux-image-2.6.24-22-generic* linux-image-generic*
  linux-restricted-modules-2.6.24-22-generic*
  linux-restricted-modules-generic* linux-ubuntu-modules-2.6.24-22-generic*
0 upgraded, 0 newly installed, 8 to remove and 12 not upgraded.
After this operation, 136MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146846 files and directories currently installed.)
Removing linux-generic ...
Removing linux-headers-generic ...
Removing linux-headers-2.6.24-22-generic ...
Removing linux-restricted-modules-generic ...
Removing linux-restricted-modules-2.6.24-22-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-22-generic ...
Removing linux-image-generic ...
Removing linux-ubuntu-modules-2.6.24-22-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic
Purging configuration files for linux-ubuntu-modules-2.6.24-22-generic ...
Removing linux-image-2.6.24-22-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.24-22-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done



sudo apt-get install linux-headers-2.6.24-21-generic linux-image-2.6.24-22-generic linux-restricted-modules-2.6.24-22-generic linux-ubuntu-modules-2.6.24-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-21-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++5 gcc-3.3-base
Use 'apt-get autoremove' to remove them.
Suggested packages:
  linux-doc-2.6.24 linux-source-2.6.24 avm-fritz-firmware-2.6.24-22 nvidia-glx
  nvidia-glx-legacy nvidia-glx-new
The following NEW packages will be installed
  linux-image-2.6.24-22-generic linux-restricted-modules-2.6.24-22-generic
  linux-ubuntu-modules-2.6.24-22-generic
0 upgraded, 3 newly installed, 0 to remove and 12 not upgraded.
Need to get 0B/42.4MB of archives.
After this operation, 128MB of additional disk space will be used.
Selecting previously deselected package linux-image-2.6.24-22-generic.
(Reading database ... 138629 files and directories currently installed.)
Unpacking linux-image-2.6.24-22-generic (from .../linux-image-2.6.24-22-generic_2.6.24-22.45_i386.deb) ...
Done.
Selecting previously deselected package linux-ubuntu-modules-2.6.24-22-generic.
Unpacking linux-ubuntu-modules-2.6.24-22-generic (from .../linux-ubuntu-modules-2.6.24-22-generic_2.6.24-22.35_i386.deb) ...
Selecting previously deselected package linux-restricted-modules-2.6.24-22-generic.
Unpacking linux-restricted-modules-2.6.24-22-generic (from .../linux-restricted-modules-2.6.24-22-generic_2.6.24.14-22.53_i386.deb) ...
Setting up linux-image-2.6.24-22-generic (2.6.24-22.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done


Setting up linux-ubuntu-modules-2.6.24-22-generic (2.6.24-22.35) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic

Setting up linux-restricted-modules-2.6.24-22-generic (2.6.24.14-22.53) ...

```

This also now boots correctly. Seems I must've had two corrupted kernels but i'm not sure what could've caused it. Fingers crossed all will be ok when the next update is released.

Thanks again for all your help.

Kieren

---

