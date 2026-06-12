---
title: "Would there be any adverse effects if I installed 32bit ubuntu on my 64bit machine?"
date: 2009-02-15
forum: General Help
---

### Post by Peter_G on 2009-02-15
Would I loose any performance?

---

### Post by mb_webguy on 2009-02-15
Yes, but you might only notice it on resource-intensive tasks like program compilation and transcoding of video (where it would be *very* noticeable).

Why would you want to change to 32-bit, anyway?  It used to be that there wasn't much software available for 64-bit systems, but that's not true anymore.  With the exception of the Flash plugin (which is still in alpha for 64-bit Linux), everything I've wanted to install has been available and worked just fine on my 64-bit laptop running 64-bit Intrepid.

---

### Post by rbmorse on 2009-02-15
Can't speak for the OP, but I've got a proprietary hardware driver (scanner) that is only available in 32-bit form. Running 32-bit Ubuntu is preferable to dual-booting with XP just to be able to use the scanner.

---

### Post by jofre on 2009-02-15
The main difference between a 32bit system and a 64bit is the amount of RAM memory that the operating system can address: 4GB for 32bits and 8GB for 64Bits. 

So unless you are working with huge data files (and you have more than 4GB installed in you machine) the difference is going to be tiny.

With this said, there is absolutely no harm at all installing a 64bit and it would be "cooler" and a tiny bit faster. Intrepid 64bits is problem free for standard things.

I know people that perform molecular dynamic simulations that used very specialized commercial libraries that are compiled only for 32bit (not open source) so they are stuck with 32bits, but I doubt is it going to be your case ;-)

Jofre

---

### Post by Peter_G on 2009-02-15
> **jofre said:**
> 
 but I doubt is it going to be your case ;-)

Jofre

This is exactly my case you insensitive clod! :P

---

### Post by JimBuntu on 2009-02-15
I have a 64bit system with 32bit installed and everything is working fine. I'm having more problems with my laptop which has 64bit installed on it.

---

### Post by chez17 on 2009-02-15
Just to clear up some confusion, I use the 64 bit flash plugin and it works perfectly. Do NOT install it from the repos, just download it from the adobe page and put it in the folder /home/yourname/.mozilla/plugins, you may have to create the 'plugins' folder if it doesn't exist. After that just restart FF and enjoy.

---

### Post by fragos on 2009-02-15
In considering performance I like to place evaluate it from a user experience perspective. Some performance gains are measurable but not perceivable. IMHO which is the case when comparing 32bit vs 64bit performance. Putting aside the 4GB memory limit with 32bit the question for me is will everything work properly in 64bit. The answer was no but that's becoming less of an issue. My advice to anyone more interested in use than the OS itself is to run 32bit. Everything will work without having to learn Linux internals. You won't have 64bit bragging rights but you will have a usable system. I've been a system software engineer since 1964 and take no shame in running 32bit Linux on my 64bit hardware.

---

### Post by jwbrase on 2009-02-15
> **jofre said:**
> The main difference between a 32bit system and a 64bit is the amount of RAM memory that the operating system can address: 4GB for 32bits and 8GB for 64Bits. 

No, it goes up exponentially. It doubles with every bit you add. 32 bit can address 4 GB, 33 bit, if anybody actually designed 33 bit computers, could address 8 GB, 34 bit could address 16 GB. 

64 bit can address about 17 *billion* gigabytes.

---

### Post by fragos on 2009-02-15
The largest increase from additional memory comes as we negate the need to access swap space on disk. We all have different application mixes so that point may vary. My desktop system virtually stopped using swap space when I got to 1GB. Servers may run many more concurrent jobs than a desktop so their memory requirements will be larger. Not being a gamer I'm not sure what their memory requirements are. My mix which includes image and video editing fits nicely in the 1GB I have. You can easily check your use of swap space with the System Monitor or running "free" on the command line.

---

