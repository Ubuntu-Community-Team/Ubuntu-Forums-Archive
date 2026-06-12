---
title: "Wubi or Live CD? What's the difference after install?"
date: 2009-01-14
forum: General Help
---

### Post by Rubicon421 on 2009-01-14
I've used both a few times and I know the major differences. Once I'm through the install process though, are there any differences besides the partition vs mount folder and the ability to uninstall a Wubi install from Windows?  I have several HDs and no problem adding a partition, so if I know how to install both and don't mind either one, what are the pros and cons after the install? It seems like the major differences are just in the install process itself.

---

### Post by azmo35 on 2009-01-15
Hi,on my case [a newbe] i foud at beginig very confusing so i went to the wubi road,i liked the ideia of unistall easier from windows.But when i transfer wubi to a real partition i encounter a few problems like boot error because lvpm move wubi to the new partition and unistall himself the same doesn't happen with wubi,but nothing you can't solve,said that i think running and install from live cd maybe is better.

---

### Post by Yashiro on 2009-01-15
- Wubi is limited to the size of the virtual disk you create.
- If Windows exits badly it makes Wubi unbootable.
- File read/write is a little slower as is OS resposiveness.
- You cannot hibernate.

---

### Post by ithanium on 2009-01-17
chose Wubi only if you don't know or are afraid of making new partitions
the installation from live CD will give you more space, speed and hibernate!

---

### Post by fiklein on 2010-02-14
WUBI is less stable than a native Linux installation. WUBI is a file in Windows that loops back in booting and runs Ubuntu. Agostino Russo created it and his work is appreciated. If you are not sure you want to use Ubuntu, the Live CD option that makes no changes to your computer is a good start. WUBI is a safe option, as it can easily be deleted via Add/Remove programs in Windows Control Panel. Unfortunately, WUBI booting has developed some recent bugs that are in the process of being corrected. 
  A live CD does not create a permanent operating system unless you choose that option. If you choose to load a native Linux partition, run Defragment in Windows to move your Windows files away from the upper addresses of your hard disk and make room for the Linux partition. It is actually pretty easy to load a native Linux partition with the tools on the Live CD. I started with WUBI and have gone to a native installation, dual boot with Windows on 3 computers. The instructions on the disc are pretty easy to follow. If you want more information than you need (and this seems to make it more confusing than necessary), you can read:
  [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) 
It is useful to have a bare minimum of 10 GB to run Ubuntu, but I have done it with about 7 GB. Smaller installations have smaller swap files, so this may slow performance. Good luck.

---

