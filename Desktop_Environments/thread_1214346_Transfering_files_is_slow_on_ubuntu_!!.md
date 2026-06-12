---
title: "Transfering files is slow on ubuntu !! ??"
date: 2009-07-15
forum: Desktop Environments
---

### Post by Wanas on 2009-07-15
When I try to transfer files (20 gb) from ntfs disk to other ntfs disk it goes very slow nautilus says (6 MB/sec), while I try to transfer on vista it says (20 MB/sec).

Dont ubuntu supports ntfs filesystem well ?
Is there a way to make the transfers faster ?

---

### Post by LepeKaname on 2009-07-15
I have had the same problem before. According to what I read, it may be related to the IDE driver. In my case Burning a DVD was taking a lot of time. I haven't manage it to fix it. I upgraded to Jaunty and the performance seems to be better now. But not sure if it will work for you.

It is just that drive? 
do you have other drives? 
are your drives IDEs?

---

### Post by Wanas on 2009-07-15
thanks for replaying 
I have three drivers tried on them all back and forth
one is sata and others is normal ides (I dont know much about hard drives)

---

### Post by iponeverything on 2009-07-15
I have noticed that nautilus is way slower than using scp from the command line. It has been that in 8.10 and now in 9.04

---

### Post by Wanas on 2009-07-15
> **iponeverything said:**
> I have noticed that nautilus is way slower than using scp from the command line. It has been that in 8.10 and now in 9.04

Is there any other GUI alternatives, because I used to copy alot of things in which using command line will eat my time

---

### Post by LepeKaname on 2009-07-17
Yes, I use gftp, which also support over ssh and other protocols. 
Other alternative is to use konqueror (but you will need kde libraries). 
If its just for copying from one drive to another, then you can use thunar (available in Xfce, but you can use in gnome as well).

---

### Post by zevans on 2009-07-17
I've noticed the NTFS filesystems are a bit tardy. I might be imagining it, but it seems FASTER if I use the FUSE stuff than if I use the kernel code - I think the fuse code might be later and better.

Either way the NTFS-3g version in Jaunty is way behind current version so that could be it too. 

I've now reached the point that all the photo-crunching and music-listening I do is in Linux so I have solved this problem by moving everything to ext4 and it's now distinctly faster even than in Windows.

---

### Post by ajji on 2009-07-17
I used to have the same problem. I upgraded to Jaunty and everything is fine now.

---

