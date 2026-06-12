---
title: "Trouble installing dual system"
date: 2006-01-20
forum: General Help
---

### Post by nelsonmandela on 2006-01-20
Hellooooo.
I am an intermediate unix user with more Solaris experience than Linux.  I had an XP SuSE 64-bit dual boot system working fine for over a year.  I don't really like SuSE and I wanted to switch to Ubuntu.  I popped in the install CD and everything went well until I started to install the base system.  Now I'm getting an error: "The debootstrap program exited wiht an error (return value 1)."  Does anyone know what I'm doing wrong?  
I confused myself when repartitioning.  I have an NTFS partition for XP, a swap partition, a 5-gig FAT32 partition (originally for Linux OS, I think ?), and a 45-gig FAT32 for data/files.  SuSE automatically formatted the 45-gig partition as Rieser and Rieser is a silly filesystem to use when trying to boot XP and Linux since windows refuses to acknowledge Rieser fs.  So when I was partitioning I switched the Rieser fs to FAT32.  I also messed with the 5-gig FAT32.  Now when I restart I boot into GRUB loader, something I've never seen or used before.  I am unable to get into Windows or SuSE. 
Help, please.  Thank you berry, berry much.

---

### Post by encompass on 2006-01-20
Did you say that you are currently trying to install with rieser... I don't think reiser is that bad... NOR do I think it uses riesr fs.  I think ubuntu uses ext3 by default.  Which is a very stable and fast FS, while fat32 is not.  I would create a 5 gig fat for swaping information... and the linux os on it's own partition that windows can't touch.
Then see if you have problems from there.  If it still gives the error I haven't the foggest idea what could be wrong outside of the cd being bad.  That can happen.  (Happened to be a zillion times)
Hope this is a start...

---

### Post by nelsonmandela on 2006-01-21
It turned out to be the fs.  I followed your advice and setup Ubuntu on its own ext3 fs and it installed without problems.  I guess it wont install on fat fs or something...I don't know but it worked so I'm going with ext3. 

I don't know much about Rieser fs, just that it gave me some hell a few months ago when I was trying to transfer files from my reiser partition to windows.


Thanks for your help!

---

### Post by encompass on 2006-01-23
Glad I could help... perhaps to help the community a little more... your system may have a quirk like that...
I would make a howto on how you installed ubuntu on you computer.  Trying to be very specific.
But.. thanks for the success report.  They are great to hear.

---

