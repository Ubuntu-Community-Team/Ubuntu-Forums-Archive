---
title: "Gparted Question"
date: 2009-01-10
forum: General Help
---

### Post by Jameshardy88 on 2009-01-10
Hey i was just wondering about resizing my ubuntu partition. I currently dual boot windows xp with intrepid (Using almost exclusively ubuntu). However i know wish to run a quite large windows program (16gb) that unfortunately Wine can't really handle. As my windows partition was minimised to virtually nothing it is no longer large enough to install it on it. Can i use the gparted program to make my ubuntu partition smaller adding the freed space to my existing windows partition without losing any data?

---

### Post by Jameshardy88 on 2009-01-10
-

---

### Post by chriskin on 2009-01-10
you can do that using the gparted live cd 
you just have to shrink the partition freeing the space that is near the windows partition and then expand the windows partition 

i do not know , yet, if the windows partition will be ok after expanding, it might have problems

with data partitions, i never had any problem, i do not know what will happen to the one with windows

---

### Post by mgol on 2009-01-10
I don't know if changing Windows partition size would be safe using GParted, but You can resize Ubuntu partition, just not being inside in this Ubuntu. ;)

Boot Your computer using Ubuntu LiveCD, there is gparted installed (as far as I know).

---

### Post by Jameshardy88 on 2009-01-10
how can i safely make my windows partition larger?

---

### Post by dcstar on 2009-01-10
> **Jameshardy88 said:**
> how can i safely make my windows partition larger?

I have resized NTFS partitions without any problems at all, just reboot Windows afterwards and let it sort out the new partition size for itself.

With any partition change you should back up any data in case it goes wrong.

---

### Post by mgol on 2009-01-10
> **dcstar said:**
> I have resized NTFS partitions without any problems at all, just reboot Windows afterwards and let it sort out the new partition size for itself.

I haven't seen any partition-enlarging utility in Windows XP... There is one in Vista, however, it allows only to enlarge it to the "right" (lol).

Jameshardy88, I'm pretty sure there is some free partition manager for Windows which will allow You to do this. You can use Partition Magic, if You have it (though it's not free). I suppose it's not Linux-connected information, though... ;) You should ask in some Windows forum.

---

### Post by Shazaam on 2009-01-10
dcstar is correct. And, there is NO need for ANY special partitioning program for Windows XP. Gparted will work fine using the livecd.
To make the Windows partition larger, boot the Ubuntu livecd (adjust your pc's bios boot order). Open System>Administration>Partition Editor. Highlight the Ubuntu partition and click "Resize/Move". A window will open with a bar. On each end is a pointer. Depending on your partition locations move either the left or the right pointer to shrink the Ubuntu partition and then click Apply. After the Ubuntu partition is resized it is a simple matter to expand the Windows XP partition in the same way.
As far as defragmenting the Windows partition it is up to you (recommended). The only time it is mandantory is before you shrink a Windows partition.

---

### Post by -kg- on 2009-01-10
Yes, GPartEd should (relatively) safely resize an XP partition...it's Vista that sometimes has some issues.

> I haven't seen any partition-enlarging utility in Windows XP

There is one...it's called Partition Manager and you should be able to find it through the Windows Help files.

---

### Post by mgol on 2009-01-10
OK, I might be wrong. My gparted allows hardly any modification of ntfs partitions, that's why I posted it - maybe I'm just missing some libraries...

---

### Post by jskandhari on 2009-01-10
> **Jameshardy88 said:**
> Hey i was just wondering about resizing my ubuntu partition. I currently dual boot windows xp with intrepid (Using almost exclusively ubuntu). However i know wish to run a quite large windows program (16gb) that unfortunately Wine can't really handle. As my windows partition was minimised to virtually nothing it is no longer large enough to install it on it. Can i use the gparted program to make my ubuntu partition smaller adding the freed space to my existing windows partition without losing any data?

Y dont you simply borrow a frndz Hdd external install the Win on it .. and Run the Program.. else for one program you will be f structure.. i.e ubuntu partiand stuff and by mistake you go wrong ... you will be in for repairing everything

---

### Post by Jameshardy88 on 2009-01-11
ok thanks all ill give it a go and see what happens

---

### Post by Jameshardy88 on 2009-01-11
> **jskandhari said:**
> Y dont you simply borrow a frndz Hdd external install the Win on it .. and Run the Program.. else for one program you will be f structure.. i.e ubuntu partiand stuff and by mistake you go wrong ... you will be in for repairing everything


This was exactly what i did however unfortunately the program won't load by this method, after reading some sites apparently this is a common problem and it insists on loading from the directory that it recommends, normally that would be an ideal solution however in this case i don't think its an option =(

---

### Post by stanz on 2009-01-11
I've also used gparted to resize ntfs - either way (make larger/smaller) - with no problems.
With xp - I defrag'ed and cleaned up things, so it didn't freak out to much. ;)
I've also kept m$ in the front of the drive:
| m$ | Ubuntu | swap |

---

