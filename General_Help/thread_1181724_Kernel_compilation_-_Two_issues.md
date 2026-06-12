---
title: "Kernel compilation - Two issues"
date: 2009-06-08
forum: General Help
---

### Post by Lockheed on 2009-06-08
I was following [this guide]("http://ubuntuforums.org/showthread.php?t=311158") but I run into two proglems.

First, when I do *dpkg -i linux*2.6.29*.deb* I get this:
```
Setting up linux-image-2.6.29.4 (x64) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Not updating initrd symbolic links since we are being updated/reinstalled 
(x64 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(x64 was configured last, according to dpkg)
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.29.4
Found kernel: /boot/vmlinuz-2.6.28-12-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
[B][COLOR="Red"]Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.29.4.postinst line 1186.
dpkg: error processing linux-image-2.6.29.4 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.29.4[/COLOR][/B]

```


But I ignored this, restarted and the new kernel doesn't boot up.
After GRUB I get this:
```
Starting up...
audit: cannot initialize inotify handle
Loading, please wait...
Gave up waiting for root device. 
(...)
ALERT! /dev/disk/by-uid/<some various digits>. Dropping to a shell!
```

After that, I am in some BusyBox:
(initramfs) _


Now, I suppose this is related to not compilin into the kernel drivers for my SATA chip. However, I did include:
- NVIDIA SATA support
- ACPI firmware driver for PATA
- AMD/NVIDIA PATA support

I am not sure what else should I choose as all the other drivers seem to me not applicable for my system (see my sig).

Can someone advise?

---

### Post by Lockheed on 2009-06-09
bump da bump

---

### Post by deepspring on 2009-06-10
> **Lockheed said:**
> ...

The first error is simple to fix. Basically, you just need to completely remove and then re-install the "nvidia-common" package. During this process, the kernel should install properly without any further errors.

To do this, simply run the following commands:
```
sudo apt-get remove --purge nvidia-common
sudo apt-get install nvidia-common
```

Note the "--purge", this is required for the trick to work properly.

The second error I'm not sure about. You may need to run "sudo update-grub" again. You may also have duplicate ID's for two of your partitions.

---

### Post by Lockheed on 2009-06-14
I am unable to run this command as I am being told another process is using those files.
When exactly should I run it? Before, during or after compilation?

---

### Post by stoner_di on 2009-06-14
I want to ask someone tried to incorporate the bootup logo ( mini tux in the top left of the display to load the system).
Perform all necessary for this:
- when compiling the kernel, I select this:

Support for frame buffer devices FB->VESA VGA graphics support FB_VESA

Select all in the:

Console display driver support ->

selct all in the:

Bootup logo LOGO->

-in the GRUB, in the file menu.lst fix this row:

kernel /boot/vmlinuz-2.6.29.3 root=UUID=d5b52903-5…. video=vesafb vga=0×0323 ro quiet

-in the file /etc/modprobe.d/blacklist-framebuffer.conf, comment this row:

#blacklist vesafb

-in the file /etc/initramfs-tools/modules, add:

fbcon
vesafb

-in the end update initramfs this command:

update-initramfs -u

In all my UBUNTU not load boot logo!!!!!!!!

---

### Post by deepspring on 2009-06-17
> **Lockheed said:**
> I am unable to run this command as I am being told another process is using those files.
When exactly should I run it? Before, during or after compilation?
Do you have Hardware Driver manager running? (installs nVidia and ATI drivers)

---

### Post by Lockheed on 2009-06-17
> **deepspring said:**
> Do you have Hardware Driver manager running? (installs nVidia and ATI drivers)

If you mean Hardware Drivers from Administration menu, then there is a green light by Nvidia 180 driver.

---

### Post by deepspring on 2009-06-17
> **Lockheed said:**
> If you mean Hardware Drivers from Administration menu, then there is a green light by Nvidia 180 driver.

I meant is the Hardware Driver applet actually running in the background when you are trying to run those commands?

You should run those commands after installing KernelCheck, when you get the following error:

```

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.29.4.postinst line 1186.
dpkg: error processing linux-image-2.6.29.4 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.29.4
```

---

### Post by Lockheed on 2009-06-21
> **deepspring said:**
> I meant is the Hardware Driver applet actually running in the background when you are trying to run those commands?

How do I check that?

---

### Post by deepspring on 2009-06-21
> **Lockheed said:**
> How do I check that?

