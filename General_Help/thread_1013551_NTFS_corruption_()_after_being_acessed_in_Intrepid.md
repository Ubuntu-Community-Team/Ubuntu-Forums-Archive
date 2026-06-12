---
title: "NTFS corruption (?) after being acessed in Intrepid"
date: 2008-12-17
forum: General Help
---

### Post by Jeconti on 2008-12-17
Alright, so I have two external hard drives that I use to store media and music, both are formatted NTFS as I started using them before I got back into Linux.

After playing a movie from one of the drives in Ubuntu (8.04), I later came back to XP and wanted to watch a movie, only when I opened it up, explorer crashed. Thankfully it wasn't a sudden "goodbye every window on my desktop, this thing is effed" kind of crash. I got the illegal operation pop up, but was still able to access and open the file before letting explorer restart.

So, two questions.

1) What happened on the Ubuntu side to make XP freak out about accessing the drive?

2) Is there anyway to fix it?

Thank you as always,

---

### Post by adult swim on 2008-12-17
explorer crashing is not an uncommon event in windows.  does it crash every time you try to access the drive?

---

### Post by jessdog9001 on 2008-12-17
Well, there are a couple of possibilities. 

1: Ubuntu or Windows corrupted the file while accessing it. This isn't very probable because the NTFS drivers for both are very stable and have been tested a lot. However, if you lost power or restarted the computer while the hard drive was accessing the file, corruption is possible. If this happened, there's a good chance you can recover the data and fix the problem.

2: There was/is a problem with your drive, either temporary or permanent. In this case, you might not be able to recover the data, and you probably won't be able to fix the problem.

To try to fix any corruption on your hard drive, you can use [chkdsk]("http://support.microsoft.com/kb/315265") under the Windows command line to scan for any errors. You can also try using ntfsfix under Linux, which is part of ntfsprogs. However, I think chkdsk is more comprehensive and can fix a broader range of errors.

After running chkdsk, it will let you know if any errors were found and if they were fixed or not. If any "unrecoverable errors" were found, you should run a thorough test of your hard drive because it is likely that it is going bad. Otherwise, try accessing the file again under Windows and Linux and see if it works. 

Good luck, and let me know if you need any more details on running chkdsk or anything else.

---

### Post by Jeconti on 2009-01-22
Just to update as resolved, the issue was not using NTFS cross platform. The movie file I watched was the issue. Something with the thumbnail preview after being accessed by Ubuntu caused Explorer to crash.

Thanks to those that responded.

---

### Post by bodhi.zazen on 2009-01-22
> **Jeconti said:**
> Just to update as resolved, the issue was not using NTFS cross platform. The movie file I watched was the issue. Something with the thumbnail preview after being accessed by Ubuntu caused Explorer to crash.

Thanks to those that responded.

Thank you for that information. Even though this is an older thread that kind of feedback is very helpful.

---

