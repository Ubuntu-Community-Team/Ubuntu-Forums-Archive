---
title: "Partitioning"
date: 2006-07-23
forum: Desktop Environments
---

### Post by royskie on 2006-07-23
hello,

I've just started using Ubuntu (and it's great!!!)...started with breezy and working my way to get dapper as of this moment.  Anyway, I have a 80GB HDD and partitioned it as follows:

10 GB - /
25 GB - /home
5  GB - swap
40 GB - supposedly as FAT32.

My question is how do I use the 40 GB partition and format it as FAT32? (was thinking of using it as data storage)

The thing is....I did not format it during the installtion part of Ubuntu, now that the beast is running, I can't get the Disk Manager to detect/format the 40 GB free space I left out during the installation.

Any help is appreciated.  Thanks!

Roy

P.S. Can you tell that I'm stuck with "Windows" terminology? hehe

---

### Post by deanjm1963 on 2006-07-23
Are you using windows? If you're NOT there is no need for your 40GB fat32.

5GB of swap is a overkill, depending on the amount of ram your system has, you could get away with anything from 256MB to 1GB.

If you're only using Ubuntu, and you're not installing mega-amounts of programs, you could consider

root = 8GB
home = 71GB
swap = 1GB

---

### Post by royskie on 2006-07-23
Thanks for the reply....that was actually my previous disk setup. As I explored the applications available for Ubuntu.... I found vmware....:-D 

Now I'm thinking of running my applications in Windows via that route LinuxOS+VMWare+"virtual" Windows+Windows Programs=I can think of a lot of things hehe. 

Anyway, my goal is to produce some files in vWindows then have a space to read/write these files via a network of different platforms.

Does that make sense?

Thanks again!
Roy

btw, I have 1GB RAM.

---

### Post by deanjm1963 on 2006-07-23
if you're going to use Vmware, you won't need the fat32 partition as it allows windows virtual machines to use linux partitions (don't quote me on that). 

What windows applications to you need to use? is there a linux equivalent?

1GB of ram is great, I have the same, I could use 512MB, but I prefer to have 1GB swap, the choice is yours.

---

### Post by royskie on 2006-07-23
Okay, thanks much for the advice.  I think Ill play with it a bit more. ](*,)

---

### Post by bruenig on 2006-07-23
do 
```
sudo apt-get install gparted
```
After that is done. Go to System>Administration>Gnome Partition Editor and there is a very easy GUI way to accomplish that task. It is the same GUI that is in the partition manager of the installer.

---

