---
title: "Dell e1505n recovery discs"
date: 2007-08-19
forum: Dell  Ubuntu Support
---

### Post by johnmikejerry on 2007-08-19
I feel really stupid about this, but I managed to wipe out the recovery partition on a Dell e1505n, and I need to get it back. Does anyone have any idea about how to get recovery discs? Or any other ideas?

---

### Post by mike999999 on 2007-08-20
Perhaps one of your fellow 1505 owners will dd you a copy?

??

---

### Post by crazedgremlin on 2007-08-27
Haha, I did the exact same thing.  I wiped it when I did a fresh installation of Kubuntu.  It would be nice if Dell would make an ISO available of the recovery partition or would just give you some discs.

---

### Post by jaspreet on 2007-08-28
> **crazedgremlin said:**
> Haha, I did the exact same thing.  I wiped it when I did a fresh installation of Kubuntu.  It would be nice if Dell would make an ISO available of the recovery partition or would just give you some discs.


Do you mean recovery partition for XP? you may like to check this link from Dell forums:
[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_winxp&thread.id=214841](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_winxp&thread.id=214841)

---

### Post by crazedgremlin on 2007-08-28
No, I mean the partition that comes with the ubuntu dells that includes Dell's custom installation of Ubuntu 7.04 along with some hardware diagnostics.

---

### Post by NickWV on 2007-08-31
same here, anyone care to post the partitions?

---

### Post by crazedgremlin on 2007-08-31
Actually, it's on  [dell's linux wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions")

 Partition 	 Type 	 Mount Point 	 Size
Partition 1 (primary) 	Utility Partition (UP) 	n/a 	32 MB
Partition 2 (primary) 	Reinstall Partition (CP) 	n/a 	2 GB
Partition 3 (primary) 	Linux 	/boot 	200 MB
Partition 4 (extended) 	Extended 	n/a 	Swap + rest of disk
Partition 5 (logical) 	Swap 	n/a 	(1.3 x RAM) + 10 MB
Partition 6 (logical) 	Linux 	/ 	Rest of disk

---

### Post by NickWV on 2007-09-03
> **crazedgremlin said:**
> Actually, it's on  [dell's linux wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions")

 Partition 	 Type 	 Mount Point 	 Size
Partition 1 (primary) 	Utility Partition (UP) 	n/a 	32 MB
Partition 2 (primary) 	Reinstall Partition (CP) 	n/a 	2 GB
Partition 3 (primary) 	Linux 	/boot 	200 MB
Partition 4 (extended) 	Extended 	n/a 	Swap + rest of disk
Partition 5 (logical) 	Swap 	n/a 	(1.3 x RAM) + 10 MB
Partition 6 (logical) 	Linux 	/ 	Rest of disk


that is just the listing of what the partitions are, I need the actual data...

---

### Post by crazedgremlin on 2007-09-03
Oh yeah, that *would* make sense.  Sorry ^_^
I wish dell would post an iso on the linux wiki.

---

### Post by vincentvee on 2007-09-03
thats cool, didn't know they came with a recovery partition
of course we can't get an ubuntu dell over here in OZ, which is fine by me really, just hoping that when mine shows up i have no trouble installing ubuntu cause the disk will be in on first boot


> **crazedgremlin said:**
> No, I mean the partition that comes with the ubuntu dells that includes Dell's custom installation of Ubuntu 7.04 along with some hardware diagnostics.

---

### Post by Afishionado on 2007-09-03
BTW, on my machine (an Inspiron 1420n), the DellUtility partition seems to have a Windows OS installed on it; when I mount it, I see lots of COM, BAT, and EXE files. I haven't tried to boot it.

Anybody know what's actually there? Finding that there really is still a Microsoft OS hidden on my Ubuntu machine is really my main disappointment with the 1420n. :(

To this original poster: Is this link more helpful?
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages)

---

### Post by crazedgremlin on 2007-09-03
The thing with COM, BAT, and EXE files is the recovery partition.  It brings the hard drive back to the original state with Dell's installation of Ubuntu 7.04.

---

