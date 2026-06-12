---
title: "1gb of memory, how can I use this instead of disk swap?"
date: 2005-12-11
forum: General Help
---

### Post by bugman on 2005-12-11
In XP one can just turn off the swap file if you have enough memory and the disk rarely gets accessed.  I have a PIII Dell latitude.  Can I encorage Ubuntu to use the RAM instead of disk?  It seemsd the hard drive is grinding a way a bit more than it should.

---

### Post by loupy on 2005-12-11
remove the swap file from /etc/fstab and you'll only be using memory.

---

### Post by pizzach on 2005-12-11
One thing that I noticed that it seems you don't HAVE to make a swap partition.  If you use gparted when booting off of the live cd or using the built in partitioner on the installer cd you can destroy it, then format it back if you want it again.  (Make sure of this first though.)

In the end not having a swap partition is a bad idea especially in Linux from what I heard.  Don't know if it's true.  The computers I use have 1gb of ram but I still use a swap.

The fstab way would be easier though.  :p

---

### Post by Gray. on 2005-12-11
In Windows it's generally considered stupid to diasble the paging file, even with 2GB+ of RAM. I'm guessing it's the same in Linux.

---

### Post by eXSBass on 2005-12-11
I'm using 1 gb physical RAM and 512mb Swap. Is this enough?

---

### Post by bugman on 2005-12-11
[QUOTE=Gray.]In Windows it's generally considered stupid to diasble the paging file, even with 2GB+ of RAM. I'm guessing it's the same in Linux.[/QUOTE]
Well, call me stupid.   I've been doing it for years on my other laptop with 2gb of ram.  Seems to perform faster,  certainly not slower, and I save > 2gb of precious laptop diskspace and the battery lasts longer.

---

### Post by rejser on 2005-12-11
Doing measurements on my computer i've noticed that with more than 512 mb ram the computer slows down using swap. Quite much acctually, 
And running swap bigger than 300mb also slows down on my computer.
Try and see, remove the swap and try.

---

### Post by bugman on 2005-12-11
Definetly faster, particularly with Pan running,  no more disk thrashing.  Lets give it a day or 2 to see if anyhting bad happens. Thanks

---

### Post by soulestream on 2005-12-11
i have always believed that 512MB of swap is plenty. If you want to try running without swap, instead of removing your fstab entry(or commenting it out), you can always just use

sudo swapoff -a


that will turn swap usage off. 

I use swap on my laptop, but my desktop that has 1GB of RAM (and a less bloated distro) I dont have swap enabled. 

The only issue you may run into (and i havent) is that some windows apps use pagefile regardless of free memory, I dont know if any linux apps work similary.

soule

---

### Post by Gurgeh on 2005-12-17
ice one lads, i'll give that a shot... erm... i'm presuming you can just turn it back on with 'swapon'? Just in case it goes titsup

---

