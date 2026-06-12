---
title: "Is there a way to ignore errors when extracting a tar.bz2 file?"
date: 2008-10-21
forum: Desktop Environments
---

### Post by cashmoney on 2008-10-21
I backed up my pc prior to re-installing the OS using 

```
tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /
```

When I go to unpack it on my system it using 

 ```
tar xvpfj backup.tar.bz2 -C /
```

It errors out apparently the external Drive I mounted it to went bad.  Is there a way to force it to continue to extract regardless of errors?  Obviosly I won't extract it to root at this point but there is 15 GB of music I downloaded off Itunes and about a gig or two of family pictures I don't want to lose. Here is the error.  Thanks in advance.

> bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now


When I run -tvv option like suggested, the only packet that shows a CRC error is 1901 the rest of the archive is good.  So is there a way I can tell it to extract ignoring errors?

Or extract to the 1900th block skip the 1901 and restart at 1902 and continue to the end?

---

### Post by Pelham123 on 2008-10-21
Take a look here:

[http://www.bestsolution.at/support/console/repair_tar_archives.html.en](http://www.bestsolution.at/support/console/repair_tar_archives.html.en)

I also thought that you could double click the archive and 'browse' the files. This would also allow you to extract out the music and photos before trying any tar repair?

---

### Post by cashmoney on 2008-10-22
> **Pelham123 said:**
> Take a look here:

[http://www.bestsolution.at/support/console/repair_tar_archives.html.en](http://www.bestsolution.at/support/console/repair_tar_archives.html.en)

I also thought that you could double click the archive and 'browse' the files. This would also allow you to extract out the music and photos before trying any tar repair?

Thanks I found that link yesterday and followed it to the T and was able to save 99.9% of my home folder. 

It was time consuming but well worth it.  Actually I'm pulling the last of my files as I type this.

---

