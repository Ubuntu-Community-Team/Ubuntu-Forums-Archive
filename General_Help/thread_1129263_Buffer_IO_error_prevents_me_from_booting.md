---
title: "Buffer I/O error prevents me from booting"
date: 2009-04-18
forum: General Help
---

### Post by Lathspell on 2009-04-18
I'm afraid Windows messed up big time while I was trying to write a DVD and now I have an I/O error on partition D(Windows in on C and Ubuntu on let's say E). Windowd cracked immediateley so I tried to write a windows DVD with ubuntu to try and fix it. However, when I mounted partition D in Ubuntu, it also cracked, so now I am left with 2 cracked OSs and an Ubuntu command line, from which I desperately tried to unmount partition D. Unfortunately, when I tried "umount -l/-f /dev/sda4" it gave an error saying "umount2: Invalid argument".
Will someone please help me clear this mess and fix at least Ubuntu?

Forever in your debt, 
Lathspell

PS: "umount -l/-f /dev/sda4" means I tried both lazy and force, but not in the same time

---

### Post by cariboo on 2009-04-18
Judging by the terminology you are using, I'm going to assume that you installed Ubuntu using wubi, as Linux doesn't use drive letters. I would suugest that you use your Vista boot disk to repair Vista first. When you get to the the install menu, select repair and let Vista repair itself. If you don't have a Vista install DVD go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download the version for your computer. Once you have Vista repaired, you can then work on Ubuntu repaired.

Start Ubuntu in recovery mode, then at the menu select xfix. Once xfix is finished select resume, which should take you to your desktop. You will have to reactivate the resricted graphics driver by going to System-->Administration-->Hardware drivers.

Jim

---

### Post by Lathspell on 2009-04-18
The problem is that Ubuntu won't even start in recovery mode right now...And that the computer I'm using doesn't have a DVD-writer...so I can't write a Vista DVD and I don't have one with me since I am away from home...thank you for the advice but do you happen to know a way I could unmount sda4 from the command line?

---

