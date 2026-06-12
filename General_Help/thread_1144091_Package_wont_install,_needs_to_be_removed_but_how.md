---
title: "Package wont install, needs to be removed but how?"
date: 2009-04-30
forum: General Help
---

### Post by ThaddeusW on 2009-04-30
UPDATE - Read on to my update post below.

Hello, 

I recently was experimenting with a custom kernel and upon installing it I found out I have a few problems with it. After installing I immediately attempted to preform a system update using "apt-get upgrade". It failed because my custom initrd was huge and nearly filled up /boot which caused the update to fail. My custom kernel was installed via apt and I uninstalled it using dpkg. 

So I uninstalled the kernel and I am now stuck with another problem. For some reason when attempting to install gnuradio it started to resume the update or something different. The gnuinstall failed and synaptic threw an error telling me to run "dpkg --configure -a" which fails. 

My package management is as of now unusable and I need to fix it. This is the error I get from dpkg:

```

sudo dpkg --configure -a

Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.30-rc3-custom
Cannot find /lib/modules/2.6.30-rc3-custom
update-initramfs: failed for /boot/initrd.img-2.6.30-rc3-custom
dpkg: subprocess post-installation script returned error exit status 1

```

Now its trying to install the bad 2.6.30 kernel initrd I compiled but keeps failing because I removed the two packages that were generated after I compiled the kernel. How do I stop this problem? Should I reinstall the bad 2.6.30 kernel and let the update resume?

I can try a few tricks like re installing the bad 2.6.30 kernel and then telling grub to boot using the Ubuntu 2.6.24 generic kernel and hard link the 2.6.30 initrd to /boot so there is room on boot for the update to continue. My boot partition is only 96MB in size and the silly initrd for my kernel was over 50MB.

---

### Post by freonchill on 2009-04-30
check the man page for apt-get

but i think its

apt-get package_name remove --force-yes
replace package_name with the package that wont let you install/reinstall

then try to install it again afterwards

---

### Post by ThaddeusW on 2009-04-30
> **freonchill said:**
> check the man page for apt-get

but i think its

apt-get package_name remove --force-yes
replace package_name with the package that wont let you install/reinstall

then try to install it again afterwards

That's the problem, apt-get will not do anything unless "dpkg --configure -a" completes. Anyone have any ideas? I cant even attempt to install the packages I removed for the custom kernel.

It looks like I painted myself into a corner. Its a complete catch 22. I cant complete "dpkg --configure -a" for initramfs-tools because of the missing kernel files and dpkg won't let me install the custom kernel because initramfs-tools isnt installed. I made a grave mistake removing the custom kernel packages. Well we all learn from our mistakes.

I see dpkg has force options but I am a bit hesitant to use them. Any one know how to force the install or a way to repair this problem? 

If this forum is unable to help me, are there any places I can look to for more detailed help on fixing apt problems?

---

### Post by ThaddeusW on 2009-04-30
UPDTAE:

I sort-of fixed the problem. I used the force option to reinstall the linux-image package and then ran "dpkg --configure -a" well it failed complaining about initramfs-tools. So I then ran "dpkg --configure initramfs-tools" and it finished the configuration of initramfs-tools because the kernel stuff was back in place. Then I ran "dpkg --configure -a" and I am back to my original problem of too little free space in /boot:

```
sudo dpkg --configure -a
Setting up linux-image-2.6.30-rc3-custom (2.6.30-rc3-custom-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.

gzip: stdout: No space left on device
mkinitramfs-kpkg failed to create initrd image.
Failed to create initrd image.
dpkg: error processing linux-image-2.6.30-rc3-custom (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 linux-image-2.6.30-rc3-custom

```

Here is the file listing of /boot:

```
ls -l /boot
total 97650
-rw-r--r-- 1 root root   422667 2008-08-21 00:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root    80049 2008-08-21 00:46 config-2.6.24-19-generic
-rw-r--r-- 1 root root    98016 2009-04-23 15:14 config-2.6.30-rc3-custom
drwxr-xr-x 2 root root     1024 2009-04-30 16:46 grub
-rw-r--r-- 1 root root  8030351 2008-10-01 18:52 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root  7614539 2008-09-30 17:41 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root 56722752 2009-04-30 16:49 initrd.img-2.6.30-rc3-custom
-rw-r--r-- 1 root root 20189184 2009-04-30 16:50 initrd.img-2.6.30-rc3-custom.new
drwxr-xr-x 2 root root    12288 2008-09-26 16:05 lost+found
-rw-r--r-- 1 root root   103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r-- 1 root root   905170 2008-08-21 00:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root  1112635 2009-04-23 16:32 System.map-2.6.30-rc3-custom
-rw-r--r-- 1 root root  1921464 2008-08-21 00:46 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root  2370544 2009-04-23 16:32 vmlinuz-2.6.30-rc3-custom

```

Look at the size of that initrd for my custom 2.6.30 kernel! Now is there a way to somehow fix this? I was thinking of moving the initrd to another partition and then hard linking the initrd to /boot to free up some space. Don't know if a hard link will work though. Oh and yes i know this will render the 2.6.30 kernel useless but thats ok, I am going to tell grub to default boot my previous ubuntu generic kernel.

---

### Post by drs305 on 2009-04-30
To clear the error message, try just moving this file (assuming it's the problem kernel):
```

sudo mv /var/lib/initramfs-tools/initrd.img-2.6.30-rc3-custom  $HOME/Desktop/initrd.img-2.6.30-rc3-custom
sudo dpkg --configure -a

```

If that corrects it you can delete it.

---

### Post by ThaddeusW on 2009-04-30
Still at it and yes I soft linked the initrd image to boot and ran "dpkg --configure -a" and it ran and completed. FINALLY! Fixed the problem myself. I guess sometimes you have to RTFM and grow a pair and just dive in. Now I haven't re-booted yet but I am crossing my fingers. I fixed /boot/grub/menu.lst to point to my old working Ubuntu generic kernel instead of the bad 2.6.30.

---

