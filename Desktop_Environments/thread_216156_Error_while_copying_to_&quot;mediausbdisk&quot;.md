---
title: "Error while copying to &quot;/media/usbdisk&quot;"
date: 2006-07-15
forum: Desktop Environments
---

### Post by venkataramanam on 2006-07-15
I am trying to copy some files onto a Transcend 128MB USB pen-drive. I get an error "There is not enough space on the destination"; I have seen a couple of related posts. One suggestion was to empty TRASH and recheck. Though the file-manager says 0 items, the free space is a cheap 1.8 MB while it is actually close to 128 MB(the full capacity of the drive). Someone else had suggested another workaround of trying to fill up the USB drive on Windows-OS and then emptying it in Ubuntu to free space virtually. My Ubuntu does not like that even. So what do you think I should do? Any help appreciated please. Thanks in advance.

Thanks
Venkat

---

### Post by aysiu on 2006-07-15
Did you, in fact, empty the trash on the pen drive (not the trash on your hard drive)? It's probably a hidden folder, so if you're using Ubuntu, press Control-H, and you should see what's in there.

---

### Post by venkataramanam on 2006-07-17
> **aysiu said:**
> Did you, in fact, empty the trash on the pen drive (not the trash on your hard drive)? It's probably a hidden folder, so if you're using Ubuntu, press Control-H, and you should see what's in there.

I am sorry for the late response. You are right, I didn't check the trash on USB drive. Coming from a windows background, I didn't realize that there is a trash for every drive ( I suppose );

I cleared the trash. It restored some space into USB drive, but not to its full capacity. What actually happened was... the trick suggested in my post earlier worked; i.e., fill up the disk on Windows and empty it on Ubuntu. To make it a lil clear ....

Let us say, full capacity of the drive is F mb;
Fill X mb on Windows; ( X <= F )
Then empty X mb on Ubuntu.
Now the net space that can be filled up on Ubuntu = X mb

I don't know what is happening. But this is how it worked.
May be Ubuntu is caching the storage space left on USB drive and somehow it is recognizing the drive.

So, probably this might have been reported by some other people as well. If you know of some workaround or clean-fix, please suggest.

Thanks
Venkat

---

### Post by vhof on 2007-07-20
I had the same problem. 
I emptied the regular trash - in "Gnome" / Ubuntu - that can icon on bottom-right... Right-click, then Empty Trash.  Then copied the file to Disk-on-key, worked!...
Thanks for help..:guitar:

---

