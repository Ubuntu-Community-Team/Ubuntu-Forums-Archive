---
title: "How do I install windows and get rid of Ubuntu?"
date: 2009-01-11
forum: General Help
---

### Post by Feral Rabbits on 2009-01-11
Hi, I've been using Ubuntu for about a month or two, and I do like it.  The problem is that it can't run the programs I need.

I tried to boot from a windows XP CD, which worked until the CD said I had no hard disks connected.

How I do Windows?

---

### Post by albinootje on 2009-01-11
> **Feral Rabbits said:**
> Hi, I've been using Ubuntu for about a month or two, and I do like it.  The problem is that it can't run the programs I need.

I tried to boot from a windows XP CD, which worked until the CD said I had no hard disks connected.

How I do Windows?

Why don't you try to set up a dual-boot Windows/Linux.
Or... easier... keep Ubuntu, and use Windows inside VirtualBox.

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
[http://farm4.static.flickr.com/3281/2568012677_6e6c0f8a1e.jpg](http://farm4.static.flickr.com/3281/2568012677_6e6c0f8a1e.jpg)
[http://www.youtube.com/watch?v=ch8X86R6d-g](http://www.youtube.com/watch?v=ch8X86R6d-g) (with a very old Ubuntu version)

---

### Post by Feral Rabbits on 2009-01-11
I'm trying the virtual machine.

How do you make a dual boot w/o windows being on the hard drive?

---

### Post by albinootje on 2009-01-11
> **Feral Rabbits said:**
> I'm trying the virtual machine.

How do you make a dual boot w/o windows being on the hard drive?

You can resize the Ubuntu partition, make the Ubuntu smaller, and then install MS-Windows.

Do you have enough space for that ? 
How big is the hard disk ?

I'm sure others can help you with installing Windows to a partition again. And I think I've read that Windows wants to have a primary partition for itself to boot from.

---

### Post by Feral Rabbits on 2009-01-11
65 gig HD with 60 gigs free.  Space wouldnt be the issue.

---

### Post by tact on 2009-01-11
If you booted from WinXP CD and it cannot see your HDD at all (??  is this the case?)  then there is a problem with WinXP (perhaps you have newer sata HDD and XP cannot see them unless patched?).  

Whatever it is I cannot really help with your WinXP install problem.  I just do not have a lot of experience there in recent years.  Provided the HDD is supported under XP then it should be as simple as booting the install CD and blowing away all the existing partitioning and start over clean.  

As others mentioned setting up a dual boot system (provided you have the spare disk space) or running XP in a VM would be good options if you do want to continue to use linux.

I personally have WinXP Pro installed in a VMWare VM running on my linux laptop.  I also have WinXP Pro installed in a VirtualBox VM on my Macbook.   It works fine in both - again provided you have the horsepower and HDD space.  Note: any 3D graphically intensive games/apps don't do well in a VM.

Cheers

---

### Post by albinootje on 2009-01-11
> **Feral Rabbits said:**
> 65 gig HD with 60 gigs free.  Space wouldnt be the issue.

Good.

You problem description sounds like a hard disk which is too new for the Windows XP cdrom to handle.
You probably need some extra driver or an update.

Some hardware vendors do not provide drivers for XP anymore. Few months ago I saw a Sony Vaio laptop where the XP cdrom could not find a hard disk. Turned out that Sony only supports MS-Vista on that laptop

I'm not a Windows user, and cannot help you with that.
Asking in the "Other OS" section, or a Windows forum would probably be a good idea.

---

### Post by tact on 2009-01-12
> **Feral Rabbits said:**
> 65 gig HD with 60 gigs free.  Space wouldnt be the issue.
Well you can use one of the proposed solutions...  VM 

It will depend on your needs what is the best choice:
- XP will install in a VM easily, even on that HDD that the XP boot CD cannot recognise.  This is because the VM will fake out XP ito installing onto a virtual disk that it can see.
- using a VM means you dont have to reboot just to use a windows app, and can even move files from the XP guest system to the linux host system (or reverse) easily.

Negative points for VM will be: 
- 3D graphical games etc wont run well.  
- While you can connect USB devices to the host PC and have them recognised by windows apps inside the XP VM, some things wont work well such as doing firmware updates on phones or other USB connected devices

As I think you have guessed - if the XP install CD will not recognise the HDD then a dual boot option is not going to work at all.  All you can do is google around and see how to hack/fix the XP install CD so that it can recognise your HDD.  I have seen web pages of instructions about how to get an XP install CD to recognise modern HDD's but the process is quite involved.  

In a virtual machine you would be installing to a virtual drive that the XP install CD will recognise.

Cheers

---

### Post by DeMus on 2009-01-12
> **Feral Rabbits said:**
> Hi, I've been using Ubuntu for about a month or two, and I do like it.  The problem is that it can't run the programs I need.

I tried to boot from a windows XP CD, which worked until the CD said I had no hard disks connected.

How I do Windows?

Is it possible that the Windows installation program refuses to see the Linux partitions, just as Windows itself refuses to see them?
Make for example your home directory smaller so you have some free space on your disk and use that to install Windows.

DeMus

---

### Post by oilchangeguy on 2009-01-12
> **DeMus said:**
> Is it possible that the Windows installation program refuses to see the Linux partitions, just as Windows itself refuses to see them?
Make for example your home directory smaller so you have some free space on your disk and use that to install Windows.

DeMus

this is not correct. if it were, you would not be able to install windows on a new hard drive (they come with no partitions, and not formatted). most likely, as another poster has stated, windows is not seeing a sata drive. when you install windows, you are prompted to install sata drivers.

---

### Post by DeMus on 2009-01-12
> **oilchangeguy said:**
> this is not correct. if it were, you would not be able to install windows on a new hard drive. most likely, as another poster has stated, windows is not seeing a sata drive. when you install windows, you are prompted to install sata drivers.

I have SATA drives and never had to install special drivers when installing Windows.
Only when using RAID you need a RAID driver.

DeMus

---

### Post by orlox on 2009-01-12
What programs you need to run??

Perhaps its something that can be run with wine.

---

### Post by oilchangeguy on 2009-01-12
> **DeMus said:**
> I have SATA drives and never had to install special drivers when installing Windows.
Only when using RAID you need a RAID driver.

DeMus

probably because you are using a factory restore cd. and not a windows cd.

---

### Post by diiphantom on 2009-01-12
In ubuntu, install gparted, with that resize your ubuntu partition, then have the free space UNPARTITIONED or even create a temp one as fat32. than install windows :) that should fix it.

---

### Post by Titan8990 on 2009-01-12
Guys, google....


This is a very common problem with computers the ship with pre-installed Vista. Windows XP doesn't know about the new SATA drivers so you must use a floppy + F5 in windows installation to manually load your sata drivers.

---

### Post by albinootje on 2009-01-12
> **Titan8990 said:**
> Guys, google....


This is a very common problem with computers the ship with pre-installed Vista. Windows XP doesn't know about the new SATA drivers so you must use a floppy + F5 in windows installation to manually load your sata drivers.

What if a laptop doesn't have a floppy drive ?

And in my opinion it's not so nice to tell people to use a search engine.
Apart from that, using a search engine sometimes needs certain experience and a handy way of using it to fully utilize a search engine search, and even then the results can be very frustrating.

Also talking to people (here) might be more comforting than talking to some software from an advertisement company like Google ;-)

