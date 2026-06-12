---
title: "Can anyone tell me which Ubuntu is best for my system?"
date: 2009-11-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Maghdalena on 2009-11-23
Can anyone tell me which Ubuntu is best for my system?
Hi all,
I have a Dell Dimension 2350 that I got in 2003 and I’m planning to upgrade some things in it this holiday season Right now, I have:
256 MB of Memory(I plan to upgrade to 1 GB, the max my motherboard will take)
CPU Processor: Intel Pentium 4, 1800 MHz (I guess this is 1.80)
Chipset: North Bridge: Intel Brookdale-G i845G
60 GB EIDE Hard Drive (Western Digital to be upgraded to 500 GB) I’m also planning on getting a PCI Control Board so it can see all 500 GB) 
LITEON DVD-ROM LTD163  (16x/48x DVD-ROM)
(To be upgraded to a PATA DVD Burner
NEC CD-RW NR-9100A  (40x/10x/40x CD-RW)(Not planning to upgrade this)

Speakers(Not sure of the brand) They’ve died. Planning to upgrade hopefully to Creative Labs T-10 Speakers
Video Adapter Intel(R) 82845G/GL/GE/PE/GV Graphics Controller (64 MB) Not planning to upgrade at this time
3D Accelerator Intel Extreme Graphics
Windows XP Home Edition SP3(Planning to upgrade to Windows XP Professional
DirectX 4.09.00.0904 (DirectX 9.0c)
CPU Fan(Mine Died, so has to be replaced(I’m not sure of the brand yet)


What I need to know is that I’m planning on Dual-Booting with Windows XP Professional on my I have several versions of Ubuntu(6.10—Edgy Eft, 7.04(Feisty Fawn—for both Ubuntu and Kubuntu, Ubuntu 7.10(Gutsy Gibbons), Ubuntu and Kubuntu 8.04(Hardy Heron) and Kubuntu 9.04(Jaunty Jackalope, which I really like), which of these would install with the least amount of pain, and work best and be most compatible with my system? I would prefer either Gnome or KDE, I’m pretty flexible. I like KDE, but the books I have for Ubuntu which is Gnome. As I said, I’m pretty flexible.
So can anyone help me?
Any help would be deeply appreciated.
Sincerely yours,
Katherine Logan
Maghdalena

---

### Post by mikewhatever on 2009-11-24
I'd go with Ubuntu/Gnome 8.04, a long term support release, supported till June 2011. That said, any of the releases you mentioned should be compatible with that computer, however, 6.10, 7.04, 7.10 and 8.04 KDE are no longer supported, which means, there are no updates and repositories. Jaunty is a solid release, but has serious unfixable regressions  with Intel's graphics, which means it might not work well. You can try running it from the cd to verify that.

---

### Post by coffeeaddict22 on 2009-11-26
I'd have a look at the latest version, as the Intel graphics issue is now fixed.  The caveat is that you'd be best to upgrade your memory first; 256 MB is the minimum requirement (it has been at least back to 8.04), so you're going to have a less than exciting experience without a bit more memory.

---

### Post by Maghdalena on 2009-11-27
> **coffeeaddict22 said:**
> I'd have a look at the latest version, as the Intel graphics issue is now fixed.  The caveat is that you'd be best to upgrade your memory first; 256 MB is the minimum requirement (it has been at least back to 8.04), so you're going to have a less than exciting experience without a bit more memory.

Thanks so much for all  your helpful advice, both of you. I was planning to upgrade my memory anyway this holiday season to one GB, the max my motherboard can handle.  I need to upgrade to a DVD burner anyway, because when I tried the live CD of some of the older Ubuntus, it was just a black screen, it started out all right, but when it was loaded in, something went south. Long Story short, I tried a Knoppix live CD and it said the disc and the Drive were not synced, so it's the drive, I'm maxing out on the upgrades, as it's the holidays, and a larger hard drive. I'm running out of space on this one(I have a 60 GB HD right now. Again, thanks for all the help.  This is a great community!

---

### Post by Zoot7 on 2009-11-27
I'd say go for either 8.04 or 9.10. 9.10 if you want the latest apps etc. and 8.04 if you want rock solid stability. :)

---

### Post by RedRat on 2009-11-27
Very definitely add memory, at least 1Gb. Your experience will be good. As to the distro, I would suggest 8.04 since it is stable and will be supported for another year and half. If you find that the graphics card is giving you grief, you might want to try an NVidia card, some of the later versions have come down in price in the last year or so. 

However, if you expect to play in multimedia, particularly video, you might want to consider moving up to 9.04 or 9.10 since there is better support for HD video. You can do HD in 8.04 but there is a lack of support for the popular video editing software that installs in 8.04. 

In the end, if you are new to Linux/Ubuntu, I think you would be best off with 8.04 LTS.

---

### Post by Maghdalena on 2009-11-28
> **RedRat said:**
> Very definitely add memory, at least 1Gb. Your experience will be good. As to the distro, I would suggest 8.04 since it is stable and will be supported for another year and half. If you find that the graphics card is giving you grief, you might want to try an NVidia card, some of the later versions have come down in price in the last year or so. 

However, if you expect to play in multimedia, particularly video, you might want to consider moving up to 9.04 or 9.10 since there is better support for HD video. You can do HD in 8.04 but there is a lack of support for the popular video editing software that installs in 8.04. 

In the end, if you are new to Linux/Ubuntu, I think you would be best off with 8.04 LTS.

Thanks. I'll take that under advisement. I checked out the prices on the Nvidia cards, and some are out of our price range; is that the whole card that is manufactured by Nvidia or just the chipset or what. I'm totally new to Video cards--total newbie here. :)  I'd prefer to spend less than 100 dollars. I don't really play video games on the computer. I'd play  movies, though. Any suggestions as to brands that you find to be good like that GeForce?

---

### Post by cascade9 on 2009-11-28
> **Maghdalena said:**
> Thanks. I'll take that under advisement. I checked out the prices on the Nvidia cards, and some are out of our price range; is that the whole card that is manufactured by Nvidia or just the chipset or what. I'm totally new to Video cards--total newbie here. :)  I'd prefer to spend less than 100 dollars. I don't really play video games on the computer. I'd play  movies, though. Any suggestions as to brands that you find to be good like that GeForce?

GeForce is just the range of 'consumer' level video cards nVidia makes (theres also nVidia Quadro cards, but they are made more for 3D workstations, not for desktop use). nVidia just makes the actual GPU. The RAM on the card will be made by somebody else, and somebody else has put the thing together. 

BTW, the Dell Dimension 2350 has ONLY PCI slots. Not even an AGP. Almost all the cards you will have seen would be PCI-E (the most common today). PCI nVidia 8400GS cards are about $40, in the US. I doubt you'll find cheaper prices in any other country, and most are more expensive.  

By the way.....I'm all for building up old machines, not throwing them away, but after looking at the specs for that Dell, I think you might do better to just buy a cheap 2nd hand machine. You will be limited to 400Mhz FSB P4s and Celerons (which are pretty slow for the rated speeds, and your limited to 2.5Ghz max), 266Mhz DDR (which is quite slow compared to dual channel DDR333/400), Dell played silly buggers with the 845GL chipset BIOS (normal 845GLs go to 2GB),no AGP (which has better upgrade potential than PCI), and if I recall correctly its a proprietary case (which means you cant put a different motherboard in there without major work...like 'drills and saws' work).

---

### Post by a!man_96 on 2009-11-28
It's better to you to find a fresh new system..
The system is too old..
;)

---

### Post by cascade9 on 2009-11-28
Too old? With more than 256MB, it would be not a problem. Even on 256MB it should run ubuntu fine, jsut not as fast as newer hardware. 

The only reason I even said that Maghdalena should get a different box is because the upgrade options for that Dell box are, well, lame.

---

### Post by RedRat on 2009-11-28
Well depending on where you live and the city your located in, finding a used computer might be problematical. But even if you upgrade the various parts you describe, I think that you are looking at $100-200 range of outlay. 

If you live near or in a geeky neighborhood or enclave, you might be able to find a pretty good used computer (sans monitor) for something in that range. You actually might strike it lucky and even get a reasonable video card too. 

Another thing to consider is finding a replacement motherboard with a newer and more powerful CPU on board. Where I live in the Seattle area, we have a number of computer stores that sell various motherboards and their prices will range from about $60 on up. The only problem here might be the power connectors to the board. The newer boards (say past 5 years or so) have moved away from the old simple plug. 

Of course all of this is dependent on what you intend to do with the computer. If you are just using it as a learning/test bed for Linux, go as cheap as you can to make it workable. Such a machine will be OK for basic web surfing and emails. However, if you intend to watch videos or even try multimedia, I think you are definitely going to need more horsepower under the hood of that computer.

---

### Post by Maghdalena on 2009-11-28
> **cascade9 said:**
> GeForce is just the range of 'consumer' level video cards nVidia makes (theres also nVidia Quadro cards, but they are made more for 3D workstations, not for desktop use). nVidia just makes the actual GPU. The RAM on the card will be made by somebody else, and somebody else has put the thing together. 

BTW, the Dell Dimension 2350 has ONLY PCI slots. Not even an AGP. Almost all the cards you will have seen would be PCI-E (the most common today). PCI nVidia 8400GS cards are about $40, in the US. I doubt you'll find cheaper prices in any other country, and most are more expensive.  

By the way.....I'm all for building up old machines, not throwing them away, but after looking at the specs for that Dell, I think you might do better to just buy a cheap 2nd hand machine. You will be limited to 400Mhz FSB P4s and Celerons (which are pretty slow for the rated speeds, and your limited to 2.5Ghz max), 266Mhz DDR (which is quite slow compared to dual channel DDR333/400), Dell played silly buggers with the 845GL chipset BIOS (normal 845GLs go to 2GB),no AGP (which has better upgrade potential than PCI), and if I recall correctly its a proprietary case (which means you cant put a different motherboard in there without major work...like 'drills and saws' work).

I had in mind upgrading, but I might consider getting a used computer. As long as it doesn't have Vista. I've heard a lot of people have been disappointed in it.  :(.  I live in Midland, MI, which isn't particularly geeky. Or getting a new system. But my husband has promised that this is the year to either buy a computer or upgrade with our Christmas bonus. The upgrades I had in mind would be around 500 or 600 bucks. And what do I do with the one I have?  There aren't any recycling centers around here and we don't have wheels.  I'm open to suggestions.  How much memory can I get for a more advanced box? I'd like to get as much memory as I can and a decent sized hard drive. I *do* like Karmic, though. It sounds good.
As for what we're using it for, we would be using it for our business/movement, and some multimedia viewing, web surfing and email, of course.  I'd like to be able to actually send email through my email clients, not receive only. I don't know why, but I've never actually been able to send out emails except through AOL or EarthLink. Now, I have cable broadband. I've been mostly using Yahoo for the bulk of our email, and then AOL as a secondary.  So, as I said, I'm open to suggestions. I want the most for my money. I don't mind not using MS Office. I'd be *nice*, but Open Office has worked really well for me, and that's with Ubuntu anyway. I still want to dual-boot with Windows, because Windows has some things I use regulary, like PrintMaster, (Informal Desktop Publishing with lots of Templates), and FrontPage.  Again, I could use some advice. Should I go with a new system or used(I could check the want ads for used systems around here.
Thanks again for all your help and advice.

---

### Post by Maghdalena on 2009-11-28
> **cascade9 said:**
> GeForce is just the range of 'consumer' level video cards nVidia makes (theres also nVidia Quadro cards, but they are made more for 3D workstations, not for desktop use). nVidia just makes the actual GPU. The RAM on the card will be made by somebody else, and somebody else has put the thing together. 

BTW, the Dell Dimension 2350 has ONLY PCI slots. Not even an AGP. Almost all the cards you will have seen would be PCI-E (the most common today). PCI nVidia 8400GS cards are about $40, in the US. I doubt you'll find cheaper prices in any other country, and most are more expensive.  

By the way.....I'm all for building up old machines, not throwing them away, but after looking at the specs for that Dell, I think you might do better to just buy a cheap 2nd hand machine. You will be limited to 400Mhz FSB P4s and Celerons (which are pretty slow for the rated speeds, and your limited to 2.5Ghz max), 266Mhz DDR (which is quite slow compared to dual channel DDR333/400), Dell played silly buggers with the 845GL chipset BIOS (normal 845GLs go to 2GB),no AGP (which has better upgrade potential than PCI), and if I recall correctly its a proprietary case (which means you cant put a different motherboard in there without major work...like 'drills and saws' work).

I took a look at the web, and I saw refurbished Dells. Are they including AGP with the newer ones, and would anyone recommend Refurbished Dells, or would you go with another brand, and if so, which ones have your vote? 
I prefer mid-towers, but I've seen some of the "slim" towers, and to be honest am a little hesitant. How do you put the DVDs in sideways and have them stay in? How easy are they. Again, any help here would be helpful.
Thanks. I sure like those high end Dells too. I assume they have Network cards, not just wireless?
Any help and advice would be deeply appreciated. 
Thanks for all your help.

---

### Post by RedRat on 2009-11-28
> **Maghdalena said:**
> I took a look at the web, and I saw refurbished Dells. Are they including AGP with the newer ones, and would anyone recommend Refurbished Dells, or would you go with another brand, and if so, which ones have your vote? 
I prefer mid-towers, but I've seen some of the "slim" towers, and to be honest am a little hesitant. How do you put the DVDs in sideways and have them stay in? How easy are they. Again, any help here would be helpful.
Thanks. I sure like those high end Dells too. I assume they have Network cards, not just wireless?
Any help and advice would be deeply appreciated. 
Thanks for all your help.
A friend of mine bought a refurbed Dell and was quite happy with it. I have two HP Pavillions running Vista (damn I hate that) and they seem to be quite reliable. I got the HPs through Fry's (this is a West Coast big box electronic retailer similar to Best Buy, but local to the West coast, I think). 

Now the thing is, they probably will come with Windows installed and if you wipe the disk and install Ubuntu, you might get some argument from Dell about the warranty on the refurbed machines. So I would dual boot, that might preserve the warranty. I think the warranty is only 90 days, might even be less. Check with Dell and see if they have any refurbed Ubuntu machines, e.g., 530n. The Ubuntu machines have an "n" after their model number. Bottom line is that a refurbed machine can be quite a good bargain.

---

### Post by Maghdalena on 2009-11-28
> **RedRat said:**
> A friend of mine bought a refurbed Dell and was quite happy with it. I have two HP Pavillions running Vista (damn I hate that) and they seem to be quite reliable. I got the HPs through Fry's (this is a West Coast big box electronic retailer similar to Best Buy, but local to the West coast, I think). 

Now the thing is, they probably will come with Windows installed and if you wipe the disk and install Ubuntu, you might get some argument from Dell about the warranty on the refurbed machines. So I would dual boot, that might preserve the warranty. I think the warranty is only 90 days, might even be less. Check with Dell and see if they have any refurbed Ubuntu machines, e.g., 530n. The Ubuntu machines have an "n" after their model number. Bottom line is that a refurbed machine can be quite a good bargain.

Thanks! :)  I was planning on Dual-booting anyway. What's your experience been with Vista. I've heard a lot of people complain about the "Blue Screen of Death." You can email me if you'd like at [email]maghdalena4@yahoo.com[/email] so we don't go off-topic, which is Ubuntu. :)
Thanks for the encouragement.

---

### Post by cascade9 on 2009-11-29
$500-600 on upgrading? o.O You can get a whole new box for that. Easy 

AMD Phenom II X2 545- $90
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103694](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103694)

Biostar TA790GX + 2GB Adata DDR2 800- $150
[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.288841](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.288841)

Coolermaster Elite 310 + 420Watt Power supply- $60
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811119210](http://www.newegg.com/Product/Product.aspx?Item=N82E16811119210)

Wester Digital 750GB 'Green Power' Hard drive- $70
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136359](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136359)

