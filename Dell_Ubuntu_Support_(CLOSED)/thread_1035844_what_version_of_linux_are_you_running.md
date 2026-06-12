---
title: "what version of linux are you running?"
date: 2009-01-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by heapy on 2009-01-10
Im just wondering, what version do **you** prefer?
I have tried many distro's in my short time in the linux world and am yet to find the best combo of stability verses fetures.

All i really want is a stable platform, but my m1530 dell laptop doesn't seem to like any!!!

here is the list i have tried wivout any real success.
Ubuntu 8.10 32 gnome
Ubuntu 8.10 64 gnome
Ubuntu hardy 8.04.1 64 gnome
Ubuntu hardy 8.04.1 32 gnome
Xubuntu hardy 32 xfce
Xubuntu hardy 64 xfce
Kubuntu 8.10 64 kde 4
Kubuntu 8.04.1 64 kde 3.5
Linux Mint Elyssa 
OpenSUSE 11.1 gnome
OpenSUSE 11.0 kde 3.5
[COLOR="Red"]fedora 10, opensuse 11.0 gnome[/COLOR]

am about to burn the dell iso of ubuntu hardy 8.04.1 to see if that works out.

All of the above I have had problems with random crashing, locking up of the system with no mouse movement. The ability to dload a large file stops after about 10 mintues with the same system freeze. The ability to watch a dvd movie all the way threw. So what have you found to do the business on your dell machine??

---

### Post by compman25 on 2009-01-10
m1330 Ubuntu 8.10 64 Gnome

---

### Post by heapy on 2009-01-10
> **compman25 said:**
> m1330 Ubuntu 8.10 64 Gnome

is your system running flawless? I have had that version on for a while, and just like the others, it froze randomly on me & became so unpredictable it annoyed me! after installing from the cd, i ran the online updates and it done its stuff, changing the kernel that went fine. 
i dont know what it is, i think my laptop could be faulty as no-one seems to be having these difficulties. memtest86 ran for 13 hrs without a hitch...

---

### Post by anjilslaire on 2009-01-10
1420 with Kubuntu 8.04 i386
Mini 9 with Ubuntu 8.10 & Netbook Remix (i386)

---

### Post by RedRat on 2009-01-10
Well I am running 8.04.1 LTS the version, not the Dell version that ships with my 530n. My machine came with 7.10 from Dell but I managed to screw the machine up (all my fault being a newbie) so I just wiped out the Dell version and partitions and installed a copy of Ubuntu 7.10 that I downloaded from the Ubuntu site. Basically a vanilla Ubuntu, I then upgraded a few months after 8.04 came out and it works with no problems, other than an annoyance with the Nvidia video card drivers with kernel updates. You would think with all the brain power at Canonical that they could find some way around that annoyance--note that I say annoyance, it is not insurmountable, just a pain in the ***.

I intend to keep using 8.04LTS going for a bit, waiting for the bugs in 8.10 get worked out. I might wait until 9.10 comes out but until their is a strong reason to change, why do it?

---

### Post by compman25 on 2009-01-10
> **heapy said:**
> is your system running flawless? I have had that version on for a while, and just like the others, it froze randomly on me & became so unpredictable it annoyed me! after installing from the cd, i ran the online updates and it done its stuff, changing the kernel that went fine. 
i dont know what it is, i think my laptop could be faulty as no-one seems to be having these difficulties. memtest86 ran for 13 hrs without a hitch...

I haven't had any problems with Ubuntu and it.

---

### Post by armandh on 2009-01-10
3 running 8.10
2 running 8.04.1
1 running 7.10

nothing works on broken hardware

---

### Post by marsopia on 2009-01-12
I bought an Inspiron 1420n with ubuntu 7.10 preloaded.
I am running Ubuntu 8.10 Gnome after a succesfull update.

Mariano

---

### Post by jespdj on 2009-01-14
64-bit Ubuntu 8.04.1 on my XPS M1530, and it [works great](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530).

I've not upgraded to 8.10, because there are some specific problems with it (like the internal microphone not working correctly), and I need my computer for serious work, so stability is important to me.

