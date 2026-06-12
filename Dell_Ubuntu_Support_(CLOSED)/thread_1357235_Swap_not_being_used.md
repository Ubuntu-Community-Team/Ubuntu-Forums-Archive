---
title: "Swap not being used"
date: 2009-12-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by texastwister on 2009-12-17
I have an Dell Mini 10 with the Dell/Ubuntu Netbook remix (8.04) factory installed.  Since this model was available with a solid state drive (On which you do not WANT swap), it was configured from the factory with no swap. 

Since mine has a 160 GB standard hard drive, I created a swap file, formatted it as swap, added it to fstab and used the swapon command.  

It now shows as available in free and top. -- However -- it is never, ever utilized, no matter how much is running in RAM.  

I checked the swappiness value of the kernel and it is at the default value.

I disabled swap, reformatted the file, and reenabled it -- still no change.

What more must be done to allow this netbook to use swap?

Output from some of the commands I ran:
```
$ free
             total       used       free     shared    buffers     cached
Mem:       1024764    1009844      14920          0      10244     514188
-/+ buffers/cache:     485412     539352
Swap:      2097144          0    2097144


$ cat /proc/sys/vm/swappiness 
60

$ cat /etc/fstab 
/dev/sda2	    /	            ext3 defaults	0 0
proc			/proc			proc	defaults	0 0
/mnt/swapfile/2gb.swap none swap sw 0 0


$ sudo swapoff -a
$ sudo mkswap /mnt/swapfile/2gb.swap 
Setting up swapspace version 1, size = 2147479 kB
no label, UUID=47fd81cf-279c-4214-a402-902fcc7da5e5
$ sudo swapon -a

```

---

### Post by mikewhatever on 2009-12-17
Swap is only used when the computer runs out of memory. In your case, there is over 500MB of free RAM available, so no point swapping. Run it for a few days, using various programs, and eventually, it should start using swap.

---