Just my 2 euro cent coins 
(Yes, the non so shiny copper alike ones which noone really uses :) )

---

### Post by Titan8990 on 2009-01-12
> **albinootje said:**
> What if a laptop doesn't have a floppy drive ?

And in my opinion it's not so nice to tell people to use a search engine.
Apart from that, using a search engine sometimes needs certain experience and a handy way of using it to fully utilize a search engine search, and even then the results can be very frustrating.

Also talking to people (here) might be more comforting than talking to some software from an advertisement company like Google ;-)

Just my 2 euro cent coins 
(Yes, the non so shiny copper alike ones which noone really uses :) )



That is understandable. Don't have a floppy drive? Write Microsoft a letter asking them why a floppy drive is the only way to load SB drivers on their installer that they made YEARS after floppies were dead.

The OP can buy one for $6 if its that important to him.

---

### Post by fjgaude on 2009-01-12
You can always buy a USB-based floppy and use that.

---

### Post by tact on 2009-01-14
> **Titan8990 said:**
> That is understandable. Don't have a floppy drive? Write Microsoft a letter asking them why a floppy drive is the only way to load SB drivers on their installer that they made YEARS after floppies were dead.

The OP can buy one for $6 if its that important to him.

Dude use google yourself.  there are sites with instructions how to put sata drivers onto XP install disk (involves taking a disk image of the XP install disks, downloading the sata drivers, putting them onto the disk image, burning the diskimage to make a new XP installer CD that has the appropriate drivers.

Damn complicated, but no floppy needed.  hehehe

To the OP - as stated several posts back, unfortunately this is an XP problem with your hardware.  Better to ask for help in a windows forum somewhere.  (Sorry cannot help more nor even point you to appropriate forum as its all outside of my knowledge.  Its definitely not a case of ubuntu spoiling your hdd).

---

