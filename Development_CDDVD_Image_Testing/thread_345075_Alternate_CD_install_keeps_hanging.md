---
title: "Alternate CD install keeps hanging"
date: 2007-01-23
forum: Development CD/DVD Image Testing
---

### Post by abovett on 2007-01-23
Hope this is the right place to post this...

I'm trying to install Herd 2 using the alternate CD on a test box which has previously run Breezy, Dapper and Edgy (and still has Dapper on another partition). 

The install keeps freezing for minutes at a time - for example, when scanning for the CD, when detecting hardware, when configuring the network. The first couple of times I tried I thought it had crashed altogether. Most of the time when it hangs I just have a blank blue screen with the white (grey?) bar across the bottom. There is no activity from the hard disk or CD during these pauses. After a few minutes, it will carry on for a while as though nothing has happened, the pause again.

Almost half an hour after booting the CD, I still haven't reached the partition editor - at this rate it will take all night (kiterally) to install!

Any ideas? Should I raise this on Launchpad?

Cheers

Andy

PS - just reached the partitioner as I was about to hit "Submit"!

----- Update -----

Just logged into the BusyBox terminal in the installer and did "dmesg", and found I'm getting the following message several (around 20) times a second:
```
Intel ISA PCIC probe: not found
```
Could this be anything to do with it?

---

### Post by pochu on 2007-01-24
You should file this in Launchpad, but first search for it, because it may have already been reported.

Thanks
Pochu

---

### Post by UBfusion on 2007-01-26
Try to install on a new disk (no preexisting partitions). It should work.

All the recent daily versions I have tried (desktop + alternate) cannot (in most cases) deal with previously installed operating systems.

This is due to a combination of bugs in the installation process (you can search them in Launchpad).

---

### Post by ksglp on 2007-07-07
> **abovett said:**
> Hope this is the right place to post this...

I'm trying to install Herd 2 using the alternate CD on a test box which has previously run Breezy, Dapper and Edgy (and still has Dapper on another partition). 

The install keeps freezing for minutes at a time - for example, when scanning for the CD, when detecting hardware, when configuring the network. The first couple of times I tried I thought it had crashed altogether. Most of the time when it hangs I just have a blank blue screen with the white (grey?) bar across the bottom. There is no activity from the hard disk or CD during these pauses. After a few minutes, it will carry on for a while as though nothing has happened, the pause again.

Almost half an hour after booting the CD, I still haven't reached the partition editor - at this rate it will take all night (kiterally) to install!

Any ideas? Should I raise this on Launchpad?

Cheers

Andy

PS - just reached the partitioner as I was about to hit "Submit"!

----- Update -----

Just logged into the BusyBox terminal in the installer and did "dmesg", and found I'm getting the following message several (around 20) times a second:
```
Intel ISA PCIC probe: not found
```
Could this be anything to do with it?

this is very similar to the problem i'm having at the moment, though since it's been 2 years there might have been some progress

i'm trying to install 7.04 from a CD i have burned myself, i've checked it's integrity and checked my memory that's all fine,

the CD loads and takes me through my language, location, and keyboard settings, then does some of it's own stuff; 

detecting hardware for CD-ROM drive,
 Scanning CD-ROM, 
Loading Additional Components and 
Detecting Network Hardware, 

after that the whole thing seems to stop and i'm left with a blue screen with a grey bar at the bottom, though i can write stuff in the grey bar, i would not have a clue what to type in, i left it all night and woke up to the same screen so it's not just taking ages,

anyone know how to solve this issue?
all help is much appreciated,

thanks, 

Jordan

---

### Post by wheredidrealitygo on 2007-10-13
I'm having the same issue, bump.

celeron ~600mhz, 60megs ram, 6 gig hdd, compaq presario craptop.

i tried using ubuntu feisty alternate installer, and xubuntu fiesty alternate installer.

---

### Post by anabelle on 2008-05-31
I'm having the same issue but using the Xubuntu 8.04 alternate CD, it gets to de "Detecting Network Hardware" stays there for a few seconds, then the screen goes black, then white, and then back to "Detecting Network Hardware"

I've found several posts about the same issue but no one gives a solution. What can be done to solve this?

---

