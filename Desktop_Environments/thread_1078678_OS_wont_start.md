---
title: "OS wont start"
date: 2009-02-23
forum: Desktop Environments
---

### Post by hot dog on 2009-02-23
Yesterday, I dual booted Windows 7 Beta, with Ubuntu...  I was able to boot into either OS without problems...

Then I decided not to have Ubuntu on on the Hard Drive, so I Went into "disk management" in Windows, right-clicked on the Ubuntu partitions and then deleted them.  When the extra hard drive space became "unallocated", I extended the Windows Partition "C" back to normal, so I'm back to my two original Windows Partitions, C & D. 

Now, on restart, I get this message: Grub Loading Stage 1.5
                                     Grub loading, please wait...
                                     Error 22

It sits on this screen and will not do any thing else...
I don't understand why "Grub" is on the Hard Drive still since I deleted the Ubuntu partitions.  I just want to be able to boot back into Windows 7...

I suppose I could reinstall, but I would like to keep the files the way they are on the Windows Partition...

I inserted the Window 7 installation disk and tried to do a start up repair, but it was

---

### Post by taurus on 2009-02-23
If you installed GRUB to MBR, then it will look for /boot/grub/menu.lst on your Ubuntu partition.  Removing Ubuntu from the harddrive would cause GRUB to get confused!  Therefore, you need to fix your MBR by removing GRUB as well.

There are many ways and here is one of them.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

