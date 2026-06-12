---
title: "Win7 error &quot;The disk structure is corrupted and unreadable. &quot; after Ubuntu access"
date: 2010-10-17
forum: Desktop Environments
---

### Post by kyllikki on 2010-10-17
I have experienced data corruption on my Windows partitition after accessing it from Ubuntu (Maverick 10.10).  I am not doing anything special to access the Windows partition - just using the built-in method provided by Maverick.

After creating files/folders in Ubuntu and booting into Windows, directories that I try to access that were modified in Ubuntu cause the following error message when modifying files/folders:

```
"The disk structure is corrupted and unreadable." 
```

After running chkdsk, access to erroneous files are restored but new directories that were created in Ubuntu are removed, with data being lost.  This behaviour isn't always reproducible, but I concerned that some data corruption has occurred.

---

### Post by iDleR on 2010-10-17
By saying the built-in method do you mean clicking inside nautilus on the partition icon?

---

### Post by kyllikki on 2010-10-17
> **iDleR said:**
> By saying the built-in method do you mean clicking inside nautilus on the partition icon?

Yes.

---

### Post by kio_http on 2010-10-17
The first step would be to run chkdsk in windows (Right click on partition properties in Mycomputer I think)

Secondly your hard drive itself may be failing.

---

### Post by kyllikki on 2010-10-24
Chkdsk didn't detect any problems.  About the same time the data was lost some errors were reported to the event log but there was a direct correlation between modifying data in Linux and the events appearing.  The events have not occurred since I stopped writing to the Windows partition from Linux.  I don't think the disk itself is the problem, I had it replaced recently.

---

### Post by kyllikki on 2010-10-24
I think that possibly moving to the EXT4 file system was the problem.  I have added "nodelalloc" to fstab and hope this fixes the problem.

---

### Post by amilkh on 2012-07-08
> **kyllikki said:**
> I think that possibly moving to the EXT4 file system was the problem.  I have added "nodelalloc" to fstab and hope this fixes the problem.

I know this is an old thread, but I am getting the same issue on Ubuntu 12.04 LTS with a dual-boot configuration with my Windows 7.

Luckily, I was able to recover my files by running as Administrator:
```
chkdsk /F
```

Can anyone please explain this fix?

-Amil
[http://www.amilkhanzada.com/](http://www.amilkhanzada.com/)

---

### Post by wildmanne39 on 2012-07-08
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

