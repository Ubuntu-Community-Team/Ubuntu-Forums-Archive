---
title: "RAM Issue"
date: 2007-08-02
forum: Dell  Ubuntu Support
---

### Post by Hybrid86 on 2007-08-02
I have a dell inspiron 8600; originally with 512mb or ram. After getting fed up with how slow my machine was, I upgraded to the maximum 2GB the machine could hold. However, it is still running as fast as it did with 512mb. Ubuntu takes the same amount of time to start up, programs take the same amount of time to get going, etc. It's like I still have 512mb :confused:

The system monitor thing says I have 2GB, so I'm not sure what's going on. Is there some terminal command I'm supposed to run after I install ram?

My new RAM's specs: Kingston 1024MB PC2700 DDR 333MHz SODIMM
(yes, this is what was recommended)

---

### Post by Rocket2DMn on 2007-08-02
Speed is not a direct correlation to the amount of RAM you have.  RAM bus speed, hard drive read/write speed, and processor speed all contribute.  Hard drives are extremely slow compared to everything else in the system, so using older hard drives can decrease your performance when loading programs or interacting with data stored on your hard drive in any way.  333mhz is not very fast RAM, if possible, you would want at least 667 or 800, but it depends on your motherboard as well.
Increasing RAM only tends to help if you multitask and overrun your previous amount of RAM and end up using a lot of SWAP space (hard drive partition used as RAM).  There is no terminal command to run.
There are methods for increasing boot speed, just search around google and the forums and you will find some tips and tricks.  However, you are still limited by your hardware.

---

### Post by rombel4u on 2007-08-02
I have inspiron 8600 as well, what i did was change my 4200 rpm hard drive that come with the system to a 7200 rpm (pata of course) from segate and i have seen improvement so you could change your hard drive and see what happen.

---

### Post by smithno on 2007-08-03
I ran Kubuntu on an old Averatec 3255 with 512MB RAM for several months before I got my 1420N w/2GB. According to the system monitor, Linux took a little over 200MB RAM with nothing running. With 2-3 browser windows open and watching a YouTube video, it would run about 450MB. Very rarely did I ever manage to run enough stuff to make it swap. I'm finding roughly the same thing with the 1420N. I can get it to use more than 512MB of memory when running running NetBeans and several other things, but Linux is so memory efficient that unless you are running a memory intensive application, RAM will rarely be an issue for a desktop system.

---

