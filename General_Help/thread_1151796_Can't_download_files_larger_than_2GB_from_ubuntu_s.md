---
title: "Can't download files larger than 2GB from ubuntu server"
date: 2009-05-07
forum: General Help
---

### Post by milindras on 2009-05-07
Hi,
We have a Ubuntu web server & Im trying to download bigger than 2 GB files & its not allowing. Less than 2GB any file I can be download or wget successfully. 
Can any one tell me where to check for this problem?
Thanks
Milindra

---

### Post by BslBryan on 2009-05-07
Hello, milindras. :-)

Well, a FAT32 partition cannot handle a file larger than 2GB, so if you're downloading on a FAT partition, try downloading on ext3 instead.

That being said, if it's *not* FAT32, it is quite possible that perhaps you have your FTP server set to cut off at 2GB?  You might check it's config file.

If that's still not the problem, just try to use this:
```
curl http://whatever.example.ie.iso -C - -o whatever.iso 
```

I hope I've been of some help. :-)

Good luck, and best to you.

---

### Post by colau on 2009-05-07
> **BslBryan said:**
> Hello, milindras. :-)

Well, a FAT32 partition cannot handle a file larger than 2GB, so if you're downloading on a FAT partition, try downloading on ext3 instead.

That being said, if it's *not* FAT32, it is quite possible that perhaps you have your FTP server set to cut off at 2GB?  You might check it's config file.

If that's still not the problem, just try to use this:
```
curl http://whatever.example.ie.iso -C - -o whatever.iso 
```

I hope I've been of some help. :-)

Good luck, and best to you.
Thanks.
Got another option "curl".

---

### Post by milindras on 2009-05-07
> **BslBryan said:**
> Hello, milindras. :-)

Well, a FAT32 partition cannot handle a file larger than 2GB, so if you're downloading on a FAT partition, try downloading on ext3 instead.

That being said, if it's *not* FAT32, it is quite possible that perhaps you have your FTP server set to cut off at 2GB?  You might check it's config file.

If that's still not the problem, just try to use this:
```
curl http://whatever.example.ie.iso -C - -o whatever.iso 
```

I hope I've been of some help. :-)

Good luck, and best to you.
Hi,
Appreciate for promt reply.
Could you tell me how to check my file system? Whether Fat32 or ?
 
