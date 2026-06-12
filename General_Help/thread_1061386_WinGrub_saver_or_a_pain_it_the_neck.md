---
title: "WinGrub saver or a pain it the neck"
date: 2009-02-05
forum: General Help
---

### Post by sokis on 2009-02-05
I have the following critical issue.

I ve been using Ubuntu 6 months, and i habe in my pc and laptop. Yesterday i diceded to get rid of my Vista partition.
By that moment my _ACER 5920g_ had these partotions

1.vista recovery
2.Vista ntfs
3. an ntfs 
4.Linux ext3
5.linux pagefile
6.acer recovery

I wanted a **clean Win xp** installation.

But i **messed things a bit...** i used a gparted live cd to create an NTFS (from partitions 1 and 2). I went to win xp installation and i deleted the NTFS that i made with gparted but then i couldnt format the partition because there were too many partitions and i exited the installation.

And then i went to **gparted** to see that it was **identified as unallocated**. Grub was away i dont know how. And i went back to win xp to format partitions 1 and the umallocated one to one partition (thank to God everything was identified).Made the installation.

But know **i dont have GRUB** and i cant install it throught UBUNTU live because the _HDD its still identified as unallocated by gparted _(but i can mount the drives).

Now i installed wingrub but i cant make the configurations properly. I see the wingrub screen when the laptop starts but it doesnt search for other OS.


Any ideas with the wingrub or any other way throught linux?

---

### Post by ladydonna on 2009-06-05
Hi  I am just wondering where I can find WINGRUB. I am having a boot up problem with windows and Ubuntu myself. Seems I messed my boot up when I installed Ubuntu on my external hard drive and cannot boot my laptop without the external attached. Any help would be greatly appreciated.

---

### Post by jbruced on 2009-06-05
I'd check the supergrub website.

Lots and lots of info, and free supergrub CD download.

---

