---
title: "What is the purpose of “lost &amp; found” item in k-menu?"
date: 2005-04-18
forum: Desktop Environments
---

### Post by SGC on 2005-04-18
I don't understand the real purpose of “Lost & found” item in k-menu or /lost+found folder. Can any one please explains their uses?

---

### Post by heimo on 2005-04-18
Hi!

I don't use KDE, so I can't be sure of this, but it sounds like it's a standard lost+found directory you can find on any unix partition. I don't know what the use is on the menu - you'd very rarely see anything there and in that situation something would have gone wrong.

But here are couple links to better desccriptions of lost+found directory:


 [http://www.cs.wayne.edu/labPages/Unix_T/file_organ.html]("http://www.cs.wayne.edu/labPages/Unix_T/file_organ.html")
 > 
               

 

[list]
[*]**The lost+found Directory**
 
 
 
             [left]When files are recovered after any sort of problem or failure,they are placed in the lost + found directory, if the kernel cannot ascertain the proper location in the system. 
 
[/left]
[/list] 


[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html#lostfound]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html#lostfound")
>  As was explained earlier during the overview of the FSSTND, Linux should always go through a proper shutdown. Sometimes your system might crash or a power failure might take the machine down. Either way, at the next boot, a lengthy filesystem check (the speed of this check is dependent on the type of filesystem that you actually use. ie. ext3 is faster than ext2 because it is a journalled filesystem) using fsck will be done. Fsck will go through the system and try to recover any corrupt files that it finds. The result of this recovery operation will be placed in this directory. The files recovered are not likely to be complete or make much sense but there always is a chance that something worthwhile is recovered. Each partition has its own lost+found directory. 

---

### Post by SGC on 2005-04-18
Thanks  heimo  :-)

---

### Post by jdong on 2005-04-19
The "Lost and Found" menu in KDE and the "/lost+found" directory are **two separate concepts**.


The KDE menu is for placing applications that have a category which doesn't fit into any existing menus.


/lost+found is a bit similar to the "Lost Clusters" concept, for orphaned (corrupted) files on a filesystem.

---

### Post by SGC on 2005-04-19
Thanks jdong, I thought the two were refering to the same thing.

---

