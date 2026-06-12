---
title: "Turn off swap file if have lots of RAM."
date: 2009-02-27
forum: General Help
---

### Post by stchman on 2009-02-27
Hello all.

I am running Hardy 64 bit.  I currently run 6GB RAM.  Would it be a good idea to turn the swap file off?

I think with 6GB RAM there would be no need for the OS to hit the swap file.

Also is Ubuntu smart enough to ONLY hit the swap when it runs out of RAM?  If yes then this discussion is academic only.

Thanks.

---

### Post by glotz on 2009-02-27
I don't think it makes any difference whether you have that swap or not, that is, unless you hibernate, in which case you need at least as much swap as you have memory.

On the other hand, I guess no amount of memory is too much for some applications... ;)

Swapping in Linux is controlled by swappiness, see [https://help.ubuntu.com/community/SwapFaq#Performance tuning with ''swappiness''](https://help.ubuntu.com/community/SwapFaq#Performance tuning with ''swappiness'')

---

### Post by SuperSonic4 on 2009-02-27
There shouldn't be any need, I use 4gb and have none in swap. I still keep a small swap file though and it is not like hard drive space is at a premium

---

### Post by x33a on 2009-02-27
well if you use hibernation, then you need the swap. otherwise, it'll not be used in your case. you can always check how much (if any) swap/memory you are using with "free" command.

---

### Post by darco on 2009-02-27
Dont mean to hijack this thread but I have 8gigs of ram with a /swap partition of 256mb. I run a virtual machine for Win7. I noticed that it still goes to swap (5.3mb) even though I have swappiness set to 0 and the fact I have a huge amount of available memory.

 free -m
             total       used       free     shared    buffers     cached
Mem:          7923       7863         60          0       1463       5490
-/+ buffers/cache:        909       7014
Swap:          258          5        253

I am just trying to figure out why it goes to swap if I have so much mem available?

darco

---

### Post by binbash on 2009-02-27
as long as you don't use hibernate it is ok

---

### Post by brokenLockpick on 2009-02-27
I use no swap for my netbook, mainly to protect the SSD from repetitive write/erase operations, and I've noticed no ill effect even with "only" 2GB of ram.

---

### Post by fragos on 2009-02-27
With only 1GB of RAM my system rarely uses swap space. There's no need to turn off swap because with enough memory it won't be used except for hibernation which would require swap space equal to the size of memory. 

The kernel tries to keep a balance between available cache space and swap memory.  There is a "swappiness" parameter that it uses to weight that decision.  It's value can range between 0 and 100 with the default being 60.  100 keeps cache memory free by swapping often even if everything will fit in memory.  0 causes applications to shrink cache size to avoid swapping.  If you're running on a laptop and want to give your drives a chance to spin down and save battery power, use 20 or less.  The information I've found is more trend than scientific but it does give you basis of understanding and the ability to experiment a bit.  Believing that 100% is never an answer I chose a value of 10 and with 1GB of memory, I rarely find anything in swap space.  IMHO the elimination of swap space may be risky.

You can change swappiness by doing the following:

sudo gedit /etc/sysctl.conf

Find the line containing "vm.swappiness=" and change the number to the one you'd like to try.  In my case "vm.swappiness=10".

---

### Post by Yellow Pasque on 2009-02-27
> **darco said:**
> ..it still goes to swap (5.3mb) even though I have swappiness set to 0 and the fact I have a huge amount of available memory.
It's because you have swappiness set to 0. Set it to something like 10 or 20 at minimum. Read this to get a better understanding of what swappiness actually does: [http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

Also note this hilarious quote by a kernel developer who got tired of people who didn't understand how virtual memory works asking him questions about swappiness.
> "I'm gonna stick my fingers in my ears and sing 'la la la' until people tell me 'I set swappiness to zero and it didn't do what I wanted it to do.'"

---

### Post by Yellow Pasque on 2009-02-27
> **stchman said:**
> Also is Ubuntu smart enough to ONLY hit the swap when it runs out of RAM?  If yes then this discussion is academic only.
The discussion is academic because the Linux kernel is very good at managing free RAM. Keep the swap space unless you're running out of disk space.

---

### Post by darco on 2009-02-27
> **fragos said:**
> 

You can change swappiness by doing the following:

sudo gedit /etc/sysctl.conf

Find the line containing "vm.swappiness=" and change the number to the one you'd like to try.  In my case "vm.swappiness=10".

Dont forget to run sudo sysctl -p right after!

darco

---

### Post by darco on 2009-02-27
> **Temüjin said:**
> It's because you have swappiness set to 0. Set it to something like 10 or 20 at minimum. Read this to get a better understanding of what swappiness actually does: [http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

Also note this hilarious quote by a kernel developer who got tired of people who didn't understand how virtual memory works asking him questions about swappiness.

heh, funny, point taken...set it to 10...wish I could send a "thanks" your way...well I guess I just did!...

darco

---

### Post by dcstar on 2009-02-28
> **darco said:**
> Dont mean to hijack this thread but I have 8gigs of ram with a /swap partition of 256mb. **I run a virtual machine **for Win7. I noticed that it still goes to swap (5.3mb) even though I have swappiness set to 0 and the fact I have a huge amount of available memory.
.......
I am just trying to figure out why it goes to swap if I have so much mem available?

darco

Probably because the VM manager you use has a setting for swap use - VMware Server certainly does.

---

### Post by darco on 2009-02-28
> **dcstar said:**
> Probably because the VM manager you use has a setting for swap use - VMware Server certainly does.

yes it does but I followed this tip:

If possible (i.e. if you have enough memory), select the option "Fit all virtual machine machine into reserved host RAM". This will prevent swapping. The Option is in "Edit" -> "Preferences" -> "Memory". Not that this memory will not be available to Linux while vmware is running. 

darco

---

### Post by Thirtysixway on 2009-02-28
I leave my computer on, and I run multiple applications like firefox, thunderbird, songbird, filezilla, gedit, etc streaming music, checking myspace, checking emails, uploading to remote servers.

I only have 1.25 GB ram and using the "free" command it says I'm using 0 swap.  So if you have 6 GB ram you may not need swap.  But I'd keep it just incase.

---

