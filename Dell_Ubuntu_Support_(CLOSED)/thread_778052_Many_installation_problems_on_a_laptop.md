---
title: "Many installation problems on a laptop"
date: 2008-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ucal on 2008-05-01
I'm sorry if this has been asked before (which I assume it has been).  And I'm sorry that I'm wasting your time with what are probably easy questions.  First the story, and a summary at the bottom, for any who don't feel like trekking through my narrative.

I've downloaded Ubuntu, and as I don't have a CD, I chose the option to have it use a virtual CD to boot from.  After rebooting and choosing Ubuntu, I get a long list of what appear to be errors in goobedlygook (ata1 drdy err or something like that), and eventually the OS loads.  The bad news doesn't end.  The wireless internet doesn't work, because I'm missing a wireless card driver I think.  That is what the message box says at least.  I try and download it, but it doesn't work (because there isn't wireless)  So I shut off, go on vista, and look up solutions. Stupidly, I didn't think to hook it up to the modem directly, but later I did, and that direct connection doesn't work either. 

Next I download the source for ndiswrapper and use an iPod to transfer it to Ubuntu, but whenever I use the install instructions that involve the terminal, I'm not even able to extract the folder because the directory doesn't exist.  I'm a terminal noob one can say.  

At one point I figured all of my problems were due to the system not being installed completely, but I can't even do that because the partitioner won't work properly.  

So the summary:
Cannot install as Partioner will not work.
Wireless internet will not work because of a missing driver (I guess)
Regular internet will not work for whatever deity you do or do not believe in knows what.
Cannot install ndiswrapper due to my own incompetence (I guess)

Cards and drivers:
Networking
Broadcom 440x 10/100 integrated controller
dell wireless 1390 WLAN mini-card
Processors
AMD Athlon 64 X2 Dual Core Processor

I'll try and provide any more info as needed.  Thanks for your help and I apologize if this is in the wrong section!

---

### Post by ucal on 2008-05-02
Bump.  Any help?  Please?

---

### Post by ucal on 2008-05-03
Is this the wrong category for this?  I chose dell because the system is a dell and I figured I could get dell specific help here.   Probably not the best reasoning though.

---

### Post by JStubbyFingers on 2008-05-03
Hi! After what probably seems like forever I may be able to get you going. Q1: Are you trying too install on the same physical disk as aforementioned Vista?
Q2: Can you mount the iso with poweriso or magiciso? 
Also, you should be able to install fwcutter and necessary firmware through the package manager once you enable the restricted repository and get the wired connection going

---

### Post by JStubbyFingers on 2008-05-03
After reading your posts again  duh, forget about the mounting question but you can create the dir like this: sudo mkdir /namehere :but that probably not the big issue.  f you can download the metapackages for fwcutter and the firmware you need and transfer them into the.  you should only ned to use ndiswrapper if the drivers aren't available through th package manager

---

### Post by JStubbyFingers on 2008-05-03
I don't have the link but you can download the Wubi installer and install the iso from within windows.  Try the install again, it sounds like the install might be corrupt.  Some of the problems (wireless disfunction) are typical with broadcom controllers

---

### Post by ucal on 2008-05-03
Okay I'm installing wubi right now. My question then becomes, can I use wubi to install ubuntu as a fully standalone operating system? Also, I've never heard of fwcutter.  What is it?

Finally, I would assume that I can get the drivers I need off of the Dell site (going by other posts in the forum) right?  Would that help with my ethernet connection though? Thanks for your help!

---

### Post by ucal on 2008-05-03
Never mind, I misunderstood what wubi does I guess.  Wubi is the same thing that came with the regular ubuntu install right?  Doesn't that decrease performance?

---

### Post by ucal on 2008-05-03
Great news!  I'm typing this in ubuntu right now!  For some reason my ethernet connection wouldn't work unless I ran it through my router (I had previously just been unplugging it from the router and running it straight to the computer, how I normally accessed the internet before I got wireless).  From there it was a simple matter to install the wireless driver.  I'll be checking on the rest of the install now.  Thanks for your help!

---

### Post by ucal on 2008-05-03
Okay, so I proceed to install ubuntu, but it fails at the Harddrive partition stage.  I resize the partition so that Vista still has some room (I would like to be able to work in that OS should I choose) but the resize operation fails, and takes me to a screen to prepare partitions.  I'm completely lost at this point.  Any help would be nice.

---

