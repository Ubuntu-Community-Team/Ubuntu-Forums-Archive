---
title: "booting in Windows 7 corrupts grub loader"
date: 2010-04-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aman.agx on 2010-04-21
I got my new Dell Studio 15 and tried to install ubuntu 9.10 on it alongside windows 7. installed fine. but when I tried to boot into ubuntu after booting into windows once... the grub was corrupted and I was not able to boot into any OS. I tried installing Ubuntu again and faced the issue again. This one comes with a system partition for Windows loader. can it be interfering with Grub?
Any solutions?

---

### Post by oldfred on 2010-04-22
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)

---

### Post by carl4926 on 2010-04-22
I always erase the factory install of windows and put in one using a full DVD.
But if you can't put your hand on a install DVD, that could be tricky.
What about creating a boot flash drive
or [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by reiki on 2010-04-22
I had this issue on my Dell Zino HD as well. Make sure you still have your liveCD available as you're probably going to screw up GRUB2 one more time.

Boot into Windows. Using the Add/Remove programs, uninstall Dell DataSafe local.

That was the culprit on my Dell box. Once I removed that program, I didn't have issues with GRUB2 being corrupted by windows again.

---

### Post by sunk8 on 2010-04-22
> **aman.agx said:**
> I got my new Dell Studio 15 and tried to install ubuntu 9.10 on it alongside windows 7. installed fine. but when I tried to boot into ubuntu after booting into windows once... the grub was corrupted and I was not able to boot into any OS. I tried installing Ubuntu again and faced the issue again. This one comes with a system partition for Windows loader. can it be interfering with Grub?
Any solutions?

Hey, you might try WUBI and install within Windows itself...
Agreed that it would be a bit slow, but you wouldn't face this issue...

Second solution: Lose Windoze altogether...

---

### Post by matrix13 on 2010-05-12
I have the same problem of Windows7 corrupting GRUB2. I experienced this with ubuntu 9.10 and 10.04. I use Dell Studio 14 laptop. You said the culprit is Dell Data Safe.

But I did not experience any problem with Ubuntu 8.04 on the same machine. Windows7 didnt corrupt the legacy GRUB. Why is that?
Is this the problem of Dell Data Safe only or related to GRUB2 also?

Thanks and Regards

---

### Post by oldfred on 2010-05-12
The MBR of a computer is reserved for booting. Some genius of a software guru noticed the windows (and old grub)  did not use the full sector and decided to hide serial numbers or special data in the remaining space. Grub2 is slightly larger and now they conflict.

---

### Post by anastasiaw on 2010-05-12
> **reiki said:**
> I had this issue on my Dell Zino HD as well. Make sure you still have your liveCD available as you're probably going to screw up GRUB2 one more time.

Boot into Windows. Using the Add/Remove programs, uninstall Dell DataSafe local.

That was the culprit on my Dell box. Once I removed that program, I didn't have issues with GRUB2 being corrupted by windows again.

I just wanted to thank you for sharing this. I've been searching for a few days for a solution to this very problem (dual booting Kubuntu and Windows 7 on a Studio XPS 16), and this seems to have cleared it up.

---

### Post by reiki on 2010-05-13
Glad to help. :)
So far that fix seems to have been the answer for me as the problem has not come back.

---

### Post by LK_gandalf_ on 2010-05-13
Same problem on a dell studio 1558, at every boot windows 7 deleted something in the grub.
I formatted completely the pc and installed 7 + linux in dual boot, problem solved.

---

### Post by g_hol on 2010-06-09
> **reiki said:**
> I had this issue on my Dell Zino HD as well. Make sure you still have your liveCD available as you're probably going to screw up GRUB2 one more time.

Boot into Windows. Using the Add/Remove programs, uninstall Dell DataSafe local.

That was the culprit on my Dell box. Once I removed that program, I didn't have issues with GRUB2 being corrupted by windows again.


It works ...  Thank you very much for sharing this !

---

