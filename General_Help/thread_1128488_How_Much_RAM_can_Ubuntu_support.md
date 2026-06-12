---
title: "How Much RAM can Ubuntu support?"
date: 2009-04-17
forum: General Help
---

### Post by Noise... on 2009-04-17
One of the things that greatly bothered me with Vista was the fact that I couldn't use my computer's hardware to it's fullest in terms of RAM. It would cap out at ~3.5GB, rather than using the full 4GB.

Will Ubuntu recognize the full 4GB and make use of it?

---

### Post by MariusLV on 2009-04-17
I am no expert, but I believe you need to download the 64 bit version of Ubuntu (simply tick the "64 bit version" option before downloading from this page ---> [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)).

This all has to do with how operative systems handle RAM. If you intend to learn, I found an article which seems to explain the phenomenon quite well: [http://blogs.msdn.com/hiltonl/archive/2007/04/13/the-3gb-not-4gb-ram-problem.aspx](http://blogs.msdn.com/hiltonl/archive/2007/04/13/the-3gb-not-4gb-ram-problem.aspx).

Hope this helps you :-)

---

### Post by coffeecat on 2009-04-17
About 3.2 GB, actually. :wink:

For a 32-bit system, [here's the explanation]("http://www.dansdata.com/askdan00015.htm"), so, no, 32-bit Ubuntu will see no more memory than 32-bit Vista.

Unless you use a [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") enabled kernel. For Ubuntu that would be the server kernel, but you do take a degree of performance hit.

Have you got a 64-bit CPU? If so, install the 64-bit version of Ubuntu which doesn't suffer from the 3.2 or 4GB RAM barrier.

---

### Post by Therion on 2009-04-17
If your processor is 64-bit enabled then you can use a 64-bit edition of Ubuntu that will recognize your 4GB of system RAM.

---

### Post by Retaliation on 2009-04-17
yea, the guy above me is right, you need a 64-bit operating system. You must've had a 32-bit vista installation, which is why you couldn't see all 4 gigs. Just get the 64-bit version and you'll be able to address all your memory.

---

### Post by Noise... on 2009-04-17
Thanks for the info. I thought that might be the case, but figured I'd ask to be sure. :)

I'm not sure on my processor - I'll have to look into it. I only have 3GB of RAM anyway, but the computer can support 4GB. I just wanted to see if it was worth upgrading or not. 

Thanks again!

---

### Post by Slim Odds on 2009-04-17
This is a VERY HIGHLY discussed topic on these forums. The search feature is very helpful.

Basically, a 32 bit OS can only directly access 4GB of RAM. But, some other devices also need some memory space, so they eat into the 4G. Depending on the motherboard, OS and devices it can vary from about 3.2 to 3.8G of memory available to the applications.

A 64 bit OS has a huge memory space and motherboards that support this huge space and 64 bit OS's have a feature that moves some of the memory from below the 4G to the space above 4G to allow room for devices while still making the full memory available to the OS and applications.

---

### Post by MariusLV on 2009-04-17
Much as I would like you to use Linux, I feel I should also tell you that this really isn't a question of Ubuntu vs. Vista. Vista can also make use of all your RAM, but you will need the 64 bit version of Vista. So you don't HAVE to change to Ubuntu, but do try it anyway :-)

---

### Post by mb_webguy on 2009-04-17
The Linux kernel used by a default installation of 32-bit Ubuntu can recognize up to 4GB of memory, though the amount of usable memory available to the user will be slightly less than this.  A Linux kernel recompiled with PAE enabled can use up to 64GB of physical memory.

The Linux kernel used by 64-bit Ubuntu can theoretically recognize up to 17.2 billion GB of physical memory, but this is subject in practice to hardware limitations.  Current AMD64 implementations allow for up to 256TB of physical memory.  Current Intel 64 implementations allow for up to 1TB of physical memory.

Of course, you have to have a 64-bit architecture to use a 64-bit OS.  But even if you don't have a 64-bit architecture, Linux can take advantage of your memory *if* you don't mind compiling your own kernel.

---

### Post by stchman on 2009-04-17
> **Noise... said:**
> One of the things that greatly bothered me with Vista was the fact that I couldn't use my computer's hardware to it's fullest in terms of RAM. It would cap out at ~3.5GB, rather than using the full 4GB.

Will Ubuntu recognize the full 4GB and make use of it?

32 bit Ubuntu will recognize 2^32 bytes or ~4GB RAM.

64 bit Ubuntu will recognize 2^64 bytes or ~16 ExaBytes RAM.

---

### Post by madman100 on 2009-04-17
hi Noise  yes the 64 bit version support 4GB and more i have  5GB of ram and 4.9GB show up

---

### Post by tornadof3 on 2009-04-17
> **madman100 said:**
> hi Noise  yes the 64 bit version support 4GB and more i have  5GB of ram and 4.9GB show up

WOW you have 15GB of swap even though you have 5GB of physical RAM, that's pretty impressive. Have you ever managed to use swap space?!!

---

### Post by dcstar on 2009-04-17
> **tornadof3 said:**
> WOW you have 15GB of swap even though you have 5GB of physical RAM, that's pretty impressive.


An impressive useless waste of disk space.

---

### Post by bendib on 2009-04-19
32 bit anything 3.58 GB of RAM. Avoid 64 bit, shitty compatibility. You really don't need more than a gig with linux anyway. Heck, I used 256MB with kde 4! At a tolerable speed!

---

### Post by bendib on 2009-04-19
You are never gonna get an exact amount. Sometimes it's a little more, sometimes it's a little less. In my case it's a little more.

---

### Post by Slim Odds on 2009-04-19
> **bendib said:**
> ...Avoid 64 bit, shitty compatibility. You really don't need more than a gig with linux anyway. Heck, I used 256MB with kde 4! At a tolerable speed!

Speak for yourself. I use 64 bit and have no "compatibility" problems. And some of us DO NEED more than a gig. Depends on what you do and apparently you don't do much.

Heck, I give my virtual machines more than a gig.

---

### Post by stchman on 2009-04-20
> **bendib said:**
> 32 bit anything 3.58 GB of RAM. Avoid 64 bit, shitty compatibility. You really don't need more than a gig with linux anyway. Heck, I used 256MB with kde 4! At a tolerable speed!

Someone obviously does not know what they are talking about.  I run 64 bit Hardy on 3 different machines with no compatibility issues.  Flash 10, openJDK for Java all run very well.

I paid for a 64 bit processor I intend to use it to its potential.

---

### Post by stchman on 2009-04-20
> **Slim Odds said:**
> Speak for yourself. I use 64 bit and have no "compatibility" problems. And some of us DO NEED more than a gig. Depends on what you do and apparently you don't do much.

Heck, I give my virtual machines more than a gig.

Hilarious.

---

### Post by jp351 on 2010-07-23
hey guys, how goes it? ok, so here's my whole ordeal. right now i am using, and intend to keep, an asus mother board capable of running dual gfx cards. i have 2 3 gig cpu's and a 500gb hdd. my mobo will support a total of 8gb of ddr2 ram.. from what i understand ubuntu 32-bit will only run between 3 and 3.5gb........ 

question is, if i have, for example, 6 gb of ram, will ubuntu only say i have 3.2 or whatever even though it's using all of it? if i have 4 gb's and ubuntu will only use, say, 3... and i have a few things running cutting into about 0.75-1gb will ubuntu be accessing the other 3 no prob and list the programs running as using very little, using what they're using out of the 3 it's accessing, or what? i mean, is there any way to get ubuntu to use more/access more or whatever? why is it that both windows and ubuntu are compatible with the same amount of max ram? why is there a ram cap on OS's??

---

### Post by 3rdalbum on 2010-07-23
> **jp351 said:**
> hey guys, how goes it? ok, so here's my whole ordeal. right now i am using, and intend to keep, an asus mother board capable of running dual gfx cards. i have 2 3 gig cpu's and a 500gb hdd. my mobo will support a total of 8gb of ddr2 ram.. from what i understand ubuntu 32-bit will only run between 3 and 3.5gb........ 

question is, if i have, for example, 6 gb of ram, will ubuntu only say i have 3.2 or whatever even though it's using all of it? if i have 4 gb's and ubuntu will only use, say, 3... and i have a few things running cutting into about 0.75-1gb will ubuntu be accessing the other 3 no prob and list the programs running as using very little, using what they're using out of the 3 it's accessing, or what? i mean, is there any way to get ubuntu to use more/access more or whatever? why is it that both windows and ubuntu are compatible with the same amount of max ram? why is there a ram cap on OS's??

Please re-read the thread, it's all answered. 32-bit operating systems can address 4 GiB of RAM, but some of the addressable RAM is taken up by parts of your computer (most notably, your graphics cards). You'll end off with less than 4 GiB of system memory usable. The usable amount will be reported in System Monitor.

You can get Ubuntu to access more RAM by either installing the server kernel on 32-bit Ubuntu, or simply by installing 64-bit Ubuntu. The reason for the limitation is because 32-bit memory addressing can only address 4 GiB of RAM; it's like how you can't have 10,001 different postcodes if a postcode only consists of four digits.

The server kernel on Ubuntu does allow for a higher amount of RAM because of PAE, which makes use of 36-bit memory addresses. You might as well run 64-bit Ubuntu anyway.

---

### Post by jp351 on 2010-07-26
> **3rdalbum said:**
> Please re-read the thread, it's all answered. 32-bit operating systems can address 4 GiB of RAM, but some of the addressable RAM is taken up by parts of your computer (most notably, your graphics cards). You'll end off with less than 4 GiB of system memory usable. The usable amount will be reported in System Monitor.

You can get Ubuntu to access more RAM by either installing the server kernel on 32-bit Ubuntu, or simply by installing 64-bit Ubuntu. The reason for the limitation is because 32-bit memory addressing can only address 4 GiB of RAM; it's like how you can't have 10,001 different postcodes if a postcode only consists of four digits.

The server kernel on Ubuntu does allow for a higher amount of RAM because of PAE, which makes use of 36-bit memory addresses. You might as well run 64-bit Ubuntu anyway.

ok... since 64-bit has some minor compatibility issues, would the 36 of the server kernel as well? i don't run an incredible amount of processes on my system, but if i chose to run something later that was (personally) as of yet untested, i'd hate for it to be incompatible with the 36-bit server kernel if it IS with 32-bit os..

---

