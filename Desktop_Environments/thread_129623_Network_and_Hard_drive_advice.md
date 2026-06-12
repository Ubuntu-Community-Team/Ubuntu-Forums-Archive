---
title: "Network and Hard drive advice"
date: 2006-02-14
forum: Desktop Environments
---

### Post by metro.tramp on 2006-02-14
Hi,
I've just installed ubuntu on my home pc; it's my first time using linux of any kind, so am a bit fresh on my feet. I just need a bit of advice on networking and file systems..

As i said, ubuntu is installed on my home (tower) pc. I installed it on my first hard drive that is partitioned and also has XP installed. I have a second HDD on this comp, which is ntfs formatted and has all of my music and videos on it - i hadn't bothered to back these up as i didnt realise linux ain't too keen on ntfs before i installed it. I have got the secnd HDD mounted and it is reading without problem. I figure i'll probably back up all the files to DVD, then format to ext3 or another linux system (is ext3 best?). I found captive ntfs ([http://www.jankratochvil.net/project/captive/]("http://www.jankratochvil.net/project/captive/")) and may try it out, but i guess it's best to use a  system linux is more comfortable with in the long run - does anybody have any experience with using captive? how reliable is it?

As i got a shiny new apple ibook for xmas :) i'm gonna use my tower pc as a 'workhorse', mainly for downloading and uploading large files, and a bit of storage. It's connected to my router via ethernet cable. I need to access this (linux) computer with my ibook which is running os x (tiger) in order to share files and all that usual networking stuff - it'd also be handy to be able to access my ibook from the linux tower. My ibook connects to the internet/network using its airport extreme. How do i set up my computers to talk to each other? is there any issue with the filesystems, or should they be able to browse one-another pretty simply?

My second question (or is it third? ...fourth?) involves an external hardrive.. i just got hold of a lacie usb2.0 external hard drive that i intend to share between both systems, so it (preferably) needs a file system that both ubuntu and os x can read and write to comfortably. But there's another little cinch... I intend to use my external drive to share my photos and music files with my friends, all of whom use xp...

Is there any kind of super-wonderful, magical dream filesystem that Ubuntu, OS X AND XP can all use effectively in a lovely melting-pot style share-fest, or do just need to partition that drive up?

I think that's about it (for now...)

thanks in advance

---

### Post by Robgould on 2006-02-14
All can share data, read and write fine to fat32.  If you were accessing your XP over the netework you could leave it as NTFS and read ane write to it with smbfs (samba).

---

### Post by metro.tramp on 2006-02-14
Isn't fat32 a bit unreliable though? I also read that it has limits to volume sizes (my external HDD is 250Gb).

---

