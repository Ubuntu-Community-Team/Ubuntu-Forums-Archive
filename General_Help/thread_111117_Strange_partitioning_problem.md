---
title: "Strange partitioning problem"
date: 2006-01-01
forum: General Help
---

### Post by crockettoo on 2006-01-01
Hi. I have upgraded my Ubuntu hard drive from 4 GB to a 40 GB drive. 
The old drive contained a ~3.5 GB ext3 main partition, and 200 MB linux-swap.
To move the main partition across to the new drive I used g4u, then grew it in GParted to about 37 GB, and then set up a ~1 GB linux-swap in the remaining space.

Here's the strange part: I now find the main partition is limited to ~4 GB accessible space, while GParted reports it as a 37 MB FAT32 (NOT ext3).

Does anyone know what went wrong?
thanks

---

### Post by az on 2006-01-01
[QUOTE=crockettoo]Here's the strange part: I now find the main partition is limited to ~4 GB accessible space, while GParted reports it as a 37 MB FAT32 (NOT ext3).

Does anyone know what went wrong?
thanks[/QUOTE]
You grew the partition, but not the filesystem on it!

Look in the ex2fs tools.  You can grow the filesystem to fit the partition.  I am pretty sure you need to unmount the partition to do that.  You should do it from a live cd like the ubuntu live cd or from the command line if you boot from the installer.

---

### Post by crockettoo on 2006-01-02
[QUOTE=azz]
Look in the ex2fs tools.
[/QUOTE]

Thanks for reply.
Where is ex2fs tools found? How is it named, exactly? Would it be available on the install disk if I boot from that?
I find a thing called "e2tools" in Synaptic as well as an "ext2resize" as well as a "testdisk" which all look interesting but dangerous.
Can you be more specific about how to grow the filesystem in the partition? First time I have come across a thing like this, particularly strange since I did not set it up as FAT32.
cheers

---

### Post by az on 2006-01-02
Sorry, I am at my in-laws and on slow slow dialup (28.8k!)  

e2fsprogs is already installed on your system.

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=e2fsprogs&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=e2fsprogs&version=breezy&arch=i386)


Use resize2fs.	


I cannot be more detailed, at the moment.  I know the installer has all of the neccessary tools built-in.  You boot it and let it install it's components and the go to the shell (CTRL-ALT-F2) and use parted or resize2fs.  You need to use a live cd like the installer or another live dc so that your partition is not mounted.

---

