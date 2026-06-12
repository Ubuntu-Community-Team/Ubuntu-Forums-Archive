---
title: "Uncompressing the UT2k4 demo"
date: 2005-12-30
forum: Gaming &amp; Leisure
---

### Post by Zarkoth on 2005-12-30
Hey there,

I migrated to Ubuntu about six months ago, love it, showering it with praise, etc.

Only thing is, of course, the lack of games.  Now up until around today I have been dealing with not gaming, but I needed a fix, and downloaded the UT2k4 demo for Linux.  Only problem is, while uncompressing it, I get "Unexpected End of File" 
...and that's it.

So, how do fix that?

Thanks in advance!

---

### Post by MrCheese on 2005-12-30
sounds like your downloaded archive is corrupt. Try re-downloading. If this comes up with the same error, check how big the file is. There is a filesize limit of 2Gb on ext2/3 filesystems, if the file is larger than this it may have been truncated to 2Gb.

---

### Post by kaamos on 2005-12-30
[QUOTE=MrCheese]sounds like your downloaded archive is corrupt. Try re-downloading. If this comes up with the same error, check how big the file is. There is **a filesize limit of 2Gb on ext2/3 filesystems**, if the file is larger than this it may have been truncated to 2Gb.[/QUOTE]

Maybe ext2 but not in ext3..
[quote=http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html]
Ext3 can support files up to 1TB. With a 2.4 kernel the filesystem size is limited by the maximal block device size, which is 2TB. In 2.6 the maximum (32-bit CPU) limit is of block devices is 16TB, but ext3 supports only up to 4TB.[/quote]
Ubuntu by default uses an ext3 partition.

---

### Post by Zarkoth on 2005-12-30
I d/led again, and same thing...

Checked the file size, and although the point is moot as mentioned earlier, it is still only 1.8 GB expanded...

Very perplexing, this problem

---

### Post by kaamos on 2005-12-30
What is the file type (zip, gz, bz2)?

---

### Post by Zarkoth on 2005-12-30
The file type is gz

---

### Post by kaamos on 2005-12-30
Open a terminal a when in the same folder with the file, type "tar xfvz nameoffile.tar.gz"

Does it give only the "unexpected end of file" error?

---

### Post by Zarkoth on 2005-12-30
I did this previously on Archive Manager, and that gave me just the unexpected EOF earlier...

Doing it here, I got this - 

```

tar: This does not look like a tar archive
tar: Skipping to next header
tar: Archive contains obsolescent base-64 headers

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors

```

I shall add the the filename is UT2004-LNX-3334.run.gz

So I think the absence of .tar.gz is something to be noted?

---

### Post by kaamos on 2005-12-30
Well, I can't think of anything but a corrupt download. Sorry. :(

---

