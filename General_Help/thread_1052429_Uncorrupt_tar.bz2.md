---
title: "Uncorrupt tar.bz2?"
date: 2009-01-27
forum: General Help
---

### Post by Paperfairy on 2009-01-27
Two days ago, I used the tar command from the terminal to compress and store my /home folder. I moved the tar.bz2 file into another partition, and reinstalled 8.10. I went to open the tar and move /home back, but the archive manager tells me the tar is corrupt. Is there any way to undo this?


> 
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now



I already ran bzip2recover, and it spat out 966 smaller versions named rec00xxxhome.tar.bz2, which I also, cannot open. They say:

> 
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Error exit delayed from previous errors


---

### Post by taurus on 2009-01-27
What filesystem is the other partition that you stored the backup of your /home?  Have you tried to uncompress and untar it from a terminal?

---

### Post by Paperfairy on 2009-01-27
Oh sweet dear, I may know what happened...

It's an ntfs filesystem. How does one do that from the terminal? This is first time using the tar command.

---

### Post by taurus on 2009-01-27
It's probably best to copy it back to an ext3 filesystem/partition.  Then, you can try something like, assuming you are in the same directory where that file is

```
tar xvjf filename.tar.bz2
```

---

### Post by Paperfairy on 2009-01-27
In the 60 seconds I was waiting for you, I got nervous and Googled around... without moving it back to ext3, I used the terminal, and it is successfully untaring. Now, after copy and pasting /home, do I need to restart or log out, or something?

---

### Post by taurus on 2009-01-27
You mean you have moved the backup to /home.  You need to restart your computer for the changes to take affect.

---

### Post by Paperfairy on 2009-01-27
One more question, after the untar, the terminal gave this to me:

home/justin/home.tar.bz2

bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Unexpected EOF in archive


However, everything appears to be in place, is there something else I should...?

---

