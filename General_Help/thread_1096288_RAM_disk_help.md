---
title: "RAM disk help"
date: 2009-03-14
forum: General Help
---

### Post by GeoMoon5 on 2009-03-14
Hello everyone!

I have a very specific RAM disk question. Hope someone can help. Here it is.


QUESTION:
If I'm running 64 bit Ubuntu 8.10 server edition, will I be able to create a RAM disk larger then 4 Gigs and run a 32 bit dedicated server application on the RAM disk? I'm not sure if it's possible because in order to get the 32 bit dedicated server application to work in the 64 bit OS environment, I have to apt-get the 32 bit libraries. I have no idea what that will do to how the OS accesses the RAM, how the 32 bit application will use the RAM, or if apt-getting the 32 bit libraries will suddenly make only 4 Gigs of my RAM accessible.


PERTINENT INFORMATION:
I want to run the HLDSupdateTool released by Valve so I can host a bunch of game servers. I'm already doing just that, but now I want to move everything to a giant RAM disk so the servers will run more efficiently and make my game servers a bit more appealing. (If it were possible, I'd like to move the OS to the RAM disk too, but that's another project). I'll occasionally back everything up to a spin-up HD, and this machine will just be hosting game servers for the time being, so sudden power failures won't be an issue. This is sort of an in-between solution to make my server more speedy until Valve releases a 64 bit version of their dedicated server application. I'm not exactly holding my breath though... 


