---
title: "Ubuntu on Dell Inspiron Mini 12"
date: 2010-02-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kixtosh on 2010-02-21
Dell is currently offering special pricing on the discontinued Mini 12. It is shipping with Windows XP (not "Dellbuntu" 8.04). With the standard 40GB hard drive and Intel Atom Z520 1.33GHz processor, the price is about $300, with $12 shipping (tax and California recycling fee are extra). A 60GB hard drive adds $25, and the Z530 1.60GHz upgrade adds $50. RAM is 1GB and cannot be increased, AFIK.
 
Anyway, would this be a good candidate for something like Ubuntu, Xubuntu or Edubuntu Lucid Lynx 10.4, or am I totally barking up the wrong tree here?
 
[http://www.dell.com/content/products/productdetails.aspx/laptop-inspiron-12?c=us&cs=19&l=en&s=corp&~lt=popup](http://www.dell.com/content/products/productdetails.aspx/laptop-inspiron-12?c=us&cs=19&l=en&s=corp&~lt=popup)
 
In my case, if I get it, I only intend to upgrade the hard drive, since upgrading the CPU too would push the whole deal over the $400 mark, which seems like a silly choice when compared to some of the other choices out there, such as the new Inspiron 11z (not being called a "mini" by Dell any more), with a better processor, better keyboard, and much better hard drive.

---

### Post by keep you kimi on 2010-02-22
Nice, 12" screen is surely better than the 10 inch one.
all *buntus are running fine on Atom (not very fast compared to Core2, but ok), the case here might be the graphics (gma500), you should search the forum for that. 

I'd skip the factory upgrades and buy a new harddrive and RAM myself, they are easy to install and for 25$ I think you can buy more than 60G (like 120-160?)

---

### Post by mikewhatever on 2010-02-22
No, in fact Dell mini 10/12 are both bad candidates. Intel has been refusing to officially support their gma500 chips since 2008, so that buying it would be like traveling to terra incognita. You can easily find more info about the problem by googling or searching these forums for gma500 or poulsbo.

---

### Post by snowpine on 2010-02-22
The Mini 9 and Mini 10v cost less (I got my 9 for about $200) and have a 100% Linux-compatible graphics card (GMA 945).

---

### Post by Kixtosh on 2010-02-22
> **keep you kimi said:**
> ... I'd skip the factory upgrades and buy a new harddrive and RAM myself, they are easy to install and for 25$ I think you can buy more than 60G (like 120-160?)This is what I thought too, but it seems the wierd PATA drive being used (not SATA) makes it more difficult to upgrade. 
 
As for the RAM, I think the system will not support more than 1G, so Dell is not offering that upgrade AFIK. There isn't even an opening on the base of the machine to access the slot. If it can be upgraded to 2G, after purchase (not by Dell), that would certainly be a welcome improvement.
 
The processor was the upgrade I was wondering the most about. ***Is it worth $50 to go from the 1.33GHz default to the 1.60GHz upgrade?***
 
> **mikewhatever said:**
> No, in fact Dell mini 10/12 are both bad candidates. Intel has been refusing to officially support their gma500 chips since 2008, so that buying it would be like traveling to terra incognita. You can easily find more info about the problem by googling or searching these forums for gma500 or poulsbo.Yes, I've read some of those posts, but it's hard for a novice like myself to read between the lines in such a vast forum as this and figure out the difference between either a real problem without any proper solution or an install that just needs some tweaking to get it to work! Travelling to *terra incognita* sounds like a very bad idea, however, precisely because I am a novice! 
 
Also, shame on Intel. Is this just because they don't want Dell to sell cheaper netbooks with cheaper processors that they go to such extremes to poke Dell in the eye and say they won't support the video chip either ... is this the real reason why the Mini 12 was replaced by the 11z?! If so, then straight to the eternal torments of hell fire and damnation with you, Intel!
 
> **snowpine said:**
> The Mini 9 and Mini 10v cost less (I got my 9 for about $200) and have a 100% Linux-compatible graphics card (GMA 945). 
> **keep you kimi said:**
> Nice, 12" screen is surely better than the 10 inch one. ...I excluded the Mini 9 and Mini 10 versions from my choices since I used to use a 9" Toshiba Portégé, in 1998, (and have since used 11" and 12" versions). I just found the 9" too small, especially the keyboard, and wasn't really prepared to go back to that ... For the intended use, 12" seems like a good compromise, hence my interest in this heavily discounted Mini 12. It's not worth it's original price IMO, especially if it's only really fully compatible with a Windows O.S., because of all the shortcomings already mentioned.
 
The other options currently available for me would be a refurbished 12-14" Lenovo or Dell, for about $300, or a new Celeron based 14" Acer for $350-400. These would all be more versatile and much easier to upgrade, but the inconvenience of everything from their actual weight to their full size power bricks and cords make me hesitate, especially since any of these may have their own Ubuntu compatability issues.

---

### Post by snowpine on 2010-02-22
> **Kixtosh said:**
> Yes, I've read some of those posts, but it's hard for a novice like myself to read between the lines in such a vast forum as this and figure out the difference between either a real problem without any proper solution or an install that just needs some tweaking to get it to work! Travelling to *terra incognita* sounds like a very bad idea, however, precisely because I am a novice! 
 
Also, shame on Intel. Is this just because they don't want Dell to sell cheaper netbooks with cheaper processors that they go to such extremes to poke Dell in the eye and say they won't support the video chip either ... is this the real reason why the Mini 12 was replaced by the 11z?! If so, then straight to the eternal torments of hell fire and damnation with you, Intel!

GMA500 wasn't actually developed by Intel; it is re-branded. I doubt Intel will be repeating that debacle any time soon after all the bad P.R.

A pretty good summary of the situation on wikipedia: [http://en.wikipedia.org/wiki/Poulsbo_(chipset)](http://en.wikipedia.org/wiki/Poulsbo_(chipset))

I do not have personal experience with Poulsbo, as I have deliberately avoided it (based on comments here on Ubuntu Forums and mydellmini.com). The new Intel Atom/Nvidia Ion chipset looks like the better choice for Linux IMHO. And of course there will be something even better coming along after that.

---

### Post by Kixtosh on 2010-02-22
> **snowpine said:**
> ... A pretty good summary of the situation on wikipedia: [http://en.wikipedia.org/wiki/Poulsbo_(chipset](http://en.wikipedia.org/wiki/Poulsbo_(chipset)) ...I had a problem with that link, but this one should work: [http://en.wikipedia.org/wiki/Poulsbo_(chipset)](http://en.wikipedia.org/wiki/Poulsbo_(chipset))
 
Not looking entirely hopeful for a Mini 12 purchase at this point ...

---

### Post by mikewhatever on 2010-02-22
> **snowpine said:**
> .......

I do not have personal experience with Poulsbo, as I have deliberately avoided it (based on comments here on Ubuntu Forums and mydellmini.com). The new Intel Atom/Nvidia Ion chipset looks like the better choice for Linux IMHO. And of course there will be something even better coming along after that.

+1 fot Ion. Nvidia has been quite active on the Linux front in recent years.

Intel's refusal to support its hardware is simply outrageous. Here is a good summary of the current situation.

[http://arstechnica.com/open-source/news/2009/12/poulsbo-mess-casts-a-shadow-on-intels-moblin-project.ars](http://arstechnica.com/open-source/news/2009/12/poulsbo-mess-casts-a-shadow-on-intels-moblin-project.ars)

> The real question at this point is whether Intel plans to take steps to address the issues with the Poulsbo driver or ensure that future products are better supported. When we put this question to Intel, they acknowledged that their GMA500 hardware is poorly supported on Linux, but they denied that they have a responsibility to make it work.

---

