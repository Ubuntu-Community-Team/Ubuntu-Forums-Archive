---
title: "Lost Ubuntu, Help!"
date: 2009-03-28
forum: General Help
---

### Post by MO-GSer on 2009-03-28
Hi All, 

I originally had XP professional installed and then installed Ubuntu and later installed Win 7.  After installing Win 7, Ubuntu was no longer an option (it's now using the Win 7 boot menu).  

So I got EBCD and attempted to fix the problem.  

On my first drive I have the following:

24mb   unallocated
83gb   Win XP (NTFS)
18gb   win files (NTFS)
282mb  swap
9.5gb  Ubuntu (ext2fs)

I'm using neogrub and this is the neogrub file:

# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# [http://neosmart.net/wiki/display/EBCD](http://neosmart.net/wiki/display/EBCD)

#This is our first entry
title		Ubuntu    
find --set-root /boot/vmlinuz-2.6.24-19-generic
root		(hd0,3) 
#Next Line: Translate (hd0,3) to Linux notation and set that as the root partition
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda4
initrd		/boot/initrd.img-2.6.24-19-generic
#End Ubuntu entry

This gets me to the Ubuntu selection but when I select it, I then get:
error 19 cannot mount selected partition

I'm sure it's something to do with my identification of what it is I want to mount/boot but cannot figure it out.  

This is my menu.lst from Ubuntu BEFORE I added Win 7:

default 0
timeout 10
title Ubuntu 8.04.1, 
kernel 2.6.24-19-generic 
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=31ffce31-c5fb-4540-9082-b54285698f54 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic


title Ubuntu 8.04.1, 
kernel 2.6.24-19-generic (recovery mode) 
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=31ffce31-c5fb-4540-9082-b54285698f54 ro single
initrd /boot/initrd.img-2.6.24-19-generic
(minus a lot of comments at the end of the Ubuntu menu.lst)

Any help would be greatly appreciated.  

Harry

I loaded Ubuntu Live and looked at the Ubuntu partition on my hard drive and I see that it is ext3 not ext2 so now I have to check if neogrub is giving the error or grub.  I was booting Ubuntu originally so grub should be able to read/mount the partition.

---

### Post by Xero Xenith on 2009-03-28
Hey there,

I'm not at all used to NeoGrub, and the way I'd approach this problem would be to restore the original GRUB settings and menu.lst, then correct it manually from there.

This can be done by burning this CD, and rebooting into it - 
[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

Rebooting into that disc, there should be the option to restore GRUB in the MBR. I think it's under Linux, or something (I'll check this in a second). _EDIT - just checked. Once you boot in, it's called "GRUB => MBR & !LINUX! (1)". This should do what needs to be done._

Let it do this, and you should only have one menu.lst file detected to choose from. Once that's all done, you can shut down the computer and put the disc to one side.

Now, reboot your computer - which of the options in the GRUB menu work now?

---

### Post by MO-GSer on 2009-03-28
> **Xero Xenith said:**
> Hey there,

I'm not at all used to NeoGrub, and the way I'd approach this problem would be to restore the original GRUB settings and menu.lst, then correct it manually from there.

Thanks for the response Xero but this has turned into a "challenge" for me.  I'm always in learning mode with Ubuntu and I'll restore the original grub as a last resort if I can't figure this out.  Restoring it should make it work like new.

thanks again,
Harry

---

