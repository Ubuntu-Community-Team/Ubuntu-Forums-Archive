---
title: "UBUNTU and USB HDD"
date: 2009-01-19
forum: General Help
---

### Post by elf_cleric on 2009-01-19
Hi Guys,
I am using ubuntu for some personal use.
I have 20GB external HDD and when try to copy files from UBUNTU to my HDD It copies only if the files are less than 5GB???
If files are more than 5GB it gives error and won't copy?

Am I missing something or is it ubuntu which is stupid?

Regards

---

### Post by gjoellee on 2009-01-19
Is it ONE FILE that is over 5GB??! However if there are several files, try to not move all at the same time.

I can't answer your last question because I don't use Ubuntu, but I can tall that computers are stupid, they can only do what they are told to do.

---

### Post by elf_cleric on 2009-01-19
> **gjoellee said:**
> Is it ONE FILE that is over 5GB??! However if there are several files, try to not move all at the same time.

I can't answer your last question because I don't use Ubuntu, but I can tall that computers are stupid, they can only do what they are told to do.

Yeah,
It is sadly one file which is 6GB and it won't go to drive which is 20GB?
Drive is too small says UBUNTU!!

---

### Post by elf_cleric on 2009-01-19
I am just wondering about,
How much size of my drive UBUNTU can see?

---

### Post by heindsight on 2009-01-19
What filesystem do you have on the external drive? And how much free space is on the drive?

Post the output of running
```
df -hT
```
(while the external drive is mounted). That may help to shed some light on what's going on.

---

### Post by elf_cleric on 2009-01-19
> **heindsight said:**
> What filesystem do you have on the external drive? And how much free space is on the drive?

Post the output of running
```
df -hT
```
(while the external drive is mounted). That may help to shed some light on what's going on.

It says file system MSDOS and 18.6GB

I am using the same drive for my windows vista as well.
I have no idea about how to get more space from my drive....

---

### Post by heindsight on 2009-01-19
> **elf_cleric said:**
> It says file system MSDOS 

That's your problem. That MSDOS means that the file system on your drive is FAT32 which has a 4GB file size limit.

---

### Post by elf_cleric on 2009-01-19
> **heindsight said:**
> That's your problem. That MSDOS means that the file system on your drive is FAT32 which has a 4GB file size limit.

File size limit on FAT32 is not 4GB!!
Are there any chances of fixing this??

If not UBUNTU is from stoneage :(
Perhaps I better uninstall this...

---

### Post by Quotey on 2009-01-19
The filesize limit on FAT32 is 4GB- it isn't Ubuntu's fault. To transfer files over 4GB you'll have to format it as NTFS.

In a terminal, type

```
sudo apt-get install gparted ntfsprogs
```

You'll have to use gparted to format the external harddrive with the NTFS filesystem selected. It'll erase all the data on the drive so back it up first. I can't help you with gparted, but you'll probably be able to do it if you're careful and get advice from other posters

---

### Post by elf_cleric on 2009-01-19
> **Quotey said:**
> The filesize limit on FAT32 is 4GB- it isn't Ubuntu's fault. To transfer files over 4GB you'll have to format it as NTFS.

In a terminal, type

```
sudo apt-get install gparted ntfsprogs
```

You'll have to use gparted to format the external harddrive with the NTFS filesystem selected. It'll erase all the data on the drive so back it up first. I can't help you with gparted, but you'll probably be able to do it if you're careful and get advice from other posters

Thanks mate!
How about formatting in vista as ntfs?

---

### Post by Yashiro on 2009-01-19
Should be OK but I'd recommend doing it from Linux.

> **"http://en.wikipedia.org/wiki/NTFS"]NTFS has five released versions:

    * v1.0 with NT 3.1,[citation needed] released mid-1993
    * v1.1 with NT 3.5,[citation needed] released fall 1994
    * v1.2 written by NT 3.51 (mid-1995) and NT 4 (mid-1996) (occasionally referred to as "NTFS 4.0", because OS version is 4.0)
    * v3.0 from Windows 2000 ("NTFS V5.0")
    * v3.1 from Windows XP (autumn 2001 said:**
>  V1.2 supports compressed files, named streams, ACL-based security, etc.[1] V3.0 added disk quotas, encryption, sparse files, reparse points, update sequence number (USN) journaling, the $Extend folder and its files, and reorganized security descriptors so that multiple files which use the same security setting can share the same descriptor.[1] V3.1 expanded the Master File Table (MFT) entries with redundant MFT record number (useful for recovering damaged MFT files).

Windows Vista introduced Transactional NTFS, NTFS symbolic links, partition shrinking and self-healing functionality[12] though these features owe more to additional functionality of the operating system than the file system itself.

---