Sony 24x DVD-RW (SATA)- (currently 'holiday special, but I would guess $30-35 after that)- 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827118030](http://www.newegg.com/Product/Product.aspx?Item=N82E16827118030)

Thats $405. Still money left over for a monitor and a video card (not that you need one with that board, but its nice). 

I dont think I would actually exactly get those parts, that was just from a  quick 5 minute poke at newegg. If the idea of a new computer is  interesting for you, I can find a slightly better set of parts for similar money. 

I'm really not impressed with any of the refurbished dell, HP, compaq or any other 'corporate' boxes I've seen, and I used to work on them LOL. 

As for geting rid of the old dell box...freecycle, give it away from a newspaper add, just leave it in a poor neighbourhood, or theres here- 
[http://www.baycounty-mi.gov/EACD/RecyclingInformation.aspx](http://www.baycounty-mi.gov/EACD/RecyclingInformation.aspx)

Just as a quick aside...AGP is pretty much over. Its nicer than PCI, but all the new video cards are PCI or PCI-E. Sideways CD/DVD drive? Theres little 'ears' tat hold the CD/DVD in when you use sideways optical drives. I'm not fond of them, but they work. Vista? Steaming pike of you know what. A refurbished computer with vista will be 'early' in the cycle, and vista ran horribly at 1st and on low end hardware. Avoid.

---

### Post by Maghdalena on 2009-11-29
> **cascade9 said:**
> $500-600 on upgrading? o.O You can get a whole new box for that. Easy 

AMD Phenom II X2 545- $90
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103694](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103694)

Biostar TA790GX + 2GB Adata DDR2 800- $150
[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.288841](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.288841)

Coolermaster Elite 310 + 420Watt Power supply- $60
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811119210](http://www.newegg.com/Product/Product.aspx?Item=N82E16811119210)

Wester Digital 750GB 'Green Power' Hard drive- $70
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136359](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136359)

