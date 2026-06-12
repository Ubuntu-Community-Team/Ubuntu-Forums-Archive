---
title: "Extracting large files"
date: 2009-03-26
forum: General Help
---

### Post by kzam on 2009-03-26
So i downloaded a file that is 4gb in size. However, I am not able to extract this with ubuntu. I know that there isn't anything wrong with the files because it happens to all my files over 2gb

Could someone please instruct me how to extract this file.
Thank You

---

### Post by DeMus on 2009-03-26
> **kzam said:**
> So i downloaded a file that is 4gb in size. However, I am not able to extract this with ubuntu. I know that there isn't anything wrong with the files because it happens to all my files over 2gb

Could someone please instruct me how to extract this file.
Thank You

I'm not completely sure but I think it is impossible to do that on a 32-bit machine. With a 64-bit OS it is no problem at all. Is there a way for you to change to a 64-bit system, or have the file extracted on a 64-bit system?

---

### Post by coffeecat on 2009-03-26
**DeMus**, I think you're confusing file sizes with RAM sizes. 32-bit sytems are limited to 4GB of RAM, but are perfectly capable of handling files (and extracting them) larger than 4GB.

**kzam**, what is the nature of the file that you can't extract? A tar.gz? tar.bz2? iso? img? And how are you trying to extract it?

Also, what filesystem are you saving it to? Is this what you mean - that you can't save a downloaded file greater than 4GB? A FAT32 filesystem can't cope with files greater than 4GB. You have to use a Linux filesystem or NTFS for very large files.

---

### Post by aeiah on 2009-03-26
try extracting from the command line. it tends to not bog the system down the same way. gui archiving programs try to scan the whole file for it's contents and this might be bogging things down.

---

### Post by Slim Odds on 2009-03-26
> **coffeecat said:**
> Also, what filesystem are you saving it to? Is this what you mean - that you can't save a downloaded file greater than 4GB? A FAT32 filesystem can't cope with files greater than 4GB. You have to use a Linux filesystem or NTFS for very large files.

Definitely sounds like a FAT32 thing.

ext2/3 has a 64TiB max file size (or 16GB with very small block size).

---

### Post by DeMus on 2009-03-26
> **coffeecat said:**
> **DeMus**, I think you're confusing file sizes with RAM sizes. 32-bit sytems are limited to 4GB of RAM, but are perfectly capable of handling files (and extracting them) larger than 4GB.

**kzam**, what is the nature of the file that you can't extract? A tar.gz? tar.bz2? iso? img? And how are you trying to extract it?

Also, what filesystem are you saving it to? Is this what you mean - that you can't save a downloaded file greater than 4GB? A FAT32 filesystem can't cope with files greater than 4GB. You have to use a Linux filesystem or NTFS for very large files.

No, I was not confusing file size with ram size. I know very well the difference between the two. 
I remembered the old days of FAT32 where 2GB was the limit. If the OP says 2GB is the limit for him then something like this could be the cause.

OP, what filesystems do you use? Ext2/3, NTFS, or do you use FAT32?

---

### Post by kzam on 2009-03-26
> **coffeecat said:**
> **DeMus**, I think you're confusing file sizes with RAM sizes. 32-bit sytems are limited to 4GB of RAM, but are perfectly capable of handling files (and extracting them) larger than 4GB.

**kzam**, what is the nature of the file that you can't extract? A tar.gz? tar.bz2? iso? img? And how are you trying to extract it?

Also, what filesystem are you saving it to? Is this what you mean - that you can't save a downloaded file greater than 4GB? A FAT32 filesystem can't cope with files greater than 4GB. You have to use a Linux filesystem or NTFS for very large files.

The thing is I have already downloaded the file (4.2gb), but the content is compressed into many rar's. When I go to extract those rars i get an error. Im using a Fat32 formatted harddrive. 

Im using archive manager (right click -- extract with archive manager)

---

