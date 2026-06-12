---
title: "Samba share, ntfs and vmware"
date: 2006-07-08
forum: Desktop Environments
---

### Post by bohboh on 2006-07-08
I have several ntfs drives which i have shared in samba and can see ok within my vmware player running xp. I want to be able to copy ubuntu files to the ntfs drive which is why i set up vmware as i cant afford to lose the files and risk ubuntus ability to write to ntfs.

SO, i would like to copy files from the samba shared unbuntu folder to the samba shared ntfs folder using vmwareplayer running xp, i can see both folders ok in xp, i just cant copy as it says that idont have write permissions to the ntfs volumes.

I dont even know where to start, is this a samba issue?

---

### Post by scxtt on 2006-07-08
how are your NTFS drives mounted in ubuntu?  what's your /etc/fstab look like?

---

### Post by someusernoob on 2006-07-08
Cant you copy the files from Ubuntu to Windows using Windows?

--

Hmm, after rereading, nvm, since vmware is using his own disk of course.

--

And after rereading it again i know what you tried to do.

No its not possible. Since Windows is sending the file to Ubuntu, Ubuntu has to place the file into the specific folder. and Ubuntu (Linux) doesnt support NTFS writing.

For example (to make it clear):
Say when im (non virtual) networking between Ubuntu and Windows. Windows has a shared folder (NTFS). I send a file from my Ubuntu box to the Windows box. Now it is Windows who gets the file, and has to place it in the folder. So all the writing is done by Windows. 

What you tried to do is sending a file from Windows, to Ubuntu, who has the NTFS folder. Since Ubuntu is receiving the file, its Ubuntu who has to put the file into the folder, but as i said, Ubuntu (Linux) cant write to NTFS.

---

### Post by bohboh on 2006-07-08
I see, so when i copy in xp from shared linux to shared ntfs i am infact passing the "copying" onto ubuntu, and since ubuntu doesnt have ntfs write installed, it is saying permission denied.

Seems obvious now, and i now realise i wasted a day getting vmware up and running. :D oh well..

So putting vmware and ntfs-fuse to one side, is there a "safe" way of writing to ntfs? by means of third party software, not necessarily free. I would even convert from ntfs to ext but i dont have the space (require at least 200gb) to backup and i dont want to risk losing everything. I thought i would need xp so set it up as dual boot, but in fact i need it a lot less than i thought.

---

### Post by scxtt on 2006-07-08
isn't it possible your NTFS drives are mounted read-only?, which is why i asked the questions i asked above ...

---

### Post by bohboh on 2006-07-08
fstab line:

```
/dev/sda1	/windows/main	ntfs	nls=utf8,umask=0222	0	0
```

---

### Post by scxtt on 2006-07-08
i'm no umask pro, but isn't umask=0222 gonna give you **ONLY** r-xr-xr-x permissions for all files/dirs on sda1?

[http://wiki.linux-ntfs.org/doku.php?id=ntfs-en#how_do_i_change_the_permissions_of_a_mounted_ntfs_volume](http://wiki.linux-ntfs.org/doku.php?id=ntfs-en#how_do_i_change_the_permissions_of_a_mounted_ntfs_volume)

---

### Post by someusernoob on 2006-07-08
> **bohboh said:**
> I see, so when i copy in xp from shared linux to shared ntfs i am infact passing the "copying" onto ubuntu, and since ubuntu doesnt have ntfs write installed, it is saying permission denied.
Exactly

> 
Seems obvious now, and i now realise i wasted a day getting vmware up and running. :D oh well..


At least you learned how to set it up and use it.

> 
So putting vmware and ntfs-fuse to one side, is there a "safe" way of writing to ntfs? by means of third party software, not necessarily free. I would even convert from ntfs to ext but i dont have the space (require at least 200gb) to backup and i dont want to risk losing everything. I thought i would need xp so set it up as dual boot, but in fact i need it a lot less than i thought.

No, there is not a really safe way yet, since MS is not releasing the sourcecode of NTFS. So thats why developing takes so long and the stuff they got to write to NTFS is still not safe to use.

And as far as i know its not possible to convert from NTFS to EXT3 without formatting. And again as far as i know it is possible to convert NTFS to FAT32, but there is no assurance it will always work without any problems, so there might be the possibilty to lose data.

---

### Post by petejacobsen on 2006-07-12
I've been reading with interest, since my new Ubuntu machine was once the backup machine for my networked Windows machines.  I've got a 250gb USB disk formated NTFS, and I can't setup backup again since the writing will actually be done by Ubuntu.

Question: If I reformat my USB disk to ext3 (or however you spell it!), can the Windows machines backup to it (through Ubuntu) and also retrieve files from it (through Ubuntu)?  I'm really hoping I don't have to turn it into gobs of FAT32 partitions to get by the 32gb limitation.

---

### Post by bohboh on 2006-07-12
> **petejacobsen said:**
> I've been reading with interest, since my new Ubuntu machine was once the backup machine for my networked Windows machines.  I've got a 250gb USB disk formated NTFS, and I can't setup backup again since the writing will actually be done by Ubuntu.

Question: If I reformat my USB disk to ext3 (or however you spell it!), can the Windows machines backup to it (through Ubuntu) and also retrieve files from it (through Ubuntu)?  I'm really hoping I don't have to turn it into gobs of FAT32 partitions to get by the 32gb limitation.

You can write/read to a ext drive from windows using several open source drivers:

[http://kennethhunt.com/archives/001314.html](http://kennethhunt.com/archives/001314.html)

Dont know what it will be like with transferring large files, i have used it for small files and was ok.

---

