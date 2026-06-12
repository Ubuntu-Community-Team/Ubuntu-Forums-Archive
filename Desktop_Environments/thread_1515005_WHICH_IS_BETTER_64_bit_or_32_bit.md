---
title: "WHICH IS BETTER? 64 bit or 32 bit?"
date: 2010-06-21
forum: Desktop Environments
---

### Post by guyshoxton on 2010-06-21
hi! i have AMD Turion 64X - which ubuntu would be better for me?

i currently have Ubuntu 10.04 LTS 32bit... and it runs perfectly fine, and plus i like 32bit because it supports some programs that 64bit didnt let me use..

may some one give me an opinion? and can you also say why 32 bit or 64 bit is better please??

thanks! :shock: =D

---

### Post by wilee-nilee on 2010-06-21
Dual boot both and compare them, only you will know what works best for you grasshopper.;)

---

### Post by phaedon on 2010-06-22
I prefer 32bit for Desktops for the reason you stated more applications are compatible with it as well most desktop apps don't need 64bit.

I use 64bit for servers for better performance.

---

### Post by tomillares on 2010-06-22
I had karmic in 32  bits. Now I use lucid in 64 bits. I have a lot of programs, and I found all for 64 bits. The only problem we have now is that adobe is not developping flash for linux 64 bits, and the last beta release of adobe flash 10 for linux 64 is not secure.

---

### Post by cascade9 on 2010-06-22
I perfer 64bit for the extra speed (admittedly only a few %). 

> **guyshoxton said:**
> i currently have Ubuntu 10.04 LTS 32bit... and it runs perfectly fine, and plus i like 32bit because it supports some programs that 64bit didnt let me use..

Never had that issue here, everything I've wanted to use I've found in 64bit without a problem. 

What programs did you have issues with?

---

### Post by coskierken on 2010-06-22
I have switched over to 64-bit even on my laptop c2duo with only 1.5gigs of ram.  The resource use is still low and it runs pretty good.  On my desktop, it is a c2quad at 3.4Gs with 8Gigs of ram/64-bit and when I crack a movie with Handrake it takes only on average 20 minutes.  This is were it does make a difference as it is cpu intensive.

---

### Post by rizzeh on 2010-06-22
> **guyshoxton said:**
> ...it runs perfectly fine...

keep it 32bit :popcorn:

Don't forget that 64bit takes up more ram and if you have less than 3Gig then the benefits are minimal considering additional pain in getting things work on 64bit. 
 However if you like tinkering - it's a different story. 
My main desktop/gaming pc - Sidux 64x
Home media server/rtorrenter - ubuntu 32x
Laptop - Mint 32x

---

### Post by mbsullivan on 2010-06-22
Yeah... if 32-bit works for your needs, then stick with it.

64-bit really has a compelling performance advantage for a few compute intensive programs (audio/video encoding, etc.). It's also handy to support > 3 GB of RAM without rolling your own kernel.

Programs will use more RAM, though... so as long as you don't have lots of RAM or do compute intensive tasks, there's no reason to use it.

Mike

---

### Post by kelt65 on 2010-06-22
64 bit is better if you have > 1GB of memory, although the 32 bit kernel has workarounds for up to 4GB. It isn't faster, but there really aren't any drawbacks to 64 bit any more, so I say, go for it, you may as well.

---

### Post by PRC09 on 2010-06-22
I use 32bit with the PAE kernel (it installed automatically) with 4gb of ram and it runs faster than my 64bit machine...I have 2 identical machines 1 32bit and the other 64......Does anyone else use this kernel???


[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by mbsullivan on 2010-06-28
>  I use 32bit with the PAE kernel (it installed automatically) with 4gb of ram and it runs faster than my 64bit machine...I have 2 identical machines 1 32bit and the other 64......Does anyone else use this kernel???


[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

I used to... How are you judging it being faster? While I didn't qualitatively notice any slowdown, it doesn't sound right that it'd be faster than the 64-bit extensions that are built into the ISA.

Also, are you compiling your own kernel, or using the server versions in the repositories?

Mike

---

### Post by cascade9 on 2010-06-29
> **mbsullivan said:**
> I used to... How are you judging it being faster? While I didn't qualitatively notice any slowdown, it doesn't sound right that it'd be faster than the 64-bit extensions that are built into the ISA.

I'm wondering the same. 

Not that benchmarks are the be-all and end all, or always right, but 32bit PAE seems to be slower all roud that 64bit- 

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by PGHammer on 2010-06-30
> **phaedon said:**
> I prefer 32bit for Desktops for the reason you stated more applications are compatible with it as well most desktop apps don't need 64bit.

I use 64bit for servers for better performance.

I use x64 on any system with a capable processor and 1 GB of RAM or more.  (Linux, Windows, etc.)

Not for increased performance, but increased security (Windows) and increased *stability* (all cases so far).

That extra stability is almost a necessity if you test applications or are a developer; writing apps (or even a seemingly low-stress activity such as kernel and driver compiles) is far from stress-free (on the system in question, let alone the system's user).  I don't write code any more (I have a background in it, primarily databases but some C++ as well), but a typical Linux user (especially if they act as their own admin) will do some compiling at some point (even if it's nothing more than graphics drivers), as that is part-and-parcel of using Linux (even newbie-oriented distributions such as 'buntu).  If you test Linux distributions (such as Maverick Meerkat), the inherent instability in a testing-OS regime makes it hard enough to find stresspoints, in addition to it taking less to stress a 32-bit OS (any 32-bit OS) to its crash-point (Linux distributions may have fewer stresspoints than Windows; however, crash-proof they are not!).

Lastly, despite the dearth of native x64 applications, it's just as easy to run the 32-bit versions that (as is the case with Windows) still constitute the vast majority of applications - just make sure you keep the ia32 versions of your dependencies up to date using your updater of choice.

Despite having only 3 GB of RAM, the only time I ever run a 32-bit OS is in a virtual machine.

---

### Post by 3Miro on 2010-06-30
I have been exclusively using 64-bit Linux for regular desktop use for 2 years now. The only issues that 64-bit Ubuntu has come from Adobe's bad 64-bit flash (for which there are several workarounds), some 32-bit windows codecs for some videos (this is rare and it can be fixed with compiling custom 32-bit mplayer, which is not very hard) and some printer drivers have only 32-bit version.

Unless you have a severe case of 32-bit printer driver problems, go for 64-bit (you can work around those as well with Virtual Box, bt it can get somewhat ugly). The added speed from 64-bit on all apps offsets the extra usage of RAM (unless you have less then a gig of RAM, but then you should probably get more RAM, at any rate old computers with <1GB of RAM will probably not have 64-bit capable CPUs anyways).

---

### Post by Greggi on 2010-07-02
If you have more than 4 GB Ram , than use 64 Bit!

---

### Post by nikhilbhardwaj on 2010-07-02
some mod should move this to recurring discussions

---

