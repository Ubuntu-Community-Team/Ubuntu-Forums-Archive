---
title: "OptiPlex 740  mem=1G boot issue"
date: 2010-06-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RayRuest on 2010-06-09
I've been fighting with the notorious Optiplex 740 issue for 2 days now.  I love these machines, but this is driving me nuts.  I've done the searching and managed to get 10.04 64-bit installed using the mem=1G boot option.  Any attempt to remove/change this option will halt the boot process in random ways (stalled splash, white lines, blank screen).  I REALLY need more than 1gig available to Ubuntu in this puppy.  Any ideas on how to proceed with this?  Any help is greatly appreciated!

Thanks
Ray

---

### Post by RayRuest on 2010-06-09
Update:

I've gotten the setup stable at either settings mem=2G, or removing 2 DIMMs to lower the physical memory to 2G.  Anything above 2G, either mem=X or physical does not work.  RAM passes memtest.

---

### Post by JinxCrossbow on 2010-07-07
I had the same problem with Ubuntu 10.4 32 Bit on my OptiPlex 740
My solution was
- installing ubuntu 9.10
- installing all updates
- installing the nvidea video driver
- updating 9.10 to 10.4 
Now my system works with Ubuntu 10.4 and 4GByte mem

Greetings Jinx

---

### Post by RayRuest on 2010-07-08
JinxCrossbow,

I tried this yesterday/today and it worked!  I had to go back to 9.04 64-bit Alternate install to start.  All the upgrades went flawless, and I'm now running 10.04 with 4 gig!

Sorta doesn't make sense.. what setting/file gets left behind after all those upgrades to get the job done I wonder?

Thanks for the help!

---

### Post by Baji P. on 2010-08-26
Jinx,

I had no problems installing with a 10.04.1 32-bit alternate CD, I was even able to install this [memory card reader]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820223103") in the empty floppy bay and it read my cell phone memory card without any fuss.

However, when I run **top** from the command line, I only see about 3.4 Gig of the 4 Gig RAM I have installed. This is typical for a 32-bit installation, it cannot address memory locations past some 3.x Gig boundary.

I am getting ready to follow RayRuest's steps, starting with a 64-bit alternate 9.04 CD to see if I can trade up to a 10.04.1 64-bit.

I'll be elated if I succeed.

Thanks for catching the first fish on this hook, I have been up at strange hours of the night trying to solve this problem.

-baji.

---

