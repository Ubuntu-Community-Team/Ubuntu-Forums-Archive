---
title: "help me install ubuntu."
date: 2008-12-28
forum: General Help
---

### Post by idcoder on 2008-12-28
hi. i have ubuntu 6.06 LTS and would like to install it along with windows XP.
Ok here is  my PC config.
256 MB ram, celeron 
1.2 GHz processor. Now i have two separate hard disk of 40 GB each. i have created 6 partitions total out of the 2 hard disk. now i had 5 partitions with Fat32 and the remaining 1 i have made it to NTFS(10GB). i want to install ubuntu in that partition.

i used the live CD and tried to install from there.
i used the manual method to partition the hard disk.
But when it came to selecting the root '/' and swap , what i did was make 8 GB root from that NTFS 10GB partition and remaining 2GB for swap. Now the remaining 2GB is not recognised either as fat or ntfs.

ok now i selected the root and swap space later but for other original partitions it said  "media/IDE/ " something(sorry i dnt remember now) I think if i had continued, it would format my entire hard drive..so i shut down the process.

anyone can please help me..
or provide any links which may help me..thanks a lot and sorry if my question is silly. i want to learn ubuntu.

---

### Post by namdung on 2008-12-28
Is there any particular reason ur using ancient 6.06. Pls use Hardy Heron 8.04.1 LTS. For ur configuration, Xubuntu is suggested but Ubuntu may also work. Try LiveCD first.

What u did look fine. Just delete the 10 GB partition, partition 9 GB with ext3 with mount to root "/". The rest 1 GB as swap (1 GB is more than enough for ur PC). Select this while partition while installation. 

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Sef on 2008-12-28
>  the remaining 1 i have made it to NTFS(10GB). i want to install ubuntu in that partition.

Ubuntu will not work correctly on NTFS, instead use the default file system, ext3.

If you do install Ubuntu 6.06, you should update it to Ubuntu 8.04, if you are using it as a desktop.  This is because support will run out by June 2009.   If you are using it as a server, then support will continue to 2011.

---

### Post by idcoder on 2008-12-28
> **namdung said:**
> Is there any particular reason ur using ancient 6.06. Pls use Hardy Heron 8.04.1 LTS. For ur configuration, Xubuntu is suggested but Ubuntu may also work. Try LiveCD first.

What u did look fine. Just delete the 10 GB partition, partition 9 GB with ext3 with mount to root "/". The rest 1 GB as swap (1 GB is more than enough for ur PC). Select this while partition while installation. 

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

hey thanks for reply. as you may see my PC config is very low. Also when i was using ubuntu 6.06 live CD it was very very slow.  I want to learn ubuntu, so i will first start with this pack.

Now, as you said i will do accordingly. I have now have understood this steps..guide me if i am wrong.

I will go to manual section while installation.
There will be a 8 GB NTFS and a 2 GB unformated space. I will delete them. It is right click delete right.? 
Once i delete them Create a partition of 9GB and 1GB as you said.

I just want that this 10Gb gets to use the ubuntu and nothing should happen to the remaining partitions.
Once i select "/" and "linux-swap" , then next step shows media/IDE/ for all partitions. Should i press continue.? will it affect my windows partitions.?

I am very scared. I really applogise for asking these questions but i dnt want anything to go wrong.

---

### Post by idcoder on 2008-12-28
> **Sef said:**
> Ubuntu will not work correctly on NTFS, instead use the default file system, ext3.

If you do install Ubuntu 6.06, you should update it to Ubuntu 8.04, if you are using it as a desktop.  This is because support will run out by June 2009.   If you are using it as a server, then support will continue to 2011.

hey sef. thanks for a reply.
i have all partitions as FAT32. what i did was empty a partition which was 10 GB and format it to NTFS. so that while installing i come to know which partition exactly i have to install ubuntu.

i use manually edit partition table, selected my 10 GB partition where i want to install ubuntu. Then what should i do.? i am stuck there..

thanks a lot for reading my query patiently and replying.

---

### Post by Bucky Ball on 2008-12-28
Your windoze ntfs drives will be clearly visible during the manual partitioning section of your installation. Just don't go near them and delete any other partitions you don't want, then create partitions you do what. A tip: make a solid plan as to what you are going to do at this section of the installation. You won't have to remember any mouse combinations; it is an easy to follow GUI. :)

IMHO, the 8.04 version of Xubuntu would be a whole lot better and more suitable for your setup. You might get Ubuntu to run but it will probably be sluggish and you would probably have to install with the alternate cd (although you never know with this issue - there seem to be no hard and fast rules, there is a norm but there are exceptions).

Good luck, stay relaxed and clear about your partitioning plan and stay away from the NTFS partitions and you will be fine.

As mentioned, forget anything but the EXT3 partitions you are about to create during the install for Ubuntu/Xubuntu. NTFS is a microsoft idea that is not natively read or written to with Ubuntu. FAT partitions on the other hand can be seen and written to, so don't touch any of those you want to keep either. There will be a lot of clues as to what partitions you are looking at (write down the sizes now before you start just as another way of checking what you are dealing with and for your own peace of mind).

---

