---
title: "Has anyone seen this?  File Copy Problem"
date: 2007-03-23
forum: Desktop Environments
---

### Post by Gallardo Spyder on 2007-03-23
This is an odd one...

I am running Edgy 6.10 and I have an internal 80gb (where Edgy is installed), an external Firewire 250gb drive and a 150gb USB drive connected to this particular machine.

I have both externals formatted as Fat32 - and both are used as network storage for my other Linux and Windoze machines.

I downloaded Frugal Linux DVD Iso (which is about 4.3gb) to my Local 80gb drive.  I go to copy it to my firewire drive (attached to the same machine mind you) so I can get to it with my test linux server.  It copies 4.094GB and completes without error...  However the file size of the original file is 4.31GB....

I copy much more GB of data to my external drives - but I cant recall any single file that was over 4gb.  So don't know if this is a new problem or one that I have had but not run into before...

Am I running into some limit of file size for copying?  I have used 3 different file managers to copy the file - but all do exactly the same copy just over 4gb - and then completes with no errors...

(It does exactly the same thing on both the Firewire and the USB drive)...

Any help or advice would be great!

Thanks,
GS

---

### Post by thingy on 2007-03-23
Yep! You hit the FAT32 4GB max file size limit.

See this [http://en.wikipedia.org/wiki/Fat32](http://en.wikipedia.org/wiki/Fat32)

---

### Post by stalker145 on 2007-03-23
It seems that you are running into the limitations of the FAT32 system.

[http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table)
[http://www.windowsitpro.com/Articles/ArticleID/38803/38803.html](http://www.windowsitpro.com/Articles/ArticleID/38803/38803.html)

FAT32 is limited to a single file size of 4GiB. You may need to split the file somehow or convert the file system to another, less stringent, one.

---

### Post by Gallardo Spyder on 2007-03-23
I think I remember that in the back of my mind somewhere - and suspected as much.

Dang it.  Since I cannot burn DVD's with Ubuntu (still don't know why and have tried everything).  I have to use Windozes to do it - thus the need to copy it to the shared drive.  

I will go at it with my 8gb flash drive - format it to NTFS and go that route.

Thanks for the confirmation...

---

### Post by mgmiller on 2007-03-23
Another option is to format your external drives in ext2 or ext3 and add ext support to your windows box. 
Get the driver here:   [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