*edit*: Oh, it's you, heapy. Too bad that you still didn't get Ubuntu to work properly... :(

---

### Post by heapy on 2009-01-14
heya jespdj lad,
..am still having problems yer, so thought i would ask about & see what versions other people are using on dell machines. maybe that would shed some light.

I think tbh, my laptop is faulty because i have tried everything i can think of. Windows is having a similar problem, but that bsod's with a stop error code.
 
[I][B]Contacted dell, and am explaining the symptoms!
A clock interrupt was not received on a secondary processor within the allocated time interval.
Stop Code   0x00000101[/B][/I] 

i just got a linux magazine with opensuse 11.1 on a dvd, i was going to install it but that wont help cus i have been checking my burnt ubuntu distros using checksum md5.

---

### Post by jespdj on 2009-01-15
If you also have random strange problems with Windows, then it's very likely that there's something wrong with the hardware, and Dell should have a look at it and repair it (or give you a new laptop).

---

### Post by linux_tech on 2009-01-15
Run the memtest86 at boot and check the memory. Let it run for at least an hour to see if there are any memory errors.

---

### Post by RedRat on 2009-01-15
> **heapy said:**
> heya jespdj lad,
..am still having problems yer, so thought i would ask about & see what versions other people are using on dell machines. maybe that would shed some light.

I think tbh, my laptop is faulty because i have tried everything i can think of. Windows is having a similar problem, but that bsod's with a stop error code.
 
[I][B]Contacted dell, and am explaining the symptoms!
A clock interrupt was not received on a secondary processor within the allocated time interval.
Stop Code   0x00000101[/B][/I] 

i just got a linux magazine with opensuse 11.1 on a dvd, i was going to install it but that wont help cus i have been checking my burnt ubuntu distros using checksum md5.

This looks like a hardware problem, might be in the cpu. Better contact Dell.

---

### Post by heapy on 2009-01-15
thank-you ubuntu people!
i have sorted it now lads. It was a hardware problem. I tried, and tried all kinds of distro's even windows thinking i was doing something differently from you guys. 

Turns out that the 0x00000101 stop was not to do with the dual core cpu as i first thought, but the 'media' , the graphics processor not responding.

I ran a bunch of tests whilst on the phone to a dell tech, and they confirmed the video card to be faulty. they are coming over to my place next wednesday to change the motherboard for free even tho my warranty is out of date. good result! (little tip: ask to speak with the manager)

now then, back to the original post **[COLOR="Red"]what versions of linux are you running on your dell desktop or laptop?[/COLOR]**

i for one will be using 8.04.1 hardy when my laptop is fixed :)

---

### Post by theozzlives on 2009-01-15
inspiron 1525, came with Vista... put Ubuntu on it. Runs fine with 8.10.

---

