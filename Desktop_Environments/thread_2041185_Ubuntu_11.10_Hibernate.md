---
title: "Ubuntu 11.10 Hibernate"
date: 2012-08-12
forum: Desktop Environments
---

### Post by bd83862 on 2012-08-12
sudo apt-get install  hibernate

Need to have a swap partition equal to size  of RAM   if RAM is around  2 to 4 GB.
If  RAM is around 1 GB or less its desired to have swap size twice that of RAM.
If RAM is more than 4 GB swap can be less than RAM size. 
This is a general rule for swap size.

My swap is /dev/sda8. 

sudo blkid /dev/sda8. 
/dev/sda8: UUID="7b015ac3-95b3-4820-8fe4-c4f5580c2a1f" TYPE="swap" 

 /etc/fstab  entry is
UUID=7b015ac3-95b3-4820-8fe4-c4f5580c2a1f swap            swap    default           0       0

list swap space
sudo swapon -s
Filename                Type        Size    Used    Priority
/dev/sda8                               partition    4194300    1220    -1

mark swap space as hibernate/resume device
 cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=7b015ac3-95b3-4820-8fe4-c4f5580c2a1f

sudo dpkg-reconfigure uswsusp
 
If this is empty, the hardcoded default, /dev/snapshot, is used. This should be OK in almost all cases. Don't change this unless there is a good reason to do so.                       

 The device node through which uswsusp can talk to the kernel:

<leave blank>
ok

Perform checksum on image? 
No

Compress image?
Yes

Perform early write out?   
Yes

Perform early write out?   
Yes

Preferred maximum image size:
By default it gives size around half of  RAM.  Leave it like that.
If empty , enter a value half of RAM  in bytes. In my case with 4GB ram the value present
was
1878371860
I Didn't change.

log level:
2

Max log level:
2

Shutdown method:
Platform

Encrypt Snapshot:
No

Show splash screen:
No

Menu will exit and we will get the following on screen

update-initramfs: Generating /boot/initrd.img-3.0.0-17-generic


Hibernate should work now. If not then reboot once.
If you have just configured a swap space and have not rebooted the kernel 
will not see the swap space.


Profit

---

