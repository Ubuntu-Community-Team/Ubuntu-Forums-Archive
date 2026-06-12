---
title: "Storage Solutions"
date: 2009-01-05
forum: General Help
---

### Post by BRFC on 2009-01-05
Ok not sure if this is the correct place to post this but here goes anyway. 

The Freecom network HD I've been using for just over 12 months has just died (looking into data recovery but my lord its expensive) so what I need is suggestions for a reliable replacement or alternative. The IT bod at work said I should build a home server, I have no idea what this would involve or how it would work (in truth, I looked at him like a dog that had been shown a card trick) 

So what I need is some advice on what I need for reliable storage and backup, 

Requirements, must be at least 500Gb, be able to cope with being used by my dual boot Ubuntu & xp desktop and the other half's Mac Book, so come on guys and girls lets have your ideas.

Cheers

Chris

---

### Post by howefield on 2009-01-05
If money were no object I think I'd be looking at a Drobo, but at about 370 quid before you add the hard drives it isn't for me, but I do like the feature set.

I use a Western Digital MyBookWorld terrabyte NAS, for long term back up and streaming to any pc connected to the network. I find it ok, but a bit slow for large file transfer.

Also a USB 250g drive to backup the operating system images, etc, with the benefit being portability. It is a Maxtor drive and comes in about 70 pounds, although you'll probably get a higher storage for the same money since I bought mine.

---

### Post by indytim on 2009-01-05
I'd recommend just building an external H/D.  Kinda a no-brainer 
- buy the case
- buy the h/d 
- install h/d into case
- format the h/d (ext3 recommended)
- plug the critter into a usb port

I put together a 320G external about 2 yrs ago (still going strong) for ~$100 USD.  Opted to build it myself to avoid some of the junk being put into commercially available external's these days.

IndyTim

---

### Post by Claus7 on 2009-01-05
Hello,

I'll grub the word "server" that you mentioned and I'll give you my ideas based on this.

First of all if money is not a big deal to you as far as building a reliable system is concerned, then I would go for SAS disks using RAID 1 configuration.

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

[http://en.wikipedia.org/wiki/Serial_Attached_SCSI](http://en.wikipedia.org/wiki/Serial_Attached_SCSI)

With SAS disks you have what you call reliable and very fast written disks, while with RAID 1 configuration you get a very reliable storage solution. 500Gb are very expensive though (I think that you can get 450 and then 750), and if you need 500Gb then you have to buy two such disks. Of course, in order to loose your data, both of these disks should be damaged simultaneously, which is extremely rare.

Servers are mostly used in clusters where multiple computers are connected toghether. The server is the no1 computer or the one that all the others are connected to it. Something like the coordinator. Depending on the needs someone has, then someone should pay attention on the characteristics of this server.

I hope this helped,
Regards!

---

### Post by cariboo on 2009-01-05
I think what your IT guy meant when he suggested a server, was a stand alone computer that you can store your files on. My server is a computer I inhereted from a former employer. It has a 400Gb raid1 array, and 80Gb and 120Gb hard drives. You don't need a raid array for your server.

The idea of a server is that you put it somewhere out of the way and just let it run. In my case the server is in my stand alone garage and it runs with out a monitor or keybaord attached. I use ssh to access it for administration task, but other wise it just sits there serving files as I neeed them. I use grsync to backup my Ubuntu based computers.

Jim

---

