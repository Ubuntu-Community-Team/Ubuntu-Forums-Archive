---
title: "Completely screwed..."
date: 2009-06-06
forum: General Help
---

### Post by USAF_EOD on 2009-06-06
Hey everyone-
Sorry if this issue has been addressed before but I DID try searching in case anyone wants to yell at me.  Here's my situation:  Recently I purchased a Samsung NC10 netbook preloaded w/ Windows XP.  After conversing with a friend who sang the praises of Ubuntu, I decided to give it a shot.  My netbook on initial startup gave me an option to set up partitions.  Knowing that I wanted to try Ubuntu, I broke it up as follows:

6 GB Windows Recovery (Not negotiable)
95 GB Windows XP
49 GB Second partition

I downloaded and installed Ubuntu Netbook Remix.  All was going GREAT and I was very excited.  There were things about UNR that I did not like so I decided to try to install Ubuntu Desktop OVER UNR.  That's apparently when all hell broke lose.  Through I'm sure what can only be called "user error", the desktop install apparently did not go over UNR but created another partition/drive.  When I tried to alleviate this through Windows partition manager, I managed to create some error causing the OS loader to not come up.  I then reinstalled Desktop again and it is working but I now have only around 3 GB or so.  Ultimately, I just want about 100 GB for windows and 50 GB for Ubuntu.  If anyone can PLEASE help me, it would be greatly appreciated.  I am enclosing a screen shot that may be of assistance.  I truly want to learn Linux but at this point, I feel I may have jumped in the deep end before I could swim.  Or even float for that matter.  Again, all help is greatly appreciated.  Thanks to all for your time.

Respectfully,
Joshua

---

### Post by AlarmingSword on 2009-06-06
Try deleting all partitions apart from the XP and windows recovery partitions (all non NTFS partitions), and then reinstalling Ubuntu by creating a partition from the leftover free space.

---

### Post by USAF_EOD on 2009-06-06
Should I just use the disk management resource in Windows XP or is there something else you recommend?

---

### Post by merlinus on 2009-06-06
Try the gparted live disk.

---

