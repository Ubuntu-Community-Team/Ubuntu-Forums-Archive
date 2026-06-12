---
title: "4GB memory on 32bit ? impossible ?"
date: 2008-08-18
forum: Desktop Environments
---

### Post by artin1982 on 2008-08-18
Hi
I have a pc with 4gb memory and I have access to just 3.2gb of memory :(

my pc:
Q6600
2*2GB memory
ECS P35T-A

Bios detects 4GB ..
memtest detects 4Gb ..

I tried to install server's kernel but no success ...
I tried to compile kernel from kernel.org with highmem 4gb and highmem 64gb but again no success ...
I tried to put mem=4gb in grub but again no success 

what is the problem ?  :confused:

---

### Post by aurelieng on 2008-08-18
Yep, you have to use a 64-bits OS if you want to adress 4Gb or more.

---

### Post by artin1982 on 2008-08-18
> **aurelieng said:**
> Yep, you have to use a 64-bits OS if you want to adress 4Gb or more.

yes but I heart I can have 4gb up to 64gb memory in 32bit but I have to enable PAE ...  I enabled it but no success ...  I dont know what is wrong ...

---

### Post by forger on 2008-08-18
You can use the ubuntu server kernel image, it has PAE enabled by default.
Note that not all processors have PAE :)

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
> In computing, Physical Address Extension (PAE) refers to a feature of x86 and x86-64 processors that allows more than 4 gigabytes (GB) of physical memory to be used in 32-bit systems, given appropriate operating system support.[1] PAE is provided by Intel Pentium Pro and above CPUs (including all later Pentium-series processors except the 400 MHz bus versions of the Pentium M), as well as by some compatible processors such as the Athlon and later models from AMD.

