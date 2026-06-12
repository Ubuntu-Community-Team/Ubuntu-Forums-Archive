---
title: "Extending the /home partition from /host"
date: 2013-05-18
forum: Desktop Environments
---

### Post by mhrsolanki2020 on 2013-05-18
Hello,
I am currently compiline Android OS from source , for which i need almost 50gb .. 
I installed Ubuntu 10.04 LTS from windows 7 Wubi.exe 
It had not given me any option for making a hard drive any larger than 30gb
So in windows i created a New drive with label "Ubuntu" with 50gb
And then opened Wubi.exe installed ubuntu 10.04 lts with 30gb partition..
So now booted in ubuntu , i have /home of 30gb and /host 50 gb(the 30gb of /home is included in this 50gb)

I want to extend the /home to and i dun need that /host space.. 

Can someone help me with it ?

---

### Post by bcbc on 2013-05-19
If you have 50GB on a whole partition, why don't you just install directly to it? The point of Wubi is not having to partition. Yes, you could resize the Wubi disk to fill up the full partition, but it will be slower than if you just installed direct.

---

### Post by mhrsolanki2020 on 2013-05-19
> **bcbc said:**
> If you have 50GB on a whole partition, why don't you just install directly to it? The point of Wubi is not having to partition. Yes, you could resize the Wubi disk to fill up the full partition, but it will be slower than if you just installed direct.
So you are saying i should make a bootable usb? and then uninstall the current ubuntu and re install from usb by booting into it?

---

### Post by bcbc on 2013-05-19
Yes, exactly. I would just delete the whole partition before doing that, because the Ubuntu installer (ubiquity) will create a new partition in that space (or if it can, an extended partition with two logical partitions - one for swap and the rest for your Ubuntu partition).

So if you want to take control of that, choose "Something else" when you get to that part:
[IMG]http://assets.ubuntu.com/sites/ubuntu/latest/u/img/download/desktop-1204-install-4.jpg[/IMG]

---

### Post by mhrsolanki2020 on 2013-05-19
I have my android source that i pulled from git .. Its about 16gb ... Can i back up the current disk and restore it in new installed ubuntu ??because copyong the whole 16gig dir to my windows partition n then again pasting after reinstalling is quite a lenghty process .. Ny alternative ??

---

### Post by bcbc on 2013-05-19
Are you asking if you can back up the Wubi root.disk? If it's on the partition you're going to use then it will be removed, but backing that up will be a 30GB file. So from Wubi you can backup the Android source to the Windows partition or an external drive. There's not much choice if you're installing over the partition (because it will replace the partition and everything on it).

---

