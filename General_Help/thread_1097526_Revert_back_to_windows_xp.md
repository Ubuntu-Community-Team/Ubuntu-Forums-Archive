---
title: "Revert back to windows xp"
date: 2009-03-16
forum: General Help
---

### Post by mrayo84 on 2009-03-16
Sony VAIO VGN-FJ290P
WIndows XP 

I was trying to do a dual boot of XP and Ubuntu 8.10. At the install menu where a graph is shown showing MS WINDOWS XP and where Ubuntu will be installed, I clicked on FORWARD and another menu popped up. After about 20 monites or so, it gave me an error message saying that it there is an error somehtign something. I stopped the install and restarted my notebook. WIndows XP was still working fine. So I tried to reinstall Ubuntu for a dual boot. THIS IS WHERE MY PROBLEM STARTED. When I reached the graph showing the partitions (the green horizontal bar graph), IT DID NOT SHOW ME MY WINDOWS XP! Where could it have been? And the options at the bottom were down to just 2: MANUAL and somehting like GUIDED with a subcategory showing "100% something somehting". 

I chose the "GUIDED" option. WHERE IS MY WINDOWS XP NOW? WILL I BE ABLE TO RECOVER IT? MY FILES, DOCUMENTS, PICS EVERYTHIGN???? 

I can't access the VAIO recovery utility. This utility is found, in XP, by clicking the Start menu... This utility can restore my notebook to its factory settings. WHERE IS IT NOW, AND HOW WILL I BE ABLE TO ACCESS IT? 

I AM SUCH A DUMB DUMB...jelo.rayo@gmail.com

---

### Post by blazemore on 2009-03-16
So you CHOSE the option "Guided: Use Entire Disk"

You then checked over what the installer was going to do, and CHOSE to go ahead with the installation, deleting your existing partitions and creating new ones, obviously heeding the advice to check your installation settings and going back to change them if necessary.

I don't see what's the problem, sounds like a textbook installation. Of course, if there were any problems, you wouldn't have gone ahead with it.

---

### Post by mrayo84 on 2009-03-16
So my WIndows XP is gone forever???

---

### Post by Admiral Yi on 2009-03-16
If you erased the partition with Windows XP on it (which it would appear you did) then yes. I don't quite know how you made this mistake, what with all the messages telling you that repartitioning would wipe the hard drive....

---

### Post by ad_267 on 2009-03-16
> **mrayo84 said:**
> So my WIndows XP is gone forever???

Until you use your Windows XP CD to reinstall it anyways. I'd be more worried about any documents or other important stuff you had on the hard drive. There are some tools available that can recover files from deleted partitions.

---

### Post by abo999 on 2009-03-16
Probably not a good time to talk about backups?

---

### Post by blazemore on 2009-03-17
It's shame you'll have to spend time re-installing, but it's not a problem.

Just reinstall Windows, and restore your files from your latest backup.

I'm cruel.

---

### Post by thelugnut on 2009-03-19
It is probably too late for this, but I will post it anyway.

When I partioned my hard drive I made four partitions: one for Windows XP, one for a solid Ubuntu release, one for any new distributions I might want to try, and one for data. The Windows partition is ntfs, the two linux partitions are ext3 and possibly ext4 ( for jackalope) and the data partition is formatted in FAT32. 

Ubuntu can read and write to the FAT32 partition as can Windows XP.

With this arrangement I can ( and have) screwed up Windows without losing anything, I can (and have) screwed up the Ubuntus without losing any data, and I don't mess with my data partition except to back it up once in awhile.:)

---

### Post by issih on 2009-03-19
I'm afraid it is more than likely you have nuked your xp install completely. On the assumption you want to save anything you can you should NOT boot from the hard drive. Instead launch from the ubuntu live cd. Now check that you have lost the xp partition. Open a terminal (Applications->Accessories->Terminal) and then enter:

```
fdisk -l
```

That will list all the partitions on your hard drive. If theres only one formatted as ext3 and a teeny one formatted as swap, then you have wiped windows.

If there is an ntfs partition lurking about you might just have some hope.

If its gone, then you need to try something like this:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

But theres no guarantee that will get you back anything, let alone everything.

Hope that helps

---

### Post by sandy8925 on 2009-04-08
Didn't you say XP was working fine. And that after that when you booted to install it showed the graph as you said ? But in that case the installation hadn't even started and XP should still be there. Maybe you clicked on the "Guided - Use entire disk" option and hence it shows the whole graph with Ubuntu without XP.

Or I guess I missed something....

---

