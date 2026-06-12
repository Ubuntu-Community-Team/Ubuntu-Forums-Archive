---
title: "GRUB error 2... I want to kill my laptop"
date: 2008-12-23
forum: General Help
---

### Post by evilminininja on 2008-12-23
I had installed ubuntu perfectly for about a month now. I dualbooted with vista and ubuntu and had a fat32 partition for my music. Now, I was trying to install gfx and things got messy. After hours of fiddling and messing with my menu.lst and other grub files... I ended up installing and deleting and reinstalling grub a thousand times over. Then, when i restart my computer... I got a grub shell. I had to make a new ubuntu cd (lost mine) and I saw my menu.lst was erased. Good thing I made a backup. I renamed the back up menu.lst and deleted the old, messed up one.** But now I get error 2 when I boot.**

So if push comes to shove.. I might reinstall ubuntu over vista...delete my other partitions except for that fat32.. then put vista back on through a torrent or maybe ask HP for a cd.. I on;y need vista for word and i have the ms office files on my fat32. I don't want to delete my ubuntu partition only because I was torrenting rosetta stone and it was 95% complete and it took me like 5 days... but I can always start over fresh...

But in case I do not want to go through all of that... can I get GRUB back? I'm going crazy

---

### Post by ponto18 on 2008-12-23
If i understand you,
you're saying that you can't login on ubuntu? cause of grub?

there is an alternate cd that you can use to recover grub and your ubuntu installation like windows.. it's in the official page.. search for alternate cd...

Hope it helps...

---

### Post by evilminininja on 2008-12-23
> **ponto18 said:**
> If i understand you,
you're saying that you can't login on ubuntu? cause of grub?

there is an alternate cd that you can use to recover grub and your ubuntu installation like windows.. it's in the official page.. search for alternate cd...

Hope it helps...

I can't boot at all. Upon starting my laptop I get 
loading sage 1
complete
loading (something I can not remeber)
error 2

I will search for alternate cd, thank you. but from the research I have done on this problem... a clean installation is the only way. Oh well, not much of a problem there

---

### Post by Pobega on 2008-12-23
No, you can use the *grub-install* executable from the LiveCD or Alternate CD to restore GRUB. Read **GRUB-INSTALL( 8 )** (man grub-install) for more information on the grub-install command

---

### Post by redilyn on 2008-12-23
You could always ditch vista altogether. 

Open office should replace word without much problems unless there is a particular feature of word that you must have which is not part of open office.

Also, if you do reinstall Ubuntu, consider making a separate /home partition, that way if you have to reinstall ubuntu again you will not lose your settings or documents.

Psst, shouldn't mention that your pirating rossetta stone either.....

---

### Post by caljohnsmith on 2008-12-23
If you want to use gfxboot, you should try the latest package from:

[http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)

The reason why is because Intrepid now formats its partitions to use a 256 byte inode file system size, whereas previous Ubuntu verions used 128 bytes. The older Grub versions choke on the newer ext3 partitions that use 256 byte inode sizes, and Grub returns an error 2. How about trying the above package and let me know how it goes.

---

### Post by albinootje on 2008-12-23
> **evilminininja said:**
> 
But in case I do not want to go through all of that... can I get GRUB back?

[http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors)
> 
2 : Bad file or directory type
    This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. 


---

