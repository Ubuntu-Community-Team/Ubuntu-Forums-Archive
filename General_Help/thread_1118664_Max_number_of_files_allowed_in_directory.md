---
title: "Max number of files allowed in directory"
date: 2009-04-07
forum: General Help
---

### Post by H4F on 2009-04-07
I am running a script witch gets htmls from web,store them ,and is parsing them.

So I am downloading htmls. currently I have 175486 files in directory. 

As I understand it depends on inode size , partition size.

my partition is 21.9 GB. each file is ~19k. don't know the size of inode !! 

how do I calculate max number of files allowed in directory ?

---

### Post by mb_webguy on 2009-04-07
According to Wikipedia:> The limit of sublevel-directories is about 32768. If the number of files in a directory exceeds 10000 to 15000 files, the user will normally be warned that operations can last for a long time unless directory indexing is enabled. The theoretical limit on the number of files in a directory is 1.3 × 10^20, although this is not relevant for practical situations.This is assuming you're talking about ext2.

---

### Post by matmat07 on 2009-04-07
You could try the new ext4, I think it has a greater limit. Be sure to read about it so you don't get an error somewhere in the process

---

### Post by DeMus on 2009-04-07
> **matmat07 said:**
> You could try the new ext4, I think it has a greater limit. Be sure to read about it so you don't get an error somewhere in the process

Is Ext 4 stable already. I read somewhere it is not. So be careful.

---

### Post by H4F on 2009-04-07
I have EXT3.  so does any one know exact number. and what would happen if i exceed that number

---

### Post by H4F on 2009-04-07
> **mb_webguy said:**
> According to Wikipedia:This is assuming you're talking about ext2.

You said I will be warned . but I am not. script is running with root privliges so the files are root owned.

---

### Post by mb_webguy on 2009-04-07
> **H4F said:**
> I have EXT3.  so does any one know exact number. and what would happen if i exceed that number
According to what I've read (and as I said in my previous post) the only hard limit on the number of files in a directory is 1.3 × 10^20 (or 130,000,000,000,000,000,000), though if you exceed something in the range of 10000 to 15000, you'll apparently get a warning about poor performance.  The limit for subdirectories is much smaller, at about 32768.  I'm not entirely clear, however, whether this is the total number of subdirectories on the filesystem or the maximum depth of the filesystem.

---

### Post by H4F on 2009-04-07
Thanks 130,000,000,000,000,000,000 would be enough for me :)

---