Sony 24x DVD-RW (SATA)- (currently 'holiday special, but I would guess $30-35 after that)- 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827118030](http://www.newegg.com/Product/Product.aspx?Item=N82E16827118030)

Thats $405. Still money left over for a monitor and a video card (not that you need one with that board, but its nice). 

I dont think I would actually exactly get those parts, that was just from a  quick 5 minute poke at newegg. If the idea of a new computer is  interesting for you, I can find a slightly better set of parts for similar money. 

I'm really not impressed with any of the refurbished dell, HP, compaq or any other 'corporate' boxes I've seen, and I used to work on them LOL. 

As for geting rid of the old dell box...freecycle, give it away from a newspaper add, just leave it in a poor neighbourhood, or theres here- 
[http://www.baycounty-mi.gov/EACD/RecyclingInformation.aspx](http://www.baycounty-mi.gov/EACD/RecyclingInformation.aspx)

Just as a quick aside...AGP is pretty much over. Its nicer than PCI, but all the new video cards are PCI or PCI-E. Sideways CD/DVD drive? Theres little 'ears' tat hold the CD/DVD in when you use sideways optical drives. I'm not fond of them, but they work. Vista? Steaming pike of you know what. A refurbished computer with vista will be 'early' in the cycle, and vista ran horribly at 1st and on low end hardware. Avoid.

OK, now we're talking about building a system. I'd like to, but right now, in our house, there is absolutely no room to. It does help to know one's options though. :) Right now, I'm considering all my options, though I'm leaning towards either getting a refurbished or a used system. I appreciate all the help I've gotten from you people. It's left me confused, but considering the pros and cons here. If I *do* upgrade, I'd get XP Professional, for the stability, so I'm really looking at Hardy for dual-booting anyway. For the stability.  I'm really considering the trade-offs here. I'm glad I asked for advice. :)
Have a great day.

---

### Post by paul7net on 2010-02-28
I personally use Ubuntu 9.10 64-bit, but I would recommend Xubuntu because it is a lot less heavy on memory.:cool:

---

