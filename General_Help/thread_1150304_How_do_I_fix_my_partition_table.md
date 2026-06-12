---
title: "How do I fix my partition table?"
date: 2009-05-06
forum: General Help
---

### Post by iammeagain on 2009-05-06
I was using Ubuntu to resize a partition for windows. It froze in the middle of it and now my when I boot I get:
> A disk read error occurred
Press Ctrl+Alt+Del to restart

I do have some info I would like to have to get off, just because I don't remember what sites I downloaded some of it from. 
My guess was the mbr or partition table was messed up. I did a windows recovery with the install disk and used fixboot, but it didn't make any difference.
I believe the hd is ntfs. I haven't used linux for a few years now but I'm not a total noob. I fixed a partition table before I believe with gparted I just don't remember what the steps were. Any tips/link/suggestions greatly appreciated.
I can provide command outputs idk what ones would be the most handy.
Thanks :)

---

### Post by stretch427 on 2009-05-06
Hey! If your using Gparted you should just be able to boot from the live CD and follow instructions. 
If your not worried about what's on the disk just used use a guided partition and set it however you want. 
If you have important files maybe just back them up on an external and away you go. 

But yeah for Gparted you should just be able to boot straight from the CD. As long as you have boot CD/DVD selected in the BIOS. 
I hope this helps!
Cheers!

---

### Post by iammeagain on 2009-05-07
Well I can reformat it and all, but I would rather not because I have to reinstall an OS and find drivers... etc.  
I wanted to fix the disk read error, it seems just to do with booting since Live cd's read the info off of it fine. I backed up my personal stuff off it already with the live cd.

Would this idea work? Use the backup program on gparted to backup the OS then reformat and put the OS back onto the hd? Since the info on the disk is fine its just the booting I think is messed up? Or would the problem I am having get backed up as well?

---

### Post by stretch427 on 2009-05-08
Alright I looked into it a bit.  
Go into your BIOS and just hit load fail-safe defaults and reboot. 

It should be as easy as that. 

I could be wrong. But thats what some other people have said worked.

---

### Post by Egi_Power on 2009-05-08
Hi!

> I did a windows recovery with the install disk and used fixboot

Did you try:
```
fixmbr
```
?
You could check out the following link, if you need help how to use the command:
[http://pcsupport.about.com/od/termsf/p/fixmbr.htm]("http://pcsupport.about.com/od/termsf/p/fixmbr.htm")

Best regards,

Egi_Power

---

### Post by anaconda on 2009-05-08
There are free recovery programs for linux, which can search existing partitions and repair the mbr and partitiontable.

But sorry. can't remember the names of those programs just now..

---

