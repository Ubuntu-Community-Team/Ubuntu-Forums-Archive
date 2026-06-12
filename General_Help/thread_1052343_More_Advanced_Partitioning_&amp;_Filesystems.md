---
title: "More Advanced Partitioning &amp; Filesystems"
date: 2009-01-27
forum: General Help
---

### Post by jaminux on 2009-01-27
Hi all,

I have been using Ubuntu for nearly 2 years now and now I want to find out a little more about Partitioning & Filesystems. 

Does anyone know where I can find information concerning the following:

1) I know how basic partitioning works (i.e. logical, extended, primary partitions, how to make a / partition, how and why to use swap, and how use and make /home partition), but I have noticed that there are various other partitions you can make such as /boot etc etc. Where could I find information concerning how and why to use these additional partitions?

Oh and I wouldn't mind finding out about the different formats you can make partitions (stuck to ext2, ext3 and ext4 so far).

2) I would like to know more about the Filesystem and how and why data is stored within it. 

For example, I know that your personal data is stored  in /home/xxx/, but would like to know if this is strictly true all the time. And what is stored in the hidden directories made by programs in your home directory.

Another example would be where programs are stored. I hate to bring a Windows (ew) example into things, but is there are Linux equivalent to program files.  

Links to precise guides rather than huge technical manuals would be much appreciated.

Thanks,
James

---

### Post by jaminux on 2009-01-27
Oh and to add a little more to this the following (possibly simplified) was explained to me when I was in school concerning why Windows (ew) had to defragment:

Hard disks fragmented because when data was deleted the data was not actually removed, rather a flag was simply added showing the data as deleted. This was why people (police for example) could restore data that had been deleted and why the hard disk became fragmented over time.

This was also true of data that had been copied, except the flag on the copied data would point to the location of the current data.

Defragmentation was the processes of removing these flags to speed things up (since going through all the flags obviously took longer).

Could someone please point me in the direction of a guide that explains fragmentation (things were often over simplified at school.. or they were a blatant lie to make the teachers life easier) and why Linux does not need to defragment.

Thanks again

---

### Post by jocko on 2009-01-27
[Wikipedia]("http://en.wikipedia.org/wiki/Main_Page") can be a good place to start looking. [Here's an article on fragmentation]("http://en.wikipedia.org/wiki/Fragmentation_%28computer%29"), which I interpret as if your teacher was wrong (or you misunderstood your teacher?) And here's something about the [filesystem hierarchy standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"), which probably explains which files can be found where in the file system.

---

### Post by jaminux on 2009-01-27
Yea sounds like I was taught the wrong thing. I am not surprised, that teacher used to talk through his hat a lot about things he did not understand.

Thanks for the link on fragmentation. That is one down. I doubt Wikipedia will have much (specific) information about the partitioning or the filesystem though.

---

### Post by mb_webguy on 2009-01-28
The Wikipedia article on the filesystem hierarchy standard jocko mentioned should give you a good basic knowledge of the structure of the Linux filesystem, but if you're particularly masochistic when it comes to knowing everything about a subject, here's the actual [filesystem hierarchy standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html") in all its techie glory.

Here's an article on [Linux partitioning]("http://aplawrence.com/Linux/linux_partitioning.html"), including why you might want to put various directories on different partitions.  It's a bit dry, but informative.

Here's a [blog article on partitioning]("http://linuxhelp.blogspot.com/2006/01/effective-partitioning-how-and-why-of.html") that's a bit more readable.

And here's a rather extensive [How To on partitioning in Linux]("http://tldp.org/HOWTO/Partition/"), that also includes some discussion on putting certain directories on separate partitions.

---

### Post by jaminux on 2009-01-28
Ah great! 

This is what I wanted.

Cheers

---

