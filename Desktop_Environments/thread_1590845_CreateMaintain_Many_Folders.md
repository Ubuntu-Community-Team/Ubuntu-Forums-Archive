---
title: "Create/Maintain Many Folders?"
date: 2010-10-08
forum: Desktop Environments
---

### Post by csharpplus on 2010-10-08
I am building an application that would need to store data in many different folders (say, 5,000,000 folders).
Obviously that is a big number of folders.

My project is flexible in terms of how to outline the folders (meaning, some folders can be sub-folders of others etc). 

Given the Ubuntu file system, is there a rule-of-thumb on how many sub-folders should be in a folder? how many files should be in a folder? (I am asking strictly from a performance point of view).

thank you.

---

### Post by kidders on 2010-10-09
Hi there,

To even *begin* to answer your questions, you'd need to post ...

[LIST]
[*]What filesystem you're using, and how it's configured. Performance stats for certain operations vary wildly from one filesystem to another, not to mention the fact that what you're describing would not even be possible in certain environments (eg a default Ext3 filesystem less than 38GiB in size).
[*]What you intend  to do with the files. The complexity of some filesystem operations can expand logarithmically, while others may be more linear. It's impossible to say that one configuration is better/worse than another without knowing what at ... and if you're going to be doing something in particular with that many files billions of times in a row, small differences can become very significant!
[*]A rough idea of the sizes & compositions of the files would also be useful.
[*]The file naming convention you're using. It would be helpful to know, for example, whether it would be possible to infer a file's location from its name. If not, you may find you have to settle for a sub-optimal directory structure.
[/LIST]

---

### Post by csharpplus on 2010-10-09
kidders,

Thanks for your help.

I am using Ext4 (version 1.0) file system, with 58GB of total size (of which 50GB are available). I will be using the newest Ubuntu 10.10 (though at present I use 10.04).

The files (of typical size ~100KB) will be created (written) once per day. meaning, each one of the 5,000,000 folders will have say a 'YYYYMMDD' folder (representing the date), in which there will be 2-3 files.
Following the files' creation, they will only be read. so, writing will be done once, but reading will be done frequently. I can write the files as either 'text' or 'binary' format (is there a preference?)

naming convention is not a problem, as I can choose a name will provide direct access to the file (meaning, I will know -- based on the file's name -- where it is stored; will have no need to search for its location etc...).

---

### Post by kidders on 2010-10-10
Hi again,

Sounds as though you'd need to store about 30 million files, just to get started (ie 5,000,000 directories, each containing a single subdirectory with 3 files in it). Assuming you used all the default configuration options when creating your ext4 filesystem, that wouldn't be possible. In fact, assuming the filesystem was completely empty to begin with, I'd expect you to run out of inodes somewhere in the region of the half way mark. You'd have to post your "df -i" to be sure though.

The other observation I'd make is that ext4 is probably a poor choice. Most of the changes made between ext2/3 and ext4 are targeted at optimising handling of large files, so it's not especially well-suited to storing millions of 100k ones.

> **csharpplus said:**
> The files (of typical size ~100KB) will be created (written) once per day.Will you be doing much deletion? Also, do you have a feel for the ratio of reads to writes? In other words, once a file is created, do you suppose it'll be read very often? The main reason for asking that has to do with the type of RAID to go for.

> **csharpplus said:**
> I can write the files as either 'text' or 'binary' format (is there a preference?)There's no distinction.

100k is an unfortunate file size, imo. It's pretty tiny, but slightly too big to be classed as "small". There are a few tricks you can use for storing & accessing small files, but I don't think any of them really apply :-( Is there likely to be much variation in the file sizes? Also, how rapidly do these files get created? (I'm just wondering where the bottlenecks are likely to be ... eg processor speed versus disk I/O, etc.)

In general, it's not efficient to create a whole directory just for a handful of files. Ideally, you should be thinking in terms of thousands (perhaps tens of thousands) of files per directory ... Among other things, you'd want the number of inodes per file to be as close to 1 as possible. By the sound of it, that may not possible with your application though.

For example, one fairly efficient approach would be to use a hashing algorithm to name your files. You could create 256 directories called "00" .. "FF", each containing 256 more (similarly named) directories. A file whose name started "1E39..." would be stored at /1E/39. Assuming the hashing algorithm was reasonably good, that'd give you a nice, even spread of about 1,500 files per directory, and only 65 thousand wasted inodes, instead of 5 million.

Anyhow, if you'd like to stick with an Extended filesystem format, I'd suggest Ext2, if for no other reason than to cut out unnecessary overhead. One issue with Extended filesystems is that you'll have to decide at the outset how many files/directories you want to store, and make sure you have enough inodes to accommodate them all.

**Edit:**

Something kinda obvious just occurred to me. Even if your Ext4 filesystem does have enough inodes to store 5,000,000 directories (which I doubt), the mere act of creating them would consume almost half of the space available on it. To make matters worse, 5M directories x 3 files x 100k = 1.4TiB additional space required to store the data itself.

---

### Post by csharpplus on 2010-10-10
Kidders,

Thank you for your help.

> 
For example, one fairly efficient approach would be to use a hashing  algorithm to name your files. You could create 256 directories called  "00" .. "FF", each containing 256 more (similarly named) directories. A  file whose name started "1E39..." would be stored at /1E/39. Assuming  the hashing algorithm was reasonably good, that'd give you a nice, even  spread of about 1,500 files per directory, and only 65 thousand wasted  inodes, instead of 5 million.


As a matter of fact,  this works perfectly for me. meaning, my application does not require so  many directories. but it does require many files (each of size say of  100KB or so). I **thought** (mistakenly, as it appears) that 1000s of  files are too much for a directory, but given that's not the case, I am  happy to go this route (using the hashing algorithm you suggested).

What is the optimal number of files (approx.) per directory, in your opinion?

---

### Post by kidders on 2010-10-10
No problem.

> **csharpplus said:**
> What is the optimal number of files (approx.) per directory, in your opinion?You should probably keep it under 30,000, but as long as the dir_index option is enabled, it really shouldn't matter how close to that number you go. Imo, the number of files per directory isn't something you should worry about too much. Much more important are ...[LIST]
[*]Making the depth of the directory tree as low as possible.
[*]Keeping the number of directories reasonably small.
[*]Reducing the complexity of computing a good filename as much as you can.
[/LIST]

Broadly speaking, the number you're looking for is something between 5 (ie so small that creating all the empty directories would consume *serious* disk space and waste 20% of your inode table) and 30,000 (ie so large that you approach the practical limits of Extended filesystems). It's certainly not uncommon for directories to contain something in the region of a thousand files, so my suggestion of 1,500 is pretty modest, really.

By the way, while you were typing your last message, I was busy editing my previous one, just to draw some attention to your disk space requirements. They're ... well ... considerable!

---

### Post by csharpplus on 2010-10-10
thanks again, kidders.

Can a setup with -- say -- 10000 directories be OK? how much space does a directory (just it, excluding any files on it) consume?

---

### Post by kidders on 2010-10-10
I guess so :-)

> **csharpplus said:**
> how much space does a directory (just it, excluding any files on it) consume?In general, 1 block.

---

### Post by csharpplus on 2010-10-10
Thanks. your help is greatly appreciated!

---

### Post by kidders on 2010-10-11
No problem :-)

---

### Post by stankrugger on 2010-10-11
Well guys I am not that much expert programmer. I could not implement these  solutions. Please let me know if there is a simple way out.

---

