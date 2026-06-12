---
title: "help with hard drive icon on desktop"
date: 2006-08-16
forum: Desktop Environments
---

### Post by amiga1200 on 2006-08-16
Using ubuntu v6.06 (64bit)

I mounted a secondary hard drive that i installed (going by a howto). I put the line:

/dev/hdb1   /media/work  ext3    defaults     0 0

into my /etc/fstab file. Ran some chmod (777 i think it was). It has mounted seemingly fine and i can access it and write to the drive...My problem is that there is a icon on my desktop showing this new drive (which i have called 'work').
I dont know how to tell my os that i dont really want the icon showing on my desktop for now ?
Any help appreciated.

I do have another question: Regarding external usb hard drive formatted ntfs.  I can read this device when plugged in. But I cant write to it. Any help or links if this was covered already ?

Im pretty much new to having linux as my main desktop..(im really trying). Im happy that my raw canon picture files load in and are opening in thee image editor now!
 
Thanks
D

---

### Post by aysiu on 2006-08-16
NTFS is read-only. Reformat it as something else (Ext3/FAT32) if you want consistent, reliable write ability.

For the drive, Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Desktop > Volumes_Visible

or...

mount it somewhere else--instead of /media/work, mount it to /work. Anything in /media will show up on the desktop.

---

### Post by mgor on 2006-08-16
i don't think there is a way to selective show/hide harddrive icons on the desktop, but there's show OR hide option in gconf, launch the editor: `gconf-editor` and look at 'volumes_visible` in apps/nautilus/desktop.

regarding ntfs write support, take a look at what google has to offer[0]. i haven't had a ntfs partition in years, so that's the best i can do.

[0] [http://www.google.com/linux?hl=en&lr=&q=ntfs+write&btnG=Search](http://www.google.com/linux?hl=en&lr=&q=ntfs+write&btnG=Search)

dang, someone else posted before me. But, there is reliable NTFS support these days (i think it's using wine and some native windows dll's). but reformatting it is still my main advice.

---

### Post by 505 on 2006-08-16
> **amiga1200 said:**
> I do have another question: Regarding external usb hard drive formatted ntfs.  I can read this device when plugged in. But I cant write to it. Any help or links if this was covered already ?

The NTFS drivers in the Ubuntu ditribution only support reading NTFS drive, writing is considered experimental. If you want read/write NTFS drives search this forum for 'ntfs-3g' There is a pretty easy how-to (in the forum section, I think). You just need to add to repositories and install it.

(I know ntfs-3g works for mounted drives, I not sure it also works for plug-n-play drives (auto-mounted))

---

### Post by mgor on 2006-08-16
heh, look what i found[0] a couple of threads down under "new posts".

[0] [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

