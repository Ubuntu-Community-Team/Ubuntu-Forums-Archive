---
title: "New Tower (for ubuntu). What should i buy?"
date: 2005-12-19
forum: General Help
---

### Post by otey on 2005-12-19
I Want to buy a new computer. 

I want it to have a TV in. That is probably my only "must". 

But what i wantet to know from you guys is; what hardware gives you problems, and what should I buy?

Is there anything i should know about?

---

### Post by Beej on 2005-12-19
I'm in a similar position. I currently have a mini-itx based system, but I have decided (partly because of the lack of support for the MPEG2 decoding capabilities of the board) to build something new.

I use my current box mainly as a media centre, and it lives in my front room next to the TV. I don't have a hell of a lot of money to spend so I was thinking based around a socket Mobo and processor as the price seems right for me.

I don't have much knowledge whaen it comes to hardware so I have a few questions.

1. What graphics card should I be looking at? Nvidia or ATi. And which chipset? I don't need blinding amount of power, just enough to play dvds well and have a TV out.

2. I'm thinking of going SATA for my hard drives. I have little knowledge of this technology but many of the Mother boards I have been looking at have SATA. Any known issues in ubuntu?

3. Any advice on PVR cards? I would like eventually to run MythTV on my new box and complete my media set up.
 
Sorry for butting in on your thread otey.

Beej

---

### Post by cdhotfire on 2005-12-19
Check these out, they come preinstalled with ubuntu. :)
[http://www.system76.com/](http://www.system76.com/)
[http://opensensesolutions.com/catalog/product_info.php?products_id=43](http://opensensesolutions.com/catalog/product_info.php?products_id=43)

---

### Post by ember on 2005-12-19
Well, I can state that:

1) Nvidia works far better than ATI
2) As far as I know, SATA works without problems.
3) If you can afford, buy a soundcard with hardware mixing capabilities - it will save you possible trouble fiddling around with alsa dmix
4) The is a Howto for Win TV-PVR 150 [here]("http://www.ubuntuforums.org/showthread.php?t=91511"). You may want to get that card (it's not too expensive)
5) I can recommend you to get a large harddisk - I have 160 GB (Samsung - they are quite good and silent) and I ran out of space and had to buy an external harddisk
6) My personal recommendation: See that you invest some money in a good keyboard, mouse and monitor (possibly TFT), many people I know ignored that advice when they bought a new computer and not much fun with it afterwards.

HTH,
ember

---

### Post by Beej on 2005-12-19
Interesting links, good to see people pre-installing Ubuntu too!

I hadn't really considered buying a prebuilt system, as i have built my last couple of PCs myself, don't see why I shouldn't give it a go this time though. Does anyone know a company that does similar in the UK? 

I'm still interested to hear feedback on components, so I can compare prices etc.

Ta,

Beej

---

### Post by cdhotfire on 2005-12-19
[QUOTE=Beej]Interesting links, good to see people pre-installing Ubuntu too!

I hadn't really considered buying a prebuilt system, as i have built my last couple of PCs myself, don't see why I shouldn't give it a go this time though. Does anyone know a company that does similar in the UK? 

I'm still interested to hear feedback on components, so I can compare prices etc.

Ta,

Beej[/QUOTE]

You could always try ebay, they sell anything there. :)

---

### Post by hardbop200 on 2005-12-19
[QUOTE=ember]Well, I can state that:

1) Nvidia works far better than ATI
2) As far as I know, SATA works without problems.
3) If you can afford, buy a soundcard with hardware mixing capabilities - it will save you possible trouble fiddling around with alsa dmix
4) The is a Howto for Win TV-PVR 150 [here]("http://www.ubuntuforums.org/showthread.php?t=91511"). You may want to get that card (it's not too expensive)
5) I can recommend you to get a large harddisk - I have 160 GB (Samsung - they are quite good and silent) and I ran out of space and had to buy an external harddisk
6) My personal recommendation: See that you invest some money in a good keyboard, mouse and monitor (possibly TFT), many people I know ignored that advice when they bought a new computer and not much fun with it afterwards.