More info:
[http://ubuntuforums.org/showthread.php?p=5364146](http://ubuntuforums.org/showthread.php?p=5364146)

linux-server package:
[http://packages.ubuntu.com/hardy/linux-server](http://packages.ubuntu.com/hardy/linux-server)
install using apt:
[apt://linux-server]("apt://linux-server")

---

### Post by artin1982 on 2008-08-18
> **forger said:**
> You can use the ubuntu server kernel image
[http://packages.ubuntu.com/hardy/linux-server](http://packages.ubuntu.com/hardy/linux-server)
[apt://linux-server]("apt://linux-server")

thanks but in the first post I said tried this too but it's showing 3.2gb memory

---

### Post by artin1982 on 2008-08-18
>forger
how can i find that cpu support PAE or no ?

//

it seems that I've posted my question in a wrong section.
MODs please move this topic to correct place if its in a wrong place

---

### Post by coffeecat on 2008-08-18
[This link]("http://www.dansdata.com/askdan00015.htm") may be useful. It's written mostly for Windows, but it's true for any 32-bit OS. I have no experience of PAE, but with only 4GB of memory it's possible you may still hit the problem Dan describes. See further on in the article for a mention of PAE, particularly:

> PAE's no good to the everyday 3Gb-problem-afflicted user, though, for two reasons.

---

### Post by Kevbert on 2008-08-18
You may need to set the bios to use the 'memory hole' to be be able to use up to 3.8Gb of your 4Gb as some memory addresses are historically used for peripherals above approx 3.2Gb limit.

---

### Post by timcredible on 2008-08-18
are you sure some peripherals like a video card aren't using some of that memory?  that would explain why the bios sees it, but the OS doesn't - because it's there, but being used by non-OS resources.  i wouldn't think a video card would use 800K of shared memory, but maybe there's more than 1 thing taking some memory?

---

### Post by artin1982 on 2008-08-18
> **Kevbert said:**
> You may need to set the bios to use the 'memory hole' to be be able to use up to 3.8Gb of your 4Gb as some memory addresses are historically used for peripherals above approx 3.2Gb limit.

I just have just "Memory Remap Feature" which is enabled by default . I dont see anythings like "Memory Hole" in the bios ..

Maybe this is the problem reason ? :(

I am changing my motherboard next week ( not because of this issue ) I hope the new motherboard support this option :D


> **timcredible said:**
> are you sure some peripherals like a video card aren't using some of that memory?  that would explain why the bios sees it, but the OS doesn't - because it's there, but being used by non-OS resources.  i wouldn't think a video card would use 800K of shared memory, but maybe there's more than 1 thing taking some memory?

you mean memory for onboard graphic card ?  
now I'm using a ATI 2600 graphic card and I think it will not use ram ( I am not sure )

> **coffeecat said:**
> [This link]("http://www.dansdata.com/askdan00015.htm") may be useful. It's written mostly for Windows, but it's true for any 32-bit OS. I have no experience of PAE, but with only 4GB of memory it's possible you may still hit the problem Dan describes. See further on in the article for a mention of PAE, particularly:

thanks for that link , I will check it when I get home

---

### Post by Redmumba on 2008-08-18
Physical Address Extension (PAE) is controlled by the kernel; if you're not comfortable with kernel hacking (and don't be afraid, its a nightmare your first time), then you can use the Ubuntu server kernel.  The server kernel has PAE enabled by default.

> 
sudo apt-get install linux-server linux-headers-server


Source: [http://samiux.wordpress.com/2008/01/10/how-to-use-4-gb-ram-on-a-32-bit-ubuntu/](http://samiux.wordpress.com/2008/01/10/how-to-use-4-gb-ram-on-a-32-bit-ubuntu/)

Good luck!

---

### Post by artin1982 on 2008-08-18
> **Redmumba said:**
> Physical Address Extension (PAE) is controlled by the kernel; if you're not comfortable with kernel hacking (and don't be afraid, its a nightmare your first time), then you can use the Ubuntu server kernel.  The server kernel has PAE enabled by default.



Source: [http://samiux.wordpress.com/2008/01/10/how-to-use-4-gb-ram-on-a-32-bit-ubuntu/](http://samiux.wordpress.com/2008/01/10/how-to-use-4-gb-ram-on-a-32-bit-ubuntu/)

Good luck!

Thanks but I think you didn't read my first post ...
I said I used server kernel and I also compiled kernel from kernel.org with PAE enabled ! but none of them are working :(

I've read all of these links before posting my question ...

---

### Post by artin1982 on 2008-08-18
I think its my MB/Cpu problem :(

I tried with 64bit LiveCD and it recognized 4gb

---

### Post by Redmumba on 2008-08-18
> **artin1982 said:**
> Thanks but I think you didn't read my first post ...
I said I used server kernel and I also compiled kernel from kernel.org with PAE enabled ! but none of them are working :(

I've read all of these links before posting my question ...

Oops!  Sorry, kind of rushed to the finish line there...

In that case, I noticed you haven't tried the "enable-pae" option through GRUB; simple append 'enable-pae' to the end of your GRUB line, see if that helps.

If not, I think you're spot on... its a motherboard issue; I hope its not a CPU issue, since PAE has been enabled since the Pentium Pro/Athlon processors!

If all else fails, 64-bit is a sure-fire way of getting that full 4GB of memory.  Unless you've got a specific compatibility issue with going 64-bit, why not just take the plunge?

---

### Post by dinub1 on 2008-08-18
OK. This may be a bit uneasy to visualize, but that is a known fact. 32 bit O/S's simply cannot see or access more than 4 GB of RAM. 
Just imagine that the total number of memory addresses that a 32 bit O/S sees is 4 GB (2^32 bits). If you take into consideration that some adresses are already taken (mapped in memory) by peripherals, video card etc, and the O/S only can see 4 GB of RAM total, here the difference. The actual number you see as accessible memory is the free RAM Regardless if that is a Windows or Linux OS. Now if you use a 64 bit OS, that O/S can see much more memory addresses. This why if you use a 64 bit OS, it will alwways report the amount of installled RAM which in your case is 4 GB. This fact may be difficult to visulalize, but that is the way it is. It is not your motherboard or system faults, it's just a 32 bit O/S limitation that occurs in every system having 4 GB (or more) of RAM installed. If it happens that say your motherboard allows 8 GB of RAM to be installed, and you have that on your system, a 32 bit O/S will not report more than say over 3 GB of RAM, even if you know that physically you have more.

---

### Post by artin1982 on 2008-08-19
I think I've found the problem !

in my grub line I have this option "vga=788"  , seems its related to ATI driver ...
After removing it surprisly PAE worked properly ! :D 
but I had problem with 3D ..

no matter because I am changing my motherboard next week and the new motherboard will have the new Intel onboard graphic card ( 4500 series ) 


thanks everybody !

---

### Post by Warren North on 2008-08-19
Only problem I found so far in compatibility problems with the 64 bit Ubuntu. Even Windows 64 Bit will only run 64 bit programs I think?.
I do not think a lot is written yet for 64 bit. I feel I been better off waiting because when I used 64 bit Ubuntu it worked but it did not work with anything on my machine and I was stuck all the time. But I got to use 3.8 GB rather than 3.2. I just got over it and like running 3.2 with the 32 bit because it is much smoother. Unless being efficient is that important.

---

### Post by artin1982 on 2008-08-19
> **Warren North said:**
> Only problem I found so far in compatibility problems with the 64 bit Ubuntu. Even Windows 64 Bit will only run 64 bit programs I think?.
I do not think a lot is written yet for 64 bit. I feel I been better off waiting because when I used 64 bit Ubuntu it worked but it did not work with anything on my machine and I was stuck all the time. But I got to use 3.8 GB rather than 3.2. I just got over it and like running 3.2 with the 32 bit because it is much smoother. Unless being efficient is that important.

I think there are 2 problems ,
1-there is stability problem with some softwares and some of them doesn't support 64bit ..
2-number of 64bit users and developers and much less than 32bit users ... in 32bit when there is a bug many user will report it and there are many developers that will fix bugs very soon .. for example there was a bug in wine 64bit and it took about 2-3 months that they fixed it completely !

now I again checked and I see following mem report using 4GB in 32bit with PAE:
```

#free -m
             total       used       free     shared    buffers     cached
Mem:          4052        646       3406          0         60        316
-/+ buffers/cache:        270       3782
Swap:         3906          0       3906


```

3.95GB is it ok ? :D

---

### Post by jacksaff on 2008-08-19
There is no 64bit problem with linux.
Everything in the repositories (ie. a lot) is compiled to run on 64bit and there are libraries you can install that let 64bit linux run binaries compiled for a 32bit system (ia32libs from memory but I'm not sure).
Even flash plugins work fine in 64bit now. There really is no reason not to use it.
PAE will cause you more problems than using a 64bit distro.

---

### Post by forger on 2008-08-19
> **artin1982 said:**
> how can i find that cpu support PAE or no ?

I think the flag "pae" shows that:
```
cat /proc/cpuinfo | grep 'pae'
```

If it shows the "flags" line, then your processor probably supports PAE

---

### Post by cooke77 on 2008-08-20
Even under Windows (XP Pro).....4 Gig of Ram only shows as '3.2 Gig'.
What do you expect it to show?
The whole 4 Gig.
Just isn't done, considering the fact that the Motherboard's BIOS allocates(automatically).....'what is missing' of that 4 Gig of RAM....to the 'onboard' graphics/sound.
That's why it shows up...as LESS than the full amount.

---

### Post by pparks1 on 2008-08-20
> **Warren North said:**
> Only problem I found so far in compatibility problems with the 64 bit Ubuntu. Even Windows 64 Bit will only run 64 bit programs I think?. Actually, 32-bit apps run in a compatibility mode...but quite often these run slower than would be typical under a 32-bit OS.

Personally, I wouldn't worry about the small amount of RAM that you aren't utilizing.  Most people don't really have a good reason for having all of that RAM anyway.   And if you really want to get every bit of RAM, go with a 64-bit install.   I know for quite a while there were numerous problems with drivers and such...but I think most of those things have been resolved.   I'm still running 32-bit though...and I have 4GB of RAM...which I only come close to utilizing when I run virtual machines :)

---

### Post by MaindotC on 2008-09-17
Can't you just recompile the kernel with an option that enables long address formats?  I saw it one time for someone who had a similar issue but I can't seem to locate the thread.  There was even a help.ubuntu.com link :(

---

### Post by dinub1 on 2008-09-17
I guess not. 4 GB RAM is an upper limitation of ANY 32 bit OS. OS cannot read/recognize/deal with more than that, and as hardware devices occupy some RAM addresses via mapping, 32 bit OS's only see the remaining RAM, that is always less than 4 GB. With 64 bit OS there is a different story.
I would agree that 4 GB of RAM is not needed for everyday applications and it is only beneficial in heavy multimedia applications.

---

