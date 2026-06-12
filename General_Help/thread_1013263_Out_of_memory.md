---
title: "Out of memory?"
date: 2008-12-16
forum: General Help
---

### Post by DManX04 on 2008-12-16
I installed Ubuntu using Wubi, upgraded to Intrepid, and have since installed Google Earth and whatever updates were made available to the OS itself. I have a year old Inspiron 1720, and I allocated to Ubuntu 15 GB of about 35 left on the hard drive.

Suddenly, after about a week, I am getting error messages saying I have no available memory. Firefox can't restore sessions. Open Office won't autosave and crashes when it tries to. I get an error saying that there is no memory in "home/donald/.openoffice/user/backup" and asks me to allocate more memory to that directory. It also freezes when I try and do a regular save as well. The thing is, that file doesn't exist, or at least it doesn't show up in any file viewer or search. Even if it did, how could I add more space to it? At startup, Open Office also tells me that some other user is trying to access a session of Office. I don't even know what that means. At first I thought it was just Open Office so I tried to download 3.0, hoping it would fix it, but I got an error saying that there wasn't enough available memory to save the download. Then the firefox restore issue came up after I had to restart the computer when Office crashed.

I have absolutely no idea what to do, but I really need this fixed. Any help is much appreciated.

---

### Post by DManX04 on 2008-12-16
I also can't use the back button in Firefox now.


This was suggested in another thread, but I haven't gotten anymore information about it: *"I suspect his /home directory is on the same partition as the os, if so then 15g is too small, as it appears that it is also backing up his files regularly which has used up the available partition space, this means his swap is crammed full also. 40g drive should be partitioned to have 20g to 25g for ubuntu sys, and the remainder for the /home partition."*

---

### Post by ElectricMoose on 2008-12-17
Same problem happened to me, with kubuntu, I am guessing that both of us probably need to switch that number from 15 to 40, I am guessing that has something to do with partition space, if you do find out, please let me know.

---

### Post by jfloydb on 2008-12-17
I'm using Wubi as well.  I've just started so/and I have not had any problems.  But am I too understand from this discussion that, if I did the 15 gig installation, that that is all the disk space that is available for my Ubuntu OS and programs?  Again, I'm not having any problems, I simply want to know for sure.  Thanks...

---

### Post by ago on 2008-12-19
> **jfloydb said:**
> I'm using Wubi as well.  I've just started so/and I have not had any problems.  But am I too understand from this discussion that, if I did the 15 gig installation, that that is all the disk space that is available for my Ubuntu OS and programs?  Again, I'm not having any problems, I simply want to know for sure.  Thanks...

Correct, 15GB is enough in most cases

---

### Post by ago on 2008-12-19
> **DManX04 said:**
> 
This was suggested in another thread, but I haven't gotten anymore information about it: *"I suspect his /home directory is on the same partition as the os, if so then 15g is too small, as it appears that it is also backing up his files regularly which has used up the available partition space, this means his swap is crammed full also. 40g drive should be partitioned to have 20g to 25g for ubuntu sys, and the remainder for the /home partition."*

Not sure what is the point of backing up something in the same partition as the original files... You should fix the application that is consuming so much space

---

