---
title: "i386 install of Ubuntu 8.10 on amd 64? Problems!"
date: 2009-02-11
forum: General Help
---

### Post by Dieseler on 2009-02-11
I heard it was possible to do this but after install I am getting white screen and lock ups at login?
Any suggestions?
Maybe some hardware just won't allow a i386 install over 64 bit?

---

### Post by 7mkgw7q on 2009-02-11
Not an answer to your question, but I am running i386 on my 64 bit just fine. Possibly a hardware issue? Or corrupt image?

---

### Post by Dieseler on 2009-02-11
I'm not sure man, I'm assuming it must be a problem along lines of my hardware as many are saying they run it fine.
Disk checked out valid.
I'm pretty much locked out of that system until I finish dl'in and burning the 8.10 64 bit cd.
When I get it I reckon I will know if maybe its something else.
I can't think of any bios setting it could be, I'm no expert there though.
Ahh, and I have never tried this before either.
64 bit has run on this machine well.

---

### Post by 7mkgw7q on 2009-02-11
Keep us updated. If you still have the problem when you get 64 bit loaded, we can take it from there. Your particular system may just need to use 64 bit.

---

### Post by Dieseler on 2009-02-11
> **7mkgw7q said:**
> Keep us updated. If you still have the problem when you get 64 bit loaded, we can take it from there. Your particular system may just need to use 64 bit.

I believe that will be the case, 
will do.

---

### Post by LowSky on 2009-02-11
An AMD64 processor will run a 32bit Operating System just fine. I have 2 computers Right now that both have AMD processors, an AMD Athlon64 San Diego @2.2Ghz, and AMD Phenom X4 @2.5Ghz

Your issue seems to be graphics related. which is possibly an easy fix. Please give us more information about your computers specificaitons.

First you should try to boot into recovery mode from GRUB and choose XFIX and follow the instructions.

---

### Post by Dieseler on 2009-02-11
> **LowSky said:**
> An AMD64 processor will run a 32bit Operating System just fine. I have 2 computers Right now that both have AMD processors, an AMD Athlon64 San Diego @2.2Ghz, and AMD Phenom X4 @2.5Ghz

Your issue seems to be graphics related. which is possibly an easy fix. Please give us more information about your computers specificaitons.

First you should try to boot into recovery mode from GRUB and choose XFIX and follow the instructions.


Hey, Thanks!
I'm not a total newby but that is a little over my head,
can you give me a little how to.
My /boot partition is sda1 (hd0,0)
and my / partition is sda7 (hdo,6)

---

### Post by joey-elijah on 2009-02-11
i can't imagine any processor only being able to handle x64 and not x86.

As mentioned above it sounds like more common problems than an prejudiced CPU.

---

### Post by Dieseler on 2009-02-11
> **LowSky said:**
> An AMD64 processor will run a 32bit Operating System just fine. I have 2 computers Right now that both have AMD processors, an AMD Athlon64 San Diego @2.2Ghz, and AMD Phenom X4 @2.5Ghz

Your issue seems to be graphics related. which is possibly an easy fix. Please give us more information about your computers specificaitons.

First you should try to boot into recovery mode from GRUB and choose XFIX and follow the instructions.

I had to run xfix from recovery 3 times but it eventually got me in to the system. I'm gonna muck around a little with themes and such, then I will reboot to be sure it continuesto work.

Lol, now I have no mouse...

---

### Post by fragos on 2009-02-11
i386 is for Intel 486 processors. You want generic which is 32 bit and runs on both 32 and 64 bit system.

---

### Post by Dieseler on 2009-02-11
On this page [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)  
I only get the option for live cd, no alternate.
So I went to this page [http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/)
and downloaded this [http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-i386.iso](http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-i386.iso)

I don't see any generic option anywhere.
Do you have a link to an install disk of generic 8.10?

---

### Post by Dieseler on 2009-02-11
The install I used says this about itself

PC(intel x86)alternate install CD
For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure.

I see now, that when I use that link decribed above that I am downloading ubntu-8.10-aternate-i386.iso.....
Hmmm.

Anyway, after rebooting I have the initial problem of whitescreen.
The mouse was there, last time when I was able to log in, but was moving really slow.
I couldn't get to a terminal either.
Had to cold reboot.

---

### Post by Slim Odds on 2009-02-11
> **fragos said:**
> i386 is for Intel 486 processors. You want generic which is 32 bit and runs on both 32 and 64 bit system.

Any x86 based processor (32 bit or 64 bit, this would include almost all desktop and laptop CPUS) can handle the i386 kernel (is uses 80386 instructions that are actually optimized for the 80486).

---

### Post by Dieseler on 2009-02-11
Bah, who cares. I was trying to get away from the 64bit stigma but apparently its not happening.
I'm burning the 64 bit now.
File it under unsolved mysteries.

I will post whatever specs anyone might ask here but I doubt I will revisit the i386 install again.
Let me know if there is any interest.

---

### Post by fragos on 2009-02-11
Download from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download). The 32 bit version you get there should work. It's the generic that runs on everything including multi-processor cores.

---

### Post by Dieseler on 2009-02-11
> **fragos said:**
> Download from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download). The 32 bit version you get there should work. It's the generic that runs on everything including multi-processor cores.

I was hoping to avoid a live cd.
Can't seem to ever get them to work period.

---

### Post by Slim Odds on 2009-02-11
> **Dieseler said:**
> I was hoping to avoid a live cd.
Can't seem to ever get them to work period.

You don't **have** do use a Live CD. You can use the alternate CD with a text based install.

---

### Post by Yellow Pasque on 2009-02-11
> I was trying to get away from the 64bit stigma
What stigma? Why would you want to run x86 when x86-64 works fine for you as you seem to indicate it does?

---

