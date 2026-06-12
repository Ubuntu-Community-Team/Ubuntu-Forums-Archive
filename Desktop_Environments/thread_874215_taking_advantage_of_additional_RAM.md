---
title: "taking advantage of additional RAM?"
date: 2008-07-29
forum: Desktop Environments
---

### Post by destr0y on 2008-07-29
Hi all,

Have been running Hardy for a while now, on a p4 3.2ghz PC with 1gb of RAM..   I recently bought a couple of 2GB memory sticks and have installed them in the box (bios is only seeing 3gb, but thats nothing to do with ubuntu) - mainly so I can do a bit of virtualisation later on.

I wasn't exactly memory-constrained when I had 1GB, so I'm not expecting to see any performance improvements by default, but...

***are there any tweaks I can use that will take advantage of that extra RAM (with tangible results)***? 

Cheers,
Brett

---

### Post by estyles on 2008-07-29
I don't have a direct answer to your question, but having 5GB of memory will be an issue if you're running the 32-bit version of Hardy (which is the default - if you don't remember if you picked 32 or 64 bit, then you probably have 32 bit).

In order to take advantage of all 5GB, you will need a 64-bit processor, and a 64-bit OS (which Ubuntu does have).  This may be why you can only see 3GB.  If you want to avoid the issue, I would just remove the 1GB memory stick and save it for when you might need it.  4GB will work fine with a 32-bit OS.  That's definitely a good idea if you're running a virtual machine though.  I have only 1GB and currently trying to find my windows disk to install on a VM, and the thought of only allowing it 512MB is kind of painful.

---

### Post by tuxxy on 2008-07-29
Upgrade to 64bit Hardy uf your running a 64bit system to solve the issue, any 32bit OS is not capable of using this much RAM.

---

### Post by benerivo on 2008-07-29
You can reduce the level at which ubuntu uses the swap partition (similar to the the virtual memory in windows) and instead force it to use your ram. This can be done by reducing your systems 'swappiness' and it's 'cache pressure'. See [here]("http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/") for full details. What i do, is to enter these two lines in to /etc/sysctl.conf, just before the first row of hash marks.

```
vm.vfs_cache_pressure=10
vm.swappiness=0
```

The end user experience is that i can load amarok, which takes about five seconds. Then i completely close it. When i open it again, it loads from ram and takes about two seconds to load.

---

### Post by destr0y on 2008-07-29
Thanks to all who've replied so far - I should clarify - the box only has two slots, so at best I will only ever see 4gb..  the 3gb thing is just a BIOS problem - I don't need to worry about Ubuntu's 32bit 4gb limitation, but thanks for the info regardless :)

> **benerivo said:**
> You can reduce the level at which ubuntu uses the swap partition (similar to the the virtual memory in windows) and instead force it to use your ram. This can be done by reducing your systems 'swappiness' and it's 'cache pressure'. See [here]("http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/") for full details. What i do, is to enter these two lines in to /etc/sysctl.conf, just before the first row of hash marks.

```
vm.vfs_cache_pressure=10
vm.swappiness=0
```

The end user experience is that i can load amarok, which takes about five seconds. Then i completely close it. When i open it again, it loads from ram and takes about two seconds to load.

Ahh Excellent, thats exactly the sort of thing I was after!   Thanks Benerivo!

---

### Post by estyles on 2008-07-29
I wonder if there's someplace where you can specify applications to be preloaded into memory at startup?  It would increase startup time, but decrease runtime when you open one of those apps.  If there's no such thing in Hardy, I would expect to see it at some point in the near future.

---