HTH,
ember[/QUOTE]

I have an ATI Radeon 9200, and I can say that it does work, but it has introduced some instability to my system (I installed the non-free driver).  I would suggest that, if your intention is to use Linux, that you buy an Nvidia card.

---

### Post by opensensesolutions on 2005-12-19
Someone mentioned my company above, Open Sense Solutions, and we're about to really expand our Ubuntu offerings.  For the past 6 months we offered one system as an "Ubuntu experiment"  That experiment has gone well, and around January 1st we are going to release our new Groovix line-up including socket 754 and 939 systems, multi-user systems, wifi, and machines that include tv tuner cards with remote control.  We have done lots of research and experimentation to find the best Linux hardware, and as always we will release full specifications so that users can "build along at home" to get an optimal configuration but still enjoy putting it together themselves and still have the option of full commercial hardware/software support if something goes wrong. 

If you just pick any old motherboard, like one with an ATI XPRESS chipset, you will be causing yourself a lot of pain.  Pretty much all of the Intel, VIA, or nvidia chipset boards work under Ubuntu, but there are small caviats to them all.

Here's what we are going to use in our next line-up: 
ASUS K8V-MX, A8V, and A8N-SLI motherboards (SLI still under experimentation)
nVidia MX4000 ...  6800GT video cards (be careful, some of the more recent cards are a big hastle under linux -- you need the absolute latest drivers, and the cards won't even work properly with a vesa or open nv driver which makes it a lot harder to use live cds, etc.)
Antec Cases and power supplies: Aria, 1650B, 2650BQE, Sonata II.  The power supply is VERY important, don't skimp on the quality of the power supply.  Wattage is not that important if the quality is good.
Audigy II creative labs sound cards (the old Live 5.1 cards were great  -- any older creative cards with a joystick/midi port will have good hardware too-- just DONT get a "live 24-bit" card)
Western Digital SATA hard drives (check out the Raptors if speed is important, or the new 16MB cache drives too)
Corsair memory (the value series is fine)
K-world (V-stream) VS-TV878RF TV tuners, (software encoding only, but very economical and includes a remote.) we are looking into a hardware encoding solution
wifi: use a netgear WGE111 external ethernet adapter for the most flexible solution.  Internally you can go with a D-LINK DWL-G520 or a netgear WG311T, but you don't have as many encryption options under linux as with the external adapter

Our goal is to get thousands of people using pretty much the same hardware, then we can perfect support for that hardware and put pressure on the hardware makers to offer a Linux support knowing that there are thousands of potential customers.  

Drop us a line if you have any questions.
Mike Pardee
[email]ubuntuforums@groovix.com[/email]
[http://opensensesolutions.com](http://opensensesolutions.com)

---

### Post by ember on 2005-12-19
Well, a bit off topic, but I have a question: Any plans on expanding to Europe? Your offerings look quite nice.

---

### Post by opensensesolutions on 2005-12-19
[QUOTE=ember]Any plans on expanding to Europe? Your offerings look quite nice.[/QUOTE]
We would love to have partners all over the world, all using the same hardware and collaborating on support and development.  If anyone has an established PC business or is thinking of starting one, we'd be more than happy to share what we've learned and work together on future development.

---

### Post by sunshine02 on 2005-12-19
I installed a Seagate 250 GB in my box, the only trouble being that it is NCQ enabled and needed to have the RAID drivers installed on the motherboard before it could be read. I had no trouble after I got the RAID drivers installed.



Intel P4 2.4 | MSI 661FM2 | MSI Radeaon 9550 | 2GB PC3200 | 450w PS |
Seagate 250 GB SATA | Maxtor 60 GB IDE | Sony DVD RW | Samsung CD RW

---

### Post by otey on 2005-12-20
Thank you for the good response everyone. :smile:

---