MORE PERTINENT INFORMATION:
I'm running Ubuntu 8.10 server edition. The OS is installed on 64 bit hardware, but I'm currently running the x86 version of Ubuntu so that I can run a 32 bit dedicated server application without the possible slowdowns of running that 32 bit application with downloaded 32 bit libraries on a 64 bit system. I'm not hosting anything 64 bit on that server right now, so I figure I'm better off performance-wise and reliability-wise keeping the OS 32 bit native. (I'm running 'hldsupdatetool' to host various HL2 mod game servers and valve in its infinite wisdom has seen it fit to not quickly release a 64 bit version of their dedicated server application)


Please any help would be appreciated.
Thank you in advance for any info!

---

### Post by martrn on 2009-03-14
> **GeoMoon5 said:**
> Please any help would be appreciated.Thank you in advance for any info!

[URL="http://www.vanemery.com/Linux/Ramdisk/ramdisk.html"]
http://www.vanemery.com/Linux/Ramdisk/ramdisk.html[/URL]

Ubuntu will by default create a ram disk.  You can create more ramdisk(s) / as many as you need when booting up.

Standard ubuntu kernels 32bit kernels will only support upto 3GB or ram and unless you recompile your kernel to get more you will not see any more.

The largest option when compileing the 64bit kernel I belive you can address 64GB of it.  You should be able to get more if you get a patch for your kernel but it dependent on the chipset of your motherboard.

Much of improving anything you are talking about will involve re-compiling a standard linux kernel.

---

### Post by GeoMoon5 on 2009-03-14
That's a great link. I came across that last night and found it very helpful.

I'm still curious; however, about whether or not I can have a larger then three Gig RAM disk on a 64 bit OS, even after apt-getting the 32 bit libraries to allow me to run the 32 bit dedicated server application in the 64 bit OS.

Will installing those 32 bit libraries change the 64 bit OS enough to prevent me from using more then three Gigs? (sometimes four Gigs, looks like my 32 bit system sees all four Gigs, sweet!)

---

### Post by martrn on 2009-03-14
> **GeoMoon5 said:**
> I'm still curious; however, about whether or not I can have a larger then three Gig RAM disk on a 64 bit OS, even after apt-getting the 32 bit libraries to allow me to run the 32 bit dedicated server application in the 64 bit OS.

Will installing those 32 bit libraries change the 64 bit OS enough to prevent me from using more then three Gigs? (sometimes four Gigs, looks like my 32 bit system sees all four Gigs, sweet!)

[https://help.ubuntu.com/community/32bit_and_64bit]("https://help.ubuntu.com/community/32bit_and_64bit")

It is possible to run a 32bit operating system such as ubuntu by recompiling your kernel with more than 4GB ram (eg 6GB on a 32bit system)  You would need to use a 1GB/3GB swap in your first area of ram where the kernel will not leave the memory that is addressable within the 32 bit and swap areas of memory around.

Applications get put where they are told to be put by the kernel.

Note : you can have a three Gig RAM disk on a 32 bit OS, and have a 3GB memory area to run applications on.  (eg 6GB ram on a 32bit OS), don't try it - needs kernel recompile.

Theoretically there should be no problems with what you are suggesting on a 64bit system. ??

Don't forget 8GB of ram chuking around 32bit applications is going to cause a lot of extra 32bits of 0's   eg 00000000000000000000000000000000  for each 32 bit interger so you would need more memory in a 64bit system than a 32 bit system.

---

### Post by GeoMoon5 on 2009-03-15
Hmmm, well I'm not looking to get the 32 bit OS to handle more then three GB of RAM, as it sounds like doing that involves a process that's more involved then my current capacities as a Linux user can handle.

It sounds like you believe what I was asking about *could* work. That being, running the 32 bit application on the 64 bit OS and hoping that the downloaded additional libraries to allow the 32 bit application to work doesn't confuse the OS into thinking it can't see all the RAM. 

That whole bit you mentioned about the 32 bit applications in the 64 bit OS causing extra work seems a bit daunting to me.  o.o;; Are you saying that the RAM will perform more slowly?

"Don't forget 8GB of ram chuking around 32bit applications is going to cause a lot of extra 32bits of 0's eg 00000000000000000000000000000000 for each 32 bit interger so you would need more memory in a 64bit system than a 32 bit system."

Perhaps I should just take a bigger financial hit and get some regular HDs and a RAID controller card and go the RAID rout.

---

### Post by martrn on 2009-03-15
> **GeoMoon5 said:**
> That whole bit you mentioned about the 32 bit applications in the 64 bit OS causing extra work seems a bit daunting to me.  o.o;; Are you saying that the RAM will perform more slowly?

Perhaps I should just take a bigger financial hit and get some regular HDs and a RAID controller card and go the RAID rout.

No If you have a 64bit OS storing and processing 32bit data/programs, then when reserving memory (say on stack space), it will require say about 15% more ram, its not very efficient at handling 32bit data, and when processesing it in the CPU it will not get any where near more quicker.

It would be better to make your 'server more speedy' if you run 64bit applications in a '64bit enviroment'.

Weather you gain more speed with by adding HDs and a RAID controller or more memory and lots of RAM drives is abut trial and error.

EDIT
-----
There are a number of factors, including the chip-set of the motherboard, the amount of processing of complex algorithms (eg the way the software is written), the type of controllers RAID/SATA,  there are many factors to take into consideration not just one, but more ram is always better.

---

### Post by GeoMoon5 on 2009-03-15
Hmmm, well, it's sounding more and more to me like I should continue using 32 bit Ubuntu for my server as it appears there are some significant inefficiencies with the 64 bit OS handling the 32 bit application. Pitty. I was hoping to be a sneaky bugger and use the 64 bit OS to have a big, fancy RAM disk and still run my 32 bit apps. I suppose I'll read up more on what goes into recompiling the kernel and see if I can get the 32 bit OS to squeeze out a few more drops of RAM. As for now, I think I'm going to do a RAID system once I get the money. Either that or save up my money so I can buy a PCIe RAM disk card once one comes out.

Thanks for all your help! I'm still open to more suggestions info BTW.

---

### Post by martrn on 2009-03-15
> **GeoMoon5 said:**
> Either that or save up my money so I can buy a PCIe RAM disk card once one comes out.

I've always want x15 pci ram cards filled with memory.  PCIe ram cards, hmmmmmm. :D

---

### Post by dcstar on 2009-03-15
> **GeoMoon5 said:**
> 
.........
I want to run the HLDSupdateTool released by Valve so I can host a bunch of game servers. I'm already doing just that, but now I want to move everything to a giant RAM disk so the servers will run more efficiently and make my game servers a bit more appealing.
........

You want to sacrifice RAM that the OS will efficiently manage for disk caching anyway to make inefficient RAM disks and reduce the resources that the OS will have available.

Why do you believe that this will make your servers any more "efficient" or "appealing"???

---

### Post by mrsteveman1 on 2009-03-15
Installing 32bit libraries doesn't change anything, but i doubt a 32bit program will be able to access 4gb+ of ram even on a 64bit OS.

If you are running the 32bit ubuntu, you can install the server kernel which is PAE enabled, for more than 4gb ram.

You really don't need to store the files for whatever server this is you are running in ram, that won't make it any faster. What you need is just to ensure that there is enough ram to run the program, give it whatever it wants and make sure no swapping takes place. Get a fast main hard drive, perhaps even an SSD or a RAID array and you'll have plenty of speed in storage.

---

### Post by sdennie on 2009-03-15
As dcstar said, using a RAM disk to speed up things that are constantly being used isn't likely to work and might even be slower.  The OS essentially uses free memory as a dynamic RAM disk and stores things you use most in RAM.  The difference is that it's able to drop things out of the cache that aren't being used anymore to make room for things you are now using which could potentially make it faster than using a static RAM disk.

You are probably better off looking at preload and/or readahead and seeding the cache on startup with what your server actually uses under load.  That allows you to essentially create a RAM disk that the OS will then be able to manage effectively and prevents all the other side effects of making huge RAM disks.

---

### Post by GeoMoon5 on 2009-03-15
Thank you cdstar, mrsteveman1, and sdennie


@ dcstar,   I'm not worried about sacrificing RAM if I can use 64 GB of the stuff. But yah, I didn't know there was disk caching going on. Is that really done so efficiently that setting up a RAM disk would yield negligible benefits? Would it actually be detrimental having a RAM disk?

As far as why I want to do this, I was under the impression that certain tasks, such as loading up the large maps, would go much faster if the dedicated game server program was stored in a RAM disk or a RAID system. I'm not expecting a RAM disk to make everything lightening fast, I'm just hoping it will make a couple things run faster. It kind of looks like disk caching already does that.


@  mrsteveman1,   Hmmm, yah I suppose there isn't really a whole lot of writing to the HD when running a game server. Maybe a RAM disk or RAID system would be over-kill. Especially if moving everything to a RAM disk wouldn't speed anything up.   : /


@ sdennie, I like this seeding idea. Perhaps I'll just seed all the large maps into the RAM and leave everything else alone.

---

### Post by sdennie on 2009-03-15
> **GeoMoon5 said:**
> 
@ sdennie, I like this seeding idea. Perhaps I'll just seed all the large maps into the RAM and leave everything else alone.

Have a look at both preload and readahead.  Readahead brings files into the cache in an order that reduces disk seek times.  Preload learns whats being cached the most and uses readahead to keep it in the cache.  Preload could drastically reduce popular map load times once it's learned what's being used the most.

---

### Post by GeoMoon5 on 2009-03-16
Thank you all for your help and knowledge. I can't wait to try out the 'preload' and 'readahead' trick I found out about.

Cheers!


^.=.^

---

