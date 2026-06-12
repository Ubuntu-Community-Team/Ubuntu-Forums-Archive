---
title: "Moving a boot partition"
date: 2008-12-21
forum: General Help
---

### Post by Jargv on 2008-12-21
The good news is I really like Ubuntu and want to allocate (much) more of my HD to the Ubuntu partition. 

The bad news is that the partition is the last one on the disk. This means I have to move the partition in order to resize it (or does it?). 

Here is what I've tried so far:

1- booting with a live disk and using parted to move the partition. This gave me an error message saying that the partition had an incompatible feature enabled. So this didn't work.

2- creating a new partition and copying the entire file system over (also from a live disk). This didn't work either and gave me a bunch of crazy error messages when I tried to run. I couldn't get past the login screen.

I guess the question is: what is the correct way to do what I am trying to accomplish?

Thanks in advance,

-Jargv

---

### Post by dcstar on 2008-12-22
> **Jargv said:**
> The good news is I really like Ubuntu and want to allocate (much) more of my HD to the Ubuntu partition. 

The bad news is that the partition is the last one on the disk. This means I have to move the partition in order to resize it (or does it?). 
.......

No, all you need is adjacent free space.

You may need to move/delete other partitions to have space to grow the existing Ubuntu partition - use the Live CD to boot off to do any of this.

There are many detailed posts on increasing partition size.

---

### Post by joehte on 2008-12-22
> **Jargv said:**
> 
2- creating a new partition and copying the entire file system over (also from a live disk). This didn't work either and gave me a bunch of crazy error messages when I tried to run. I couldn't get past the login screen.

I guess the question is: what is the correct way to do what I am trying to accomplish?


I did this a while ago, I don't remember all the details, but I think this webpage gives pretty nicely the details:

[http://it.toolbox.com/blogs/locutus/how-to-copy-linux-to-a-different-partition-12865](http://it.toolbox.com/blogs/locutus/how-to-copy-linux-to-a-different-partition-12865)

I also installed LVM so that I can easily add more space in the future, but that's another story...

---