### Post by coffeecat on 2009-03-26
Do you know what size the file should have been? FAT32 has a maximum filesize of 4GB. In my experience when you try to save/copy a large file to a FAT32 filesystem, it will save part of the file up to the 4GB mark. So you think you've got a complete file, but you haven't. I wonder if that's why unrar is failing.

If the file was considerably larger than 4GB (or 4.2 - perhaps the discrepancy is a GB/GiB thing), can you download it to an ext3 filesystem? Do you have room on your root partition?

---

### Post by damis648 on 2009-03-26
> **kzam said:**
> Im using a Fat32 formatted harddrive.

There's your problem. Files over 4GB cannot reside in a FAT32 filesystem, that is the limit of the filesystem. The archive is probably just pushing that limit. Now, if the archive consisted of a lot of small files versus a few large files, that is a different story. But I would bet it is FAT32 that is causing you the problems, as somewhere in the archive there may be a file well over the file size limit of FAT32.

> I'm not completely sure but I think it is impossible to do that on a 32-bit machine. With a 64-bit OS it is no problem at all. Is there a way for you to change to a 64-bit system, or have the file extracted on a 64-bit system?

That is RAM size.

> No, I was not confusing file size with ram size. I know very well the difference between the two.
I remembered the old days of FAT32 where 2GB was the limit. If the OP says 2GB is the limit for him then something like this could be the cause.

OP, what filesystems do you use? Ext2/3, NTFS, or do you use FAT32

You may very well know the difference, but you just contradicted yourself. First you talk about 32 and 64-bit OS's, now filesystem. >.>

---

### Post by kzam on 2009-03-26
> **coffeecat said:**
> Do you know what size the file should have been? FAT32 has a maximum filesize of 4GB. In my experience when you try to save/copy a large file to a FAT32 filesystem, it will save part of the file up to the 4GB mark. So you think you've got a complete file, but you haven't. I wonder if that's why unrar is failing.

If the file was considerably larger than 4GB (or 4.2 - perhaps the discrepancy is a GB/GiB thing), can you download it to an ext3 filesystem? Do you have room on your root partition?

Im pretty sure the whole file has downloaded. I ran the extaction again and this is the error message i get 

>  Write error in the file /media/disk/dfd-007-synaptic.mkv [R]etry, [A]bort
Write error in the file /media/disk/dfd-007-synaptic.mkv
Inappropriate ioctl for device 

---

### Post by Sapelko on 2009-03-26
Hi kzam,

 same thing happened to me before. The workaround I found was to issue the following command in a terminal window:

unrar fileName.rar

where fileName.rar is the file name of the file you downloaded. If it's a multipart rar file, the 'unrar' tool will take care automatically, you just provide the name of the initial compressed file (the one that ends with .rar).

If you get an error message complaining about 'unrar' not being installed, just do (from a terminal window)

sudo apt-get install unrar

and that should do the trick. 

Feel free to mail me if it still doesn't work for you.

Cheers.

---

### Post by kzam on 2009-03-26
> **Sapelko said:**
> Hi kzam,

 same thing happened to me before. The workaround I found was to issue the following command in a terminal window:

unrar fileName.rar

where fileName.rar is the file name of the file you downloaded. If it's a multipart rar file, the 'unrar' tool will take care automatically, you just provide the name of the initial compressed file (the one that ends with .rar).

If you get an error message complaining about 'unrar' not being installed, just do (from a terminal window)

sudo apt-get install unrar

and that should do the trick. 

Feel free to mail me if it still doesn't work for you.

Cheers.

i tried that and it gave me a list of commands 

i.e 
e-extract
p-print
etc

am i doing something wrong

thanks

---

### Post by Slim Odds on 2009-03-26
Nothing will work on files that large on FAT32.

Use a different file system.

---

### Post by Sapelko on 2009-03-26
sorry, my bad... the right command to type would have been

unrar e fileName.rar


the 'e' part tells unrar to Extract the file contents. sorry for the mistake

if it's a multi-part file, then you shouldn't be concerned about file system issues, it should still work

---