Run the following command to see if the Hardware Drivers applet is running:

```
ps aux | grep jockey
```

If the Hardware Drivers applet is running you should see something like the following:

```

scott@beowolf:~$ ps aux | grep jockey
root     [COLOR="Red"]16273[/COLOR]  0.3  0.8  24244 17060 ?        S    11:47   0:01 /usr/bin/python /usr/share/jockey/jockey-backend --debug -l /var/log/jockey.log
scott    [COLOR="Red"]18452[/COLOR]  8.1  1.2  48064 25224 ?        S    11:55   0:00 /usr/bin/python /usr/bin/jockey-gtk

```

Note the numbers highlighted in red. These are the process id's, they will probably be different on your system. To kill (stop) the processes, run the following command for each process, replacing <num> with the process numbers on your system:

```
sudo kill -9 <num>
```

Then try purging and re-installing nvidia-common.

---

### Post by Lockheed on 2009-06-22
There is a problem. This is the outoput:
```
$ ps aux | grep jockey
root     10725  0.0  0.0   7528   908 pts/0    S+   09:33   0:00 grep jockey
```

The problem is that the 10725 number changes every second and by the time I run...
```
sudo kill -9 10725
```
...the actuall number already changed and I get
```
kill: No such process

```

---

### Post by deepspring on 2009-06-22
> **Lockheed said:**
> There is a problem. This is the outoput:
```
$ ps aux | grep jockey
root     10725  0.0  0.0   7528   908 pts/0    S+   09:33   0:00 grep jockey
```The problem is that the 10725 number changes every second and by the time I run...
```
sudo kill -9 10725
```...the actuall number already changed and I get
```
kill: No such process

```

You don't need to worry about "grep jockey", that command was used to filter the output of the ps command so we can easily see the commands we were looking for ("jockey-gtk" and "jockey-backend").

If the commands we were looking for were running, they would have shown up.

You should be able to purge and reinstall nvidia-common.

---

### Post by Lockheed on 2009-06-22
I was now able to successfully purge it but...

```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
[COLOR="Red"]Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30.postinst line 1186.
dpkg: error processing linux-image-2.6.30 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.30[/COLOR]

```

---

### Post by deepspring on 2009-06-22
When does that happen?

After the "sudo apt-get remove --purge nvidia-common" or "sudo apt-get install nvidia-common".

---

### Post by Lockheed on 2009-06-22
After 
```
dpkg -i linux*2.6.30*.deb
```

---

### Post by deepspring on 2009-06-22
Try purging nvidia-common. Then install the new kernel. Then re-install nvidia-common.

---

### Post by Lockheed on 2009-06-22
Ok, that seemed to have worked. Not much use of it, though, since I am stuck at boot with:


```

Starting up...
audit: cannot initialize inotify handle
Loading, please wait...
Gave up waiting for root device. 
(...)
ALERT! /dev/disk/by-uid/<various digits>. Dropping to a shell!
```

---

### Post by deepspring on 2009-06-22
I'm not sure how to help you with that error.

It could be one of:

[LIST]
[*]Missing kernel driver for your hard disk controller (least likely)
[*]Duplicate partition UID's (most likely)
[/LIST]
Try booting from one of the previous kernels. When you get into Gnome open up a terminal window and run the following commands and post the output:
```

sudo update-grub
sudo fdisk -l

```

I've never encountered that error before. Posting the output of those commands may help someone else help you.

---

