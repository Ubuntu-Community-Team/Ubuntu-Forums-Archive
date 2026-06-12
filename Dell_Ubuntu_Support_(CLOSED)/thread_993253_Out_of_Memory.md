---
title: "Out of Memory?"
date: 2008-11-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DManX04 on 2008-11-25
I installed Ubuntu using Wubi, upgraded to Intrepid, and have since installed Google Earth and whatever updates were made available to the OS itself. I have a year old Inspiron 1720, and I allocated to Ubuntu 15 GB of about 35 left on the hard drive.

Suddenly, after about a week, I am getting error messages saying I have no available memory. Firefox can't restore sessions. Open Office won't autosave and crashes when it tries to. I get an error saying that there is no memory in "home/donald/.openoffice/user/backup" and asks me to allocate more memory to that directory. It also freezes when I try and do a regular save as well. The thing is, that file doesn't exist, or at least it doesn't show up in any file viewer or search. Even if it did, how could I add more space to it? At startup, Open Office also tells me that some other user is trying to access a session of Office. I don't even know what that means. At first I thought it was just Open Office so I tried to download 3.0, hoping it would fix it, but I got an error saying that there wasn't enough available memory to save the download. Then the firefox restore issue came up after I had to restart the computer when Office crashed.

I have absolutely no idea what to do, but I really need this fixed. Any help is much appreciated.

---

### Post by linux_tech on 2008-11-25
what is output from
```
 dmesg
```

How much space is free on hd? Applications->Accessories->Disk Usage Analyzer

How much RAM do you have installed?  (post output)
```
free
```

---

### Post by upchucky on 2008-11-25
I suspect his /home directory is on the same partition as the os, if so then 15g is too small, as it appears that it is also backing up his files regularly which has used up the available partition space, this means his swap is crammed full also. 40g drive should be partitioned to have 20g to 25g for ubuntu sys, and the remainder for the /home partition.

---

### Post by DManX04 on 2008-11-25
Is there a way to fix that problem? As I said, I installed with Wubi, so I don't know if that has anything to do with it. Also, it's not a 40G hard drive, it's just that that is all the space left. Actually, there are only about 20 left after installing the Wubi install.

---