### Post by sirebral on 2009-01-16
Studio Hybrid with Ubuntu 8.10 (Gnome)
Inspiron 1510 with Ubuntu 8.10 (Gnome)
Inspiron 910 with Ubuntu 8.04 (Dell's Remix)

All work great!!

I have some issues with the Remix, but the stability helps me feel better.

---

### Post by pmthien on 2009-01-16
1310 with ubuntu 8.10 works perfect

---

### Post by heapy on 2009-01-16
> **sirebral said:**
> Studio Hybrid with Ubuntu 8.10 (Gnome)
Inspiron 1510 with Ubuntu 8.10 (Gnome)
Inspiron 910 with Ubuntu 8.04 (Dell's Remix)

All work great!!

I have some issues with the Remix, but the stability helps me feel better.

what is dell's remix? is that dells own iso dvd of hardy?

---

### Post by sirebral on 2009-01-16
> **heapy said:**
> what is dell's remix? is that dells own iso dvd of hardy?

It is the distro that came with the Mini 9.  The CD is a basic 8.04 LTS disc (says I can pass it on), but the drivers are really what make it Dell's remix.  The drivers really stabilize the OS.  On my Studio Hybrid running 8.10 I sometimes have problems with sound cutting out after viewing internet video (Mainly YouTube), but on this laptop I have noticed very little in the area of similar defects.

I thought I was going to drop the pre installed OS in favor of Xubuntu, but after playing around with it I decided I actually like it.  So far.

---

### Post by jespdj on 2009-01-16
Good that you now know that it's a hardware problem and Dell is going to fix it for you. :KS

Does the "Dell remix" version that you get with the Inspiron Mini 9 run on other Dell laptops? I'd imagine that it's specifically tailored for the Mini 9, and isn't meant to be used on other models (which have other hardware and therefore might require other drivers).

---

### Post by sirebral on 2009-01-16
Like I said.  The Ubuntu distro is a basic 8.04.01 LTS disc.  The OS is the same.

Dell added some software.  That should work.  It is a new desktop manager that really simplifies the GUI.  I don't use it.

The drivers I think are the main thing.  If DELL would release a disc of drivers specific to your Laptop and Ubuntu I think you would get the same effect.

Dell is working on fully supporting Linux.  So I am guessing that in the future the linux drivers for their hardware will be available.  Give it time and you will see the stability I speak of.

---

### Post by heapy on 2009-01-16
> **jespdj said:**
> Good that you now know that it's a hardware problem and Dell is going to fix it for you. :KS

Does the "Dell remix" version that you get with the Inspiron Mini 9 run on other Dell laptops? I'd imagine that it's specifically tailored for the Mini 9, and isn't meant to be used on other models (which have other hardware and therefore might require other drivers).

thanks m8, im glad i finally got the answers lad. was sooo frustrating not being able to run ubuntu stably. i would like to thank everyone who has put up wiv my forum posts & irc chats about random freezing problems, now i know its hardware and nothing we tried would of helped!!


...is this 'dell remix' you talk of  ? 
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

---

### Post by sirebral on 2009-01-16
Ok, let me say this again.  The ubuntu disc that came with my Mini 9 is a vanilla Ubuntu 8.04.  It even says 'pass it on' on the disc.

What is included is the drivers disc which contains the mini 9 video, wifi, mouse, and other specific to mini 9 drivers.  It also contains other software, I think.  I have to look at it but I think it also contains the DELL utilities that are made for Linux 8.04.

Whatever driver you use I am fairly certain you can install the utilities on any ubuntu distro just because the disc is vanilla.  

When you put the Vanilla Ubuntu together with the Dell Drivers and Utilities disc that equals the remix.

Understand now?

---

### Post by heapy on 2009-01-17
> **sirebral said:**
> Ok, let me say this again.  The ubuntu disc that came with my Mini 9 is a vanilla Ubuntu 8.04.  It even says 'pass it on' on the disc.

What is included is the drivers disc which contains the mini 9 video, wifi, mouse, and other specific to mini 9 drivers.  It also contains other software, I think.  I have to look at it but I think it also contains the DELL utilities that are made for Linux 8.04.

Whatever driver you use I am fairly certain you can install the utilities on any ubuntu distro just because the disc is vanilla.  

When you put the Vanilla Ubuntu together with the Dell Drivers and Utilities disc that equals the remix.

Understand now?



thankyou cerebral, im on it now lad. sounds good will give it a try

---

### Post by AlexDudko on 2009-01-17
1. Laptop - Ubuntu-8.10
2. Desktop - Fedora-9
3. Server - FreeBSD-7.0 amd-64

---

### Post by heapy on 2009-01-17
anyone tried xubuntu or arch linux?

---

### Post by Cap'n Skyler on 2009-01-17
i have a toshiba and went with the 64 bit and it was butt ugly.so not all distros will work(odd occurence by the way) on all comp.could be a iso image or it was damaged on download,no idea.i went and tried the 810 and the general 32 bit version,and everything went and worked fine except wifi,but i found the tutorial to fix that.
  i have 2 issues besides my wifi,and that is my volume seems to be less than it should be (minor issue really) and some vids are choppy.i need to investigate the codecs and see what i can change to fix it.
 i suggest trying either an older version of teh 'buntu or the 32 bit general purpose version and see how it goes.
  you *should* be able to get a distro up and running and not crashing or otherwise buggy,then work your way thru the sounds/video/wifi stuff and see what you have.if it is buggy,to me that is an issue to the distro(as happened to me)--perhaps an older(more bugs fixed and patched over it's life span) will get you all working?and if so,then as you learn that version and update,you will know how to hunt down the issues and get it all running like dynamo hum!


scott

---

### Post by anjilslaire on 2009-01-18
> **heapy said:**
> anyone tried xubuntu or arch linux?

Yes, I run Xubuntu on my desktop. Tried it on the mini, just didn't care for it. Resolution was correct, it just didn't seem to scale well to the 8.9" screen. Shame, really...

---

