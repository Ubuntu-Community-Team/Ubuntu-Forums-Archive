---
title: "GRUB Hard Disk Error:"
date: 2008-04-16
forum: Desktop Environments
---

### Post by ryazkhan on 2008-04-16
I am sure lot of you guys heard about this error before but I am sorry I did not find comprehensive solution for it after searching for quite a while. Here is my problem
I have a IBM Intellistation M Pro Dual Xeon 2.4Ghz Tower Server with scasi hard drive in it. I want to intalll ubuntu on it every thing goes well untill I reboot the machine after installation I got GRUB Hard Drive Error: and not else but if I put the CD in again and ask machine to boot from hard drive it works just fine this thing eathing my head hairs which are already not enough:) I tried lot of things like putting IDE HDD in it and istalling on that, making seprate partition for /boot, flash bios, upgrade hard drive I found tool on IBM website but all that in vain I got still same issue. My best thinking is that IBM bios does not support Linux because I installed suse too but got same error. It is IBM want you pay for every single thing you want to do.
Please Please Please Please Please help me with this and save my hairs:) I am very :confused: :confused::confused::confused: I never seen this before I installed ubuntu on many machines but this one is ....

---

### Post by ryazkhan on 2008-04-16
Because Windows works perfect & fast without any issue.
Please Please Please Please Please help me with this and save my hairs:) I am very :confused::confused::confused::confused: I never seen this before I installed ubuntu on many machines but this one is ....

---

### Post by amacca on 2008-06-12
Hi there, I have encountered the same problem with an IBM Intellistation M Pro we have here and also tried the same things to resolve it. It simply wont go past the grub hard disk error so I hope someone out there has some suggestions.

Andrew

---

### Post by meierfra. on 2008-06-13
This  thread
[URL="http://ubuntuforums.org/showthread.php?p=3829572"]
http://ubuntuforums.org/showthread.php?p=3829572[/URL]

seems to contain a solution to your problem. Grub needs to be installed without the stage1.5 files. 

The thread shows you how to do that (see post 35) But you can also download Supergrub (see my signature)

and follow these  instruction (the easy Solution)

[http://www.supergrubdisk.org/wiki/WindowsErasesGrub]("http://www.supergrubdisk.org/wiki/WindowsErasesGrub")

---

