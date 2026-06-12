---
title: "dos partition long filenames lost after power outage"
date: 2009-06-18
forum: General Help
---

### Post by PC-XT on 2009-06-18
After the power went out, while using Windows 98 on a FAT32 partition, Program Files and everything in it, as well as My Documents (though *nothing* in it) and one folder in Recycled (Recycle Bin) lost their long filenames. I was hoping someone knew of a utility to retrieve the names, as I have heard of some such thing, but hoped I would never need it. :-o I did rename Program Files, My Documents, Program Files\Common Files, and what I needed to get on the Internet, as I don't yet have Internet access with Linux, but stuck with stupid Windows-only dial-up :(

---

### Post by PC-XT on 2009-06-20
I found the win98 utility is windows\command\sulfnbk.exe, and found instructions at [http://support.microsoft.com/kb/190418](http://support.microsoft.com/kb/190418) to get it to fix the start menu, and have heard about an L switch, but don't know what it does. This seems to be just a quick hack to fix a start menu problem after an incomplete uninstall, using names from a list, without actually recovering any names from directory entries. The icon at least makes it look like a quick hack...

I just realized that one of the folders (shared over the network) got an old folder's name. I thought it had been deleted a long time ago. Strange.

---

### Post by PC-XT on 2009-06-25
I found someone who kindly helped me in [Programming Talk]("http://ubuntuforums.org/showthread.php?t=1191244"), so I'm marking this thread solved.

---

### Post by jake16424 on 2009-06-25
DataRecovery v.2.4.2 (Undelete Files from Recycle Bin) 

also scan's formatted partitions, might be of some assistance.

*could maybe turn pc off before it gets fried before a storm comes?*

usually leave mine on unless there are brown outs *they can allow the 
reader heads of your hard drive to momentarily lose power and hit your disk, = not good at all *

---

### Post by PC-XT on 2009-06-25
Thanks for the input. This wasn't a storm, the power just went off for a few seconds. It's happened a couple times before, but almost always without issue other than losing info from RAM. I'll look into DataRecovery.

---

### Post by PC-XT on 2009-07-18
I had renamed most by hand, but am now looking into getting Data Recovery again, as it happened again. I had scandisk log this time, and it lists all the lfn directory entries as though they were regular entries, and says it deleted them. It was strange, because I had tested scandisk, and it seemed to be working. I think I was accidentally overriding the ini file during the tests. This info led me to a nearly identical problem at [http://www.computing.net/answers/windows-95/how-do-i-restore-long-file-names/170107.html](http://www.computing.net/answers/windows-95/how-do-i-restore-long-file-names/170107.html)
So I set lfncheck back on, which should stop it from happening.
Still no free solution except by hand-renaming. This time scandisk had run completely because I wasn't there to stop it. I do have an incomplete backup, thankfully, but will need to get Windows working first. :(
I was wondering if anyone had used something mentioned in that discussion like [Disk Investigator]("http://www.snapfiles.com/reviews/Disk_Investigator/diskinvestigator.html") or [Uneraser]("http://www.uneraser.com/longfilenames.htm") or something else to recommend it. I found several programs called Data Recovery. Ultimate Data Recovery 5.0 by MISPBO Technologies is one example.

---

### Post by PC-XT on 2009-07-22
I found Disk Investigator to be easiest to use for this problem.
Also, reinstalling programs may cause duplicate files, which I'm using CloneSpy to clean.

---

