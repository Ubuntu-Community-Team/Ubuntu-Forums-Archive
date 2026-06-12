---
title: "Full disc encryption: initrd.img missing after upgrade"
date: 2009-01-04
forum: General Help
---

### Post by mes on 2009-01-04
Hello community,

I am running 8.04 with full disc encryption (installed from the alternate CD).

I tried to upgrade to 8.10, but the upgrade failed at installing the linux kernel package. From what I can tell my seperate /boot partition run out of disc space. So I moved the old kernel files from /boot to /tmp and retried, again without success.
Now the stupid part: When moving the kernel files back I forgot the initrd.img file. So after the next reboot I just got a File Not Found error in grub and am now unable to boot my Laptop. 

Things I tried to get back to my data: 

1) I booted into WinXP and used freeOTFE to mount the encrypted part under Windows, which works fine. However, on the encrypted partition Ubuntu puts an LVM2 setup, which in turn can't be used from Windows, at least from what I understand. 
There is a tool called explore2FS which supports reading LVM, however, it has its own HDD detection method and can't use the virtual drive freeOTFE creates. 

2) I tried copying initrd images from other Ubuntu installations into my /boot partition. None of them gave me the expected  passphrase prompt though but just stopped in Ash after a while.

From what I understand the initrd.img is created from the individual kernel setup after installation. So I guess I need a initrd image that includes the encryption specific parts. 

So, can anyone help me with this mess? From my own analysis I would need either a method to read LVM volumes from a virtual drive under windows or an initrd image that lets me decrypt my HDD. 

Any further ideas are of course very much appreciated. 

More details: 

2.6.24-22-generic is the kernel version I currently have on /boot that is missing the initrd image. 

Detailed disc setup: 
/dev/sda1           ext2       /boot
/dev/sda2           ntfs       windows
/dev/sda3           extended   

/dev/sda3 is encrypted and contains the LVM setup.

Please let me know if you need any more details. 

Best regards,
Eric

---

### Post by dcstar on 2009-01-04
> **mes said:**
> 
.......
Now the stupid part: When moving the kernel files back I forgot the initrd.img file. So after the next reboot I just got a File Not Found error in grub and am now unable to boot my Laptop. 
.......
2.6.24-22-generic is the kernel version I currently have on /boot that is missing the initrd image. 
.......

This command will create new initrd.img files, but you have to be running to use it.
```
update-initramfs -k all -u
```
I assume if you run it on another Ubuntu machine with the same kernel running then you can copy the file to your other system.

---

