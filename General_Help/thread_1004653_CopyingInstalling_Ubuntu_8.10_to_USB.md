---
title: "Copying/Installing Ubuntu 8.10 to USB"
date: 2008-12-07
forum: General Help
---

### Post by maustin2 on 2008-12-07
I currently have a functional ubuntu server 8.10 configured with my required packages.

I have a 16GB usb flash drive that I wish to install and make bootable the above system. Is this possible and how?

Have searched for the answer but have not found it at this point. Any assist would be appreciated.


):P

---

### Post by dstein on 2008-12-07
Is this what you're looking for? [http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

---

### Post by maustin2 on 2008-12-08
Sorry I took so long to respone.

Not quite the solution I am looking for and I had seen this one.

I am seeking a way to copy the entire filesystem of the established 8.10 and all of the other packages I have installed to a 16GB USB flash drive. The results I seek is an exact copy of my current 8.10 system on the flash drive w/o having to recreate it.
Is this possible???

---

### Post by ciscosurfer on 2008-12-08
You might try Clonezilla or Ghost for Linux, both are discussed on other threads in this forum.

---

### Post by caljohnsmith on 2008-12-08
> **maustin2 said:**
> Sorry I took so long to respone.

Not quite the solution I am looking for and I had seen this one.

I am seeking a way to copy the entire filesystem of the established 8.10 and all of the other packages I have installed to a 16GB USB flash drive. The results I seek is an exact copy of my current 8.10 system on the flash drive w/o having to recreate it.
Is this possible???
If you're just concerned about copying the entire file system, you can copy over the entire linux filesystem using "cp -ax". I've used that method before with perfect success, so I know it can work. If you want specifics of how to actually go about it, how about posting:
```
sudo fdisk -l
```
And identify the source/destination partitions. We can work from there if you want.

---

### Post by ciscosurfer on 2008-12-08
@caljohnsmith,

In your opinion, would the copy method you suggest be quicker or more stable than other methods/apps?

---

### Post by maustin2 on 2008-12-08
Thanks caljhonsmith.

I will look into cp -ax and get back to you with results.Since you have done so with success, I will probably have the same results. Thanks again.

---

### Post by caljohnsmith on 2008-12-08
> **ciscosurfer said:**
> @caljohnsmith,

In your opinion, would the copy method you suggest be quicker or more stable than other methods/apps?
I think "cp -ax" could be quicker than a cloning program, because a true cloning program does a byte-for-byte low-level copy of the entire partition, including all the empty space; in contrast, "cp -ax" just copies over the existing file system, and in most cases the file system does not take up the full partition space. But Clonezilla claims to just copy the used bytes in a partition if the partition uses one of its supported file systems, so it's doing more than what a simple "dd" cloning command does. And I've never compared "cp -ax" vs. cloning first-hand as far as speed, so I don't know for sure. :) 

Also, I think that either copying the file system over via "cp -ax" or cloning the partition should both yield a stable copy in the end (if all goes well). I was only suggesting "cp -ax" because that's an easy way to copy the entire file system over when the destination partition is not the exact same size as the source partition; using something like Clonezilla is great as long as the destination partition is the exact same size as the source partition. From the Clonezilla FAQ:
> [B]Why Clonezilla can _NOT_ image from a large drive to a smaller drive?
[/B]
It's not easy to implement such a feature, since Clonezilla now is a partition "imaging" tool, by "imaging", it means clonezilla actually does not know the files themself, clonezilla just knows where the used blocks are. Because of this reason, the target partiton size must be equal or larger than the original one so that clonezilla can restore the used blocks on that partition. If the target partition size is smaller, then it will go wrong.
But cloning programs definitely have their good uses, I think using "cp -ax" is not the best solution in all cases. :)

---

