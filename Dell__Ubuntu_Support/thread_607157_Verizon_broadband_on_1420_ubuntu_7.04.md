---
title: "Verizon broadband on 1420 ubuntu 7.04"
date: 2007-11-08
forum: Dell  Ubuntu Support
---

### Post by RobertGloverJr on 2007-11-08
I would like to go to my local Verizon wireless store and buy a Broadband card to use with my Dell Inspiron 1420 that came pre-loaded with Ubuntu 7.04.

   However, Verizon  sells many different kinds of broadband cards (see:  [http://b2b.vzw.com/productsservices/wirelessinternet/](http://b2b.vzw.com/productsservices/wirelessinternet/)  and more especaill:  [http://b2b.vzw.com/broadband/bbapccard.html](http://b2b.vzw.com/broadband/bbapccard.html)).

     The last link says:

Verizon Wireless offers the three most commonly used interface types for the BroadbandAccess service:
• Standard Type II card slot
   Typically found on most Windows notebooks
• ExpressCard/34 card slot
   Found on some newer Windows and Mac notebooks
• Universal Serial Bus (USB)
   Found on most computers today

    I don't know which is the best to buy for the Dell laptop running ubuntu 7.04.

    Advice/anecdotes/war stories  appreciated greatly....:confused:

---

### Post by groovete on 2007-11-08
:confused: Your  notebook comes with a build in wireless card and a 10/100 network card - so why buying additional stuff???

---

### Post by RobertGloverJr on 2007-11-09
You make a good point.  However, I am considering it for business reasons.  As a consultant I use a desktop computer at the site I consult at, and it's connected to the internet.  But I am not permitted to connect my Dell Inspiron 1420 to the corporate network and hence have no internet connectivity wireless or otherwise thru the laptop.  However if I had a Verizon Broadband card I could connect to the internet while consulting on site at a company on my own without needing any help (which they will not provide) from the corporate network.

---

### Post by greatbuckets on 2007-11-09
I have a 1420, and that does not have a "Standard Type II card slot", it has the "ExpressCard/34 card slot".

Oh, and USB too, of course.

Can't advise on which would work though.

---

### Post by dacap06 on 2007-11-09
Is there something that prevents you from taking your 1420 laptop to the Verizon store and trying them out to see which (if any) works?

---

### Post by RobertGloverJr on 2007-11-09
> **greatbuckets said:**
> I have a 1420, and that does not have a "Standard Type II card slot", it has the "ExpressCard/34 card slot".

Oh, and USB too, of course.

Can't advise on which would work though.

     Oddly, the order for my 1420 does not say which of those two I have, or at least I don't see it.  Can anyone tell from the order info below whether I have "Standard Type II card slot" or else "ExpressCard/34"?

223-1345 Inspiron 1420, Intel Core 2 Duo T7500, 2.2GHz, 800Mhz, 4M L2 Cache	$1578.00
320-5524 Basic Black Matte LCD back color	$0.00
311-7255 2GB, DDR2, 667MHz 2 Dimm	$0.00
320-5521 High Resolution, glossy widescreen 14.1 inch display (1440x900)	$0.00
320-5495 Intel Integrated Graphics Media Accelerator 3100 Inspiron 1420	$0.00
341-4866 160G 7200RPM SATA Hard Drive	$0.00
420-7153 Ubuntu Edition version 7.04	$0.00
430-0493 Integrated 10/100 Network Cardand Modem, for Inspiron	$0.00
313-5277 8X DVD+/-RW Dual Layer Drive for Inspiron	$0.00
313-4783 Integrated High Definition Audio 2.0	$0.00
430-2334 Intel 3945 WLAN (802.11a/g) Mini Card	$0.00
320-5523 No Camera	$0.00
312-0540 85 WHr 9-cell Lithium Ion Primary Battery, for Inspiron 1420	$0.00
310-9348	Intel Centrino Core Duo Processor	$0.00

---

### Post by RobertGloverJr on 2007-11-09
> **dacap06 said:**
> Is there something that prevents you from taking your 1420 laptop to the Verizon store and trying them out to see which (if any) works?

    That's a provocative question.  It's true I could take the 1420 laptop to the Verizon Store on my lunch hour.  The reason I did not realistically consider that is because there is not one chance in ten million that anyone in the Verizon store will have any experience with Linux.  They will undoubtedly tell me that they only can help me with Windows related questions and then walk away to help a more easily served customer.

   Surely there is someone on this forum who is using Verizon Broadband on a Dell 1420 and can share their experiences and advice?

---

### Post by dacap06 on 2007-11-09
Robert,

So the question at hand is whether or not either Verizon's Expresscard/34 broadband card or its USB broadband device will work with Ubuntu 7.04.  I still say the simplest thing to do is take your laptop with you and try it, even though the Verizon tech is likely to be as clueless as you expect.  It should not be hard to talk a tech into shoving the card into a slot and seeing what happens.  You could get lucky and everything could already be set up for you.  

If you are not so lucky and it does not work out of the box, you will have to find a driver and install it (assuming you can find it).  The place to start is with Tina Gasperson's most excellent article on the Verizon Broadband card:  [http://www.linux.com/articles/52729](http://www.linux.com/articles/52729).

Regards,

DaCAP

---

### Post by nooblot on 2007-11-10
can you share your experience so far about the 1420 in [this thread]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=607345"), I'm lookong to get one as well

thanks

---

### Post by greatbuckets on 2007-11-11
> **RobertGloverJr said:**
> Oddly, the order for my 1420 does not say which of those two I have, or at least I don't see it.  Can anyone tell from the order info below whether I have "Standard Type II card slot" or else "ExpressCard/34"?

223-1345 Inspiron 1420, Intel Core 2 Duo T7500, 2.2GHz, 800Mhz, 4M L2 Cache	$1578.00
320-5524 Basic Black Matte LCD back color	$0.00
311-7255 2GB, DDR2, 667MHz 2 Dimm	$0.00
320-5521 High Resolution, glossy widescreen 14.1 inch display (1440x900)	$0.00
320-5495 Intel Integrated Graphics Media Accelerator 3100 Inspiron 1420	$0.00
341-4866 160G 7200RPM SATA Hard Drive	$0.00
420-7153 Ubuntu Edition version 7.04	$0.00
430-0493 Integrated 10/100 Network Cardand Modem, for Inspiron	$0.00
313-5277 8X DVD+/-RW Dual Layer Drive for Inspiron	$0.00
313-4783 Integrated High Definition Audio 2.0	$0.00
430-2334 Intel 3945 WLAN (802.11a/g) Mini Card	$0.00
320-5523 No Camera	$0.00
312-0540 85 WHr 9-cell Lithium Ion Primary Battery, for Inspiron 1420	$0.00
310-9348	Intel Centrino Core Duo Processor	$0.00

My order for a 1420 didn't mention that it was an express card slot.

---

