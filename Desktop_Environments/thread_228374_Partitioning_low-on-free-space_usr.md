---
title: "Partitioning low-on-free-space /usr"
date: 2006-08-03
forum: Desktop Environments
---

### Post by RavenOfOdin on 2006-08-03
Got a quick partitioning question.

Linux takes up all the space on a 6.4 GB HD with 3 partitions. /, /opt, and /usr. The /opt partition which is ReiserFS has 1.8 GB. The /usr partition has 1.3 GB. The / partition has the rest (obviously!)

Due to some bad partitioning choices that I made (I was going to try for a dual boot system and transplant /home directories from one install to another) I now have a partition of 1.8 GB that is doing nothing and a /usr partition that needs space since its full to the brim.

Is there any way I can get the 1.8 GB into the current 1.3 via a partition editor that will not make me reinstall the entire system?

---

### Post by RAOF on 2006-08-03
You should be able to get a LiveCD to allow you to delete, move, and expand partitions.  I like [System Rescue CD]("http://www.sysresccd.org/Main_Page"), but even the Dapper Live/Install CD should work.

---

### Post by RavenOfOdin on 2006-08-03
Okay. I'll try the Ubuntu Live CD. 

It worked when I corrupted my boot loader. :p

---

### Post by andb on 2006-08-03
Be careful if you have ntfs partitions in the middle. Ive seen nothing but problems with linux based tools resizing ntfs partitions. I personaly use partition magic. I tried it using hiren's boot cd, which I found online at [http://homepage.ntlworld.com/hiren.thanki/bootcd.html](http://homepage.ntlworld.com/hiren.thanki/bootcd.html)

takes a while, but itll do the job. If there are no ntfs partitions that will me moved /resized, the gparted live cd is great. 

By the way, the only things I have in opt are azureus and swiftwox and its around 50 meg. So I have that in the root partition. Do you want to move move what you have in opt into root and then merge all that space into home (I think best option) or just shrink opt and then move freespace? You can easily do the first booting from a live cd. If you need instructions, just write and I'll write a step-by step...

---

### Post by eXisor on 2006-08-03
There is an excellent guide on how to move your /home/ partition to another partition which will work for the /usr/ move too (just substitute /usr/ for /home/. I moved my /home/ this way recently without any problems... even the symlinks moved properly.

[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