And also what doest meant by
curl [http://whatever.example.ie.iso](http://whatever.example.ie.iso) -C - -o whatever.iso  
 
Thanks
Milindra

---

### Post by 3rdalbum on 2009-05-07
Fat32 can handle files up to 4GB, not 2GB.

I'm thinking that Ext2 has a filesize limit of 2GB?

Curl is a program for downloading; it's an alternative to "wget". You've just been given a command to use with Curl; the URL given ([http://whatever.example.ie.iso](http://whatever.example.ie.iso)) is the URL of the file that you want to download, and the "whatever.iso" is the filename that you want the file to have when it hits your hard disk.

---

### Post by colau on 2009-05-07
> **3rdalbum said:**
> Fat32 can handle files up to 4GB, not 2GB.

I'm thinking that Ext2 has a filesize limit of 2GB?

Curl is a program for downloading; it's an alternative to "wget". You've just been given a command to use with Curl; the URL given ([http://whatever.example.ie.iso](http://whatever.example.ie.iso)) is the URL of the file that you want to download, and the "whatever.iso" is the filename that you want the file to have when it hits your hard disk.
Does curl have resume support?

---

### Post by gamblor01 on 2009-05-07
> 
Could you tell me how to check my file system? Whether Fat32 or ?

You can use the following command to list all of the partitions and their corresponding formats:

```

sudo fdisk -l

```

If this is a Linux machine I seriously doubt the drive is formatted FAT32.  Most likely it's ext3 (the ID column with be "83" and the System column will say "Linux").

What is the error message you are getting when wget fails?

---

### Post by milindras on 2009-05-07
> **3rdalbum said:**
> Fat32 can handle files up to 4GB, not 2GB.

I'm thinking that Ext2 has a filesize limit of 2GB?

Curl is a program for downloading; it's an alternative to "wget". You've just been given a command to use with Curl; the URL given ([http://whatever.example.ie.iso](http://whatever.example.ie.iso)) is the URL of the file that you want to download, and the "whatever.iso" is the filename that you want the file to have when it hits your hard disk.
Thanks.
Im using a download manager to download files to a XP machine. So the curl command cannot use isnt it?

---

### Post by milindras on 2009-05-07
> **gamblor01 said:**
> You can use the following command to list all of the partitions and their corresponding formats:

```

sudo fdisk -l

```

If this is a Linux machine I seriously doubt the drive is formatted FAT32.  Most likely it's ext3 (the ID column with be "83" and the System column will say "Linux").

What is the error message you are getting when wget fails?
Disk /dev/sda: 158.9 GB, 158999773184 bytes
255 heads, 63 sectors/track, 19330 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         262     2104514+  82  Linux swap / Solaris
/dev/sda2   *         263       19330   153163710   83  Linux
 
that is the out put of that. Can you tell me how to identify the file type?
 
Thanks

---

### Post by milindras on 2009-05-07
> **milindras said:**
> Disk /dev/sda: 158.9 GB, 158999773184 bytes
255 heads, 63 sectors/track, 19330 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         262     2104514+  82  Linux swap / Solaris
/dev/sda2   *         263       19330   153163710   83  Linux
 
that is the out put of that. Can you tell me how to identify the file type?
 
Thanks
Ah Its looks like FAT32

---

### Post by gamblor01 on 2009-05-07
No this system is clearly using ext3 (the ID is 83 and System is Linux) and not FAT32 according to the fdisk output.

I am a little confused however.  First you say that are using Ubuntu, then you say you are using a download manager on Windows XP, and then you post the output of disk from a Linux machine.

So which is it?  Are you trying to download the file on a system running Ubuntu or Windows XP?

---

### Post by milindras on 2009-05-07
> **gamblor01 said:**
> No this system is clearly using ext3 (the ID is 83 and System is Linux) and not FAT32 according to the fdisk output.
 
I am a little confused however. First you say that are using Ubuntu, then you say you are using a download manager on Windows XP, and then you post the output of disk from a Linux machine.
 
So which is it? Are you trying to download the file on a system running Ubuntu or Windows XP?
Oh, Sorry If I confused you. Its like this. 
 
We have a Linux web server (Ubuntu) which Im taking some weekly backups.
Im using a download manager on a Xp machine to downloads those backed up files from the ubuntu server to Xp machine.
I can download any files less than 2GB from my server to my XP machine. But not anything larger than 2 GB.
 
Thanks

---

### Post by cholericfun on 2009-05-07
so check you XP if its FAT32, (and you'll never be able to make files larger than 2GB - never heard of the 4GB another poster mentioned earlyer)
i think you can see that in the defragger

also you might want to check if all works fine for files >2GB on an NTFS / ext3 machine. just case theres something else going on as well

---

### Post by Slim Odds on 2009-05-07
> **cholericfun said:**
> so check you XP if its FAT32, (and you'll never be able to make files larger than 2GB - never heard of the 4GB another poster mentioned earlyer)


File size limits are:
FAT32 -- 4GB
FAT16 -- 2GB

[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)

Also, for one of the previous posters, ext2 is 16GB (or more depending on block size).

---

### Post by cholericfun on 2009-05-07
> **Slim Odds said:**
> File size limits are:
FAT32 -- 4GB
FAT16 -- 2GB


ah cool, was never aware of that

---

### Post by milindras on 2009-05-27
> **cholericfun said:**
> so check you XP if its FAT32, (and you'll never be able to make files larger than 2GB - never heard of the 4GB another poster mentioned earlyer)
i think you can see that in the defragger
 
also you might want to check if all works fine for files >2GB on an NTFS / ext3 machine. just case theres something else going on as well
 
I think there is something else. 
Does apache, FTP server etc .. can put restrictions on the download limits?
For ftp server im using vsftpd, and I checked the vsftpd.conf file for any limitation, but couldnt find any thing. 
 
thanks

---

