---
title: "home directory on fat 32?"
date: 2008-12-31
forum: General Help
---

### Post by matemargo on 2008-12-31
Is possible to assing the home directory to a fat32 device?

---

### Post by taurus on 2008-12-31
Using fat32/vfat filesystem for /home is a bad idea because fat32/vfat doesn't play well with ownership and permissions.

---

### Post by matemargo on 2008-12-31
Ok, but is it possible?

My other option would be to convert it to ext3, but it's not possible from what I read.

---

### Post by bumanie on 2008-12-31
FAT32 is rather limiting with its file size maximums, why do you want the partition this way. Linux reads and writes fine to ntfs - if you need a filesystem that both linux and windows can share, ntfs is the best option. Of course you may have another reason. In short, it is possible.

---

### Post by wmdiem on 2008-12-31
I just spent a lot of time trying to do this with NTFS, and I was eventual told I couldn't (because it wouldn't preserve permissions and ownership). 
I ended up having to just leave /home on the main partition, but I was able to move the subfolders to the NTFS partition and put links between them.

EDIT: what i meant to say was that /home/username has to be in a fs that supports permissions and ownership (ext2, 3 rieser), because each user has to have exclusive permission on his own user folder, but anything within that folder can be linked in from another fs, FAT, NTFS, etc.

---

### Post by theozzlives on 2008-12-31
Put your /home on its own partition, formatted ext3, then in Windows install ext2fsd to give your /home a drive letter in Windows.

---

### Post by matemargo on 2008-12-31
My idea is to completely remove Windows. I just want to preserve all that is on the FAT32 partition.

Maybe I would do what wmdiem suggest and keeps links between the folders.

Thanks.

---

### Post by LowSky on 2008-12-31
> **matemargo said:**
> My idea is to completely remove Windows. I just want to preserve all that is on the FAT32 partition.

Maybe I would do what wmdiem suggest and keeps links between the folders.

Thanks.
I think you are confusing a few things, or maybe I am?
If your completely removing Windows, you don't need FAT32. If you have a partition that is current serving Windows as your Documents and settings or as you normal "go to" folder, you cannot use it as your /home folder. Best suggestion is backing up your data to another partion or keeping the FAT32 partiton as a backup partition.

---

### Post by wmdiem on 2008-12-31
> **LowSky said:**
> I think you are confusing a few things, or maybe I am?
If your completely removing Windows, you don't need FAT32. If you have a partition that is current serving Windows as your Documents and settings or as you normal "go to" folder, you cannot use it as your /home folder. Best suggestion is backing up your data to another partion or keeping the FAT32 partiton as a backup partition.

I suspect the idea is to remove windows but retain all the files currently on the windows partition without having to back them all up. It takes a lOOOOOOOOOOng time to backup 40gig if you're doing it 700 mb at a time.

---

### Post by matemargo on 2008-12-31
> **wmdiem said:**
> I suspect the idea is to remove windows but retain all the files currently on the windows partition without having to back them all up. It takes a lOOOOOOOOOOng time to backup 40gig if you're doing it 700 mb at a time.

That's exaclty the reason.

---

### Post by skern03 on 2008-12-31
This solution is probably on the forbidden side in the land of free s/w... but I had a similar situation with an external drive formated to FAT32. GParted would have nothing to do with resizing the partition despite following the advice of some posts on the forums here. There was no choice but to use a third party tool. Partition Magic lets you convert FAT32 to NTFS. I'm not sure about converting NTFS to ext3. It did not take that long, either, just a few minutes as I recall. If GParted could have handled this, I would have used it.

---