### Post by master_kernel on 2009-06-22
Reference: [http://www.ubuntu.com/getubuntu/releasenotes/810#Boot%20failures%20on%20systems%20with%20Intel%20D945%20motherboards](http://www.ubuntu.com/getubuntu/releasenotes/810#Boot%20failures%20on%20systems%20with%20Intel%20D945%20motherboards)

> Users have reported slower than normal detection of SATA hard drives on systems with Intel D945 motherboards in Ubuntu 8.10. This may cause the system to drop to a busybox initramfs shell on boot with a "Gave up waiting for root device." error. Wait a minute or two and then exit the initramfs shell by typing 'exit'. Booting should proceed normally. If it doesn't, wait a bit longer and try again. Once the system boots, edit /boot/grub/menu.lst and add rootdelay=90 to the kernel stanza for your current kernel. (Bug 290153). 
[B]
EDIT:[/B] Also try to let GRUB reconfigure itself.
```
sudo apt-get install --reinstall grub
```

---

### Post by Lockheed on 2009-06-23
> **deepspring said:**
> I'm not sure how to help you with that error.

It could be one of:

[LIST]
[*]Missing kernel driver for your hard disk controller (least likely)
[*]Duplicate partition UID's (most likely)
[/LIST]
Try booting from one of the previous kernels. When you get into Gnome open up a terminal window and run the following commands and post the output:
```

sudo update-grub
sudo fdisk -l

```

I've never encountered that error before. Posting the output of those commands may help someone else help you.

I am not sure what do you mean by duplicate ID. If there is a new kernel it is normal that its UID is the same as the old one, isn't it?

Here is what you asked for:
```
~# sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30
Found kernel: /boot/vmlinuz-2.6.29.4
Found kernel: /boot/vmlinuz-2.6.28-12-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

```
# sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a53d359

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2089    16779861    7  HPFS/NTFS
/dev/sda2            2090       38913   295788780    5  Extended
/dev/sda5            2090       35204   265996206    7  HPFS/NTFS
/dev/sda6           35205       38403    25695936   83  Linux
/dev/sda7           38404       38913     4096543+  82  Linux swap / Solaris

```

and this is my menu.lst:
```
title		Win7
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


title		U9
uuid		087b9e3b-a65c-4890-9b0e-de019b0fff18
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=087b9e3b-a65c-4890-9b0e-de019b0fff18 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.30
uuid		087b9e3b-a65c-4890-9b0e-de019b0fff18
kernel		/boot/vmlinuz-2.6.30 root=UUID=087b9e3b-a65c-4890-9b0e-de019b0fff18 ro quiet splash 
initrd		/boot/initrd.img-2.6.30
quiet 

title		Ubuntu 9.04, memtest86+
uuid		087b9e3b-a65c-4890-9b0e-de019b0fff18
kernel		/boot/memtest86+.bin
quiet
```


**master_kernel**, I do not have Intel-based mobo. Besides, everything works fine with the 9.10 default kernel. Reinstallation of grub did not help.


I may add that during kernel compilation, I have disabled all SATA drivers except those for Nvidia, AMD and ACPI sata.

---

### Post by master_kernel on 2009-06-23
> I may add that during kernel compilation, I have disabled all SATA drivers except those for Nvidia, AMD and ACPI sata.

I am almost convinced you disabled the neccessary driver for your system here. When the system gives up waiting for the root device, the SATA drive is not found/loaded. Try recompiling without disabling any SATA options, and the new kernel should work fine.

For a fast(er) recompile, follow these steps (as root):
```
cd /usr/src/linux
cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
make xconfig   # Configure the kernel
make-kpkg clean
CONCURRENCY_LEVEL=3 make-kpkg --initrd kernel_image kernel_headers modules_image --append-to-version=-candela
```


Good Luck,
master_kernel

---

### Post by Lockheed on 2009-06-23
I did what you said just now - included all sata drivers into the compilation - but it made absolutely no difference.

---

### Post by master_kernel on 2009-06-24
> **Lockheed said:**
> I did what you said just now - included all sata drivers into the compilation - but it made absolutely no difference.
Now I'm stuck. Try the rootdelay=90 just for fun.

---

### Post by Lockheed on 2009-06-24
Tried that, too.
If it is impossible to install new kernel in Ubuntu, how to clean the mess after unsuccesfull compilations?

---

### Post by master_kernel on 2009-06-24
You just dpkg -r the packages and remove /usr/src/linux and /usr/src/linux-2.6.30.

---

### Post by Lockheed on 2009-06-24
Well, I am trying to 
```
dpkg -r linux-headers-2.6.30_386_amd64.deb
```
but all it gives me is
```
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in
```

---

### Post by Lockheed on 2009-06-24
Ok, I tried compilation for the tenth time and finally it worked!
But now I lost this ubuntu progress bar that masked all those commands being run in the background during bootup. Is it possible to get it back?

Also, **more important**, computer pauses for 20 seconds on this message:
```
Boot from (hd0,5) ext4 0820982-xxx-.....................
```
Previous kernel spent only under 1 second on this message and proceeded to "Starting up..." but this one keep HDD light on for like 20 mintues and onle then moves forward.

---

### Post by deepspring on 2009-06-24
> **Lockheed said:**
> Well, I am trying to 
```
dpkg -r linux-headers-2.6.30_386_amd64.deb
```but all it gives me is
```
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in
```
Leave the .deb off the end of the file name.

---

