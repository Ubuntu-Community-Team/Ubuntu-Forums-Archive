---
title: "Building a computer for Ubuntu"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Vinn on 2006-08-28
Hi, I was thinking of building an XPC style computer to run Ubuntu on (a cube computer basically) and to save some space. I've been looking around and there are some good barebone kits out there, but I must ask this: for Ubuntu, which processor (Intel or AMD) would work best? The online store I've been to (tigerdirect.com) has the kit I want in either AMD or Intel. Ive heard that AMD processors generate less heat which would be good for such a small case, but Ive also heard some drivers not working correctly for some processors. 

My other question is what wireless cards work in Ubuntu, for desktop computers? I have a wireless network and Ubuntu picks up the wifi card in my laptop fine and connects to the network, I'd like a wireless card in the next computer I build. Is there a list of compatable cards anywhere?

Thanks

---

### Post by DarkNemesis618 on 2006-08-28
I don't know about the wireless, but Ubuntu works fine on both my AMD and Intel Computers.  The only thing is that I would try to avoid the 64bit version, especially if you want to use flash.  I have found some programs non-functional for 64bit operations.

---

### Post by Vinn on 2006-08-29
Ok, so no 64 bit processors, got it. They can get expensive anyway.

I'll probably choose AMD if what people say about them running cooler is true, cause I don't want to pack this little case full of fans.

Still need to know about the wireless though.

> **DarkNemesis618 said:**
> I don't know about the wireless, but Ubuntu works fine on both my AMD and Intel Computers.  The only thing is that I would try to avoid the 64bit version, especially if you want to use flash.  I have found some programs non-functional for 64bit operations.

---

### Post by iTrendsNET on 2006-08-29
Vinn - A non-64-bit AMD CPU is going to run HOT, unless it is actually a mobile CPU, which is fine for use in a small box but will often cost more.  I notice the AMD CPU's at TigerDirect are 754 or 939 (better).  These are generally budget priced these days.  Both should run cooler than a comparable Intel CPU.  FYI, I am reading very good things about the newest dual core Intel CPU's as they perform excellent, run cool like AMD 64, but they will be costly at least for the short term.  

Look at the chipset on the motherboard as well as if it will run on board graphics or has a proper slot for an add on video card (again better!)  I've used SIS, nVidia, ATI and VIA chipsets with Linux and never had any problems.  But as I stated, watch out if you will be forced to use on board graphics as you may not like what you get with built in SIS or ATI graphics with Linux.  Intel on board graphics have generally worked good for me with Linux.  

Regarding wireless, my experience is the best are cards using the atheros chipset.  Ubuntu will have no problems with that type of card.  Do a search here in the forums or with Google and you will find a good list of cards that work.  Ditto for what motherboard chipsets and graphics that seem to work the best.  Watch version numbers on the card you buy as the same model wireless card may switch chipsets when the manufacturer jumps to a new revision number!

Good luck with your home built system.  I always prefer to custom build.

---

### Post by amp_man on 2006-08-29
Personally, unless you have some need for speed or plan on doing 3d modelling/gaming, I'd reccommend a Sempron processor, preferrably Socket 939 (if not, socket A, avoid 754 like the plague), and if you can, get one with 64-bit extensions. 32-bit Dapper (or windows, or any other distro/OS) will run PERFECTLY FINE on a 64-bit CPU, I run 32-bit dapper and 64-bit windows on my desktop (okay, so I don't ever use windows, but it is there), but if, in the future, you decide to go 64-bit (after flash 9 and w64codecs are released), you can't unless you have a 64-bit CPU. I have both an Athlon XP 1800+ and a Sempron 2400+, and even at the faster speed, the sempron runs a heck of a lot cooler than the athlon does. Also, semprons are great in the bang-for-your-buck category, they aren't nearly as underpowered and overpriced as the old Durons or Celerons are.

As far as your driver concerns go, I've never had trouble with anything for drivers relating to my amd cpus under linux or windows. Drivers are designed to work with a generic x86 (or x86_64) architecture, and don't differentiate between amd and intel. 

As for wireless, you can look for an atheros or a natively-supported chipset, and if you find one for a decent price, get it. OTOH, just about every popular chipset nowadays is supported by ndiswrapper, and many have native drivers either available or in the works and available as a beta. Do a little research, if it won't work or it's problematic, a google search will usually turn up half a dozen forum posts stating that on the first page. The ubuntu wiki also has a list of cards/chipsets [here](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported), however, take it with a grain of salt, not every working card will be listed on that page.

edit: also, I do most of my shopping through newegg. I was just looking through tigerdirect's wireless selection, and googling for linux support, and most of the time the first link was a newegg review. it seems like [this](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=587833&Tab=0&NoMapp=0) may be a decent card to fit your needs. And always avoid D-Link ;-)

---

### Post by jtibau on 2006-08-29
> **Vinn said:**
> Ok, so no 64 bit processors, got it. They can get expensive anyway.

I'll probably choose AMD if what people say about them running cooler is true, cause I don't want to pack this little case full of fans.

Still need to know about the wireless though.

I think what DarkNemesis618 meant was to avoid ubuntu 64bit version...
I have a Athlon 64 3200+ in my desktop. It runs dapper 32bit mainly. I've installed the 64bit version but decided against using it yet, there's a couple of stuff like flash that do work but are a bit of a hassle.

AMD 64bit CPUs are really good though even if you use them for running a 32bit OS (as most people do, I think). I'd say that even if you're budget-minded right now it would still be a good choice to pick one of those.

Haven't checked the options recently, my CPU is about a year old, and I don't have a single complain about it. Runs great.

---

### Post by Vinn on 2006-08-29
Alright, thanks a lot everybody. I'm probably going to go with a Sempron now, and thanks for the link to the wireless card. I'm curious though, what's wrong with socket 754? And integrated graphics? I know they aren't a good choice for games, but I'm not really using it for that. Is it okay if the mobo I get has intergrated graphics? I never really considered that.

Again I'm on a budget here. 


Thanks

---

### Post by cstudent on 2006-08-29
Just a note about Tiger Direct. If you're planning on trying to save some money by getting a rebate, watch out. I got burned by them one too many times. I no longer buy from them. I use Newegg.com now. And absolutely do not buy a Wintergreen system. Just Google them if you want to see how many people they've ticked off.

---

### Post by Vinn on 2006-08-29
Wintergreen? Okay I'll keep that in mind. I'm not trying to go for rebates that much either, but thanks. I'm looking through Newegg as well.

---

### Post by anthro398 on 2006-08-29
I've been comparing prices on xpc boxes, too.  I think [newegg.com]("http://newegg.com/") has better prices and their service has always been excellent.  I've used them for years and so do most of the people I know.  I really wanted an xpc with a mobile processor, but they were too expensive.  Also, Shuttle seems to have a better reputation than the other sff manufacturers. Good luck.  

I also bought a [Cobalt Qube]("http://www.prairienet.org/~jtuttle/blog/item/97/") last week.  It's old, but super cool. 
[IMG]http://www.prairienet.org/~jtuttle/images/qube.jpg[/IMG]
 Now, if I could just find a [Powerelf]("http://www.iapplianceweb.com/appreview/soho_server_19.htm")!

---

### Post by Vinn on 2006-08-29
Yeah I like Newegg better, it's easier to shop there plus they have better prices.

Nice cube, I like the color :P. I've always wanted to build a cube, and have a desktop dedicated to Linux. Why not a cube dedicated to Ubuntu? The cube cases are my favorite and ideal for where I want to put it, on my desk, and to save space (my other desktop's tower is f'ing huge).

---

### Post by iTrendsNET on 2006-08-29
> **amp_man said:**
> Personally, unless you have some need for speed or plan on doing 3d modelling/gaming, I'd reccommend a Sempron processor, preferrably Socket 939 (if not, socket A, avoid 754 like the plague), and if you can, get one with 64-bit extensions. 32-bit Dapper (or windows, or any other distro/OS) will run PERFECTLY FINE on a 64-bit CPU, I run 32-bit dapper and 64-bit windows on my desktop (okay, so I don't ever use windows, but it is there), but if, in the future, you decide to go 64-bit (after flash 9 and w64codecs are released), you can't unless you have a 64-bit CPU. I have both an Athlon XP 1800+ and a Sempron 2400+, and even at the faster speed, the sempron runs a heck of a lot cooler than the athlon does. Also, semprons are great in the bang-for-your-buck category, they aren't nearly as underpowered and overpriced as the old Durons or Celerons are.

As far as your driver concerns go, I've never had trouble with anything for drivers relating to my amd cpus under linux or windows. Drivers are designed to work with a generic x86 (or x86_64) architecture, and don't differentiate between amd and intel. 

As for wireless, you can look for an atheros or a natively-supported chipset, and if you find one for a decent price, get it. OTOH, just about every popular chipset nowadays is supported by ndiswrapper, and many have native drivers either available or in the works and available as a beta. Do a little research, if it won't work or it's problematic, a google search will usually turn up half a dozen forum posts stating that on the first page. The ubuntu wiki also has a list of cards/chipsets [here](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported), however, take it with a grain of salt, not every working card will be listed on that page.

edit: also, I do most of my shopping through newegg. I was just looking through tigerdirect's wireless selection, and googling for linux support, and most of the time the first link was a newegg review. it seems like [this](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=587833&Tab=0&NoMapp=0) may be a decent card to fit your needs. And always avoid D-Link ;-)

While these CPU recommendations are OK, they are not entirely up to date.

1) Sempron = 754 or Socket A, with the socket A being an old XP cut down to half the L2 cache.  If you search really hard, you might find mention of a Sempron 939, but you will never find one in the stores.  There is a new Sempron based on the AM2 socket, but this one requires a different type motherboard.  

2) Since the release of the AM2 socket AMD64 CPUs, the AMD64 939's have dropped way down in price.  Therefore, not cost effective to go for Sempron vs. a true AMD64 939 or even 754 with double the L2 cache.  As examples at NewEgg.

a) Sempron 2800+ Socket A based on the XP - $75.00
b) True AMD64 939 CPU = $66.00 - so much more HP for the buck

Note that I do also have a Sempron CPU (2800+ socket 754) in one of my PC's.  It has 64-bit extensions and is a good setup with my nVidia motherboard.  However, once places like Fry's started selling full AMD64 CPU's for almost the same price as the Semprons it is best to get the better and more powerful CPU.  

I like D-Link myself, as well as any of the other main name brand cards and routers, as long as they have the proper chipset.

---

### Post by Vinn on 2006-08-29
Yeah I had a feeling something was up, I couldn't find a Sempron in 939. Instead I found a regular AMD64 for about the same price as the processor I chose before (754 socket).

Right now this is what I'm looking at: Case ([http://www.newegg.com/Product/Product.asp?Item=N82E16856101002](http://www.newegg.com/Product/Product.asp?Item=N82E16856101002)) Processor ([http://www.newegg.com/Product/Product.asp?Item=N82E16819103537](http://www.newegg.com/Product/Product.asp?Item=N82E16819103537)) and Wifi Card ([http://www.newegg.com/Product/Product.asp?Item=N82E16833127145](http://www.newegg.com/Product/Product.asp?Item=N82E16833127145))

Let me know if this is good so far, just for running Ubuntu and basic applications (no gaming or video editing)

---

### Post by iTrendsNET on 2006-08-29
> **Vinn said:**
> Yeah I had a feeling something was up, I couldn't find a Sempron in 939. Instead I found a regular AMD64 for about the same price as the processor I chose before (754 socket).

Right now this is what I'm looking at: Case ([http://www.newegg.com/Product/Product.asp?Item=N82E16856101002](http://www.newegg.com/Product/Product.asp?Item=N82E16856101002)) Processor ([http://www.newegg.com/Product/Product.asp?Item=N82E16819103537](http://www.newegg.com/Product/Product.asp?Item=N82E16819103537)) and Wifi Card ([http://www.newegg.com/Product/Product.asp?Item=N82E16833127145](http://www.newegg.com/Product/Product.asp?Item=N82E16833127145))

Let me know if this is good so far, just for running Ubuntu and basic applications (no gaming or video editing)

Lookin good!  First off, before I make my final decision on the wireless card I do a couple of Google searches using the card's model # + linux.  Searching on the D-Link DWL-G510, I am finding that only "rev B of this card uses the supported Atheros chipset".  I cannot tell what rev. NewEgg is selling so I would make a phone call first on that one.  Yes, ndiswrapper usually works to get other cards working, but why go through the trouble if you can get a card that works "out of the box"?

Good reviews on the Shuttle box and it looks nice.  It would seem the nVidia 6100 on board graphics will fulfill your needs.  Try a couple of searches on "nvidia+6100" here in the forums to make certain people are placed with how this chipset is performing with Dapper.  It's a newer chipset, but I do not see any major problems and I would buy it.  Also, that motherboard is good and will support a X2 CPU if you want to upgrade later.  

Nice box set processor.  The box gets you the AMD approved fan and a better warranty than if you bought a CPU (only) somewhere.  I think you would be happy with this system.

---

### Post by Vinn on 2006-08-29
> **iTrendsNET said:**
> Lookin good!  First off, before I make my final decision on the wireless card I do a couple of Google searches using the card's model # + linux.  Searching on the D-Link DWL-G510, I am finding that only "rev B of this card uses the supported Atheros chipset".  I cannot tell what rev. NewEgg is selling so I would make a phone call first on that one.  Yes, ndiswrapper usually works to get other cards working, but why go through the trouble if you can get a card that works "out of the box"?

Good reviews on the Shuttle box and it looks nice.  It would seem the nVidia 6100 on board graphics will fulfill your needs.  Try a couple of searches on "nvidia+6100" here in the forums to make certain people are placed with how this chipset is performing with Dapper.  It's a newer chipset, but I do not see any major problems and I would buy it.  Also, that motherboard is good and will support a X2 CPU if you want to upgrade later.  

Nice box set processor.  The box gets you the AMD approved fan and a better warranty than if you bought a CPU (only) somewhere.  I think you would be happy with this system.


Okay, good to hear, thanks :). I went through the list of supported cards a little more thoroughly and found one of the D-Link cards on the list that worked out of box on sale at Newegg for a reasonable price. In fact one of the reviews on the page says it works with the current version of Ubuntu out of box, with only a few extra software installations to fully utilize it.

Here: [http://www.newegg.com/Product/Product.asp?Item=N82E16833127118](http://www.newegg.com/Product/Product.asp?Item=N82E16833127118)

If there are any better cards that aren't very expensive and work better, let me know.

---

### Post by ShadowRage on 2006-08-29
pfft. get a 64 bit AMD cpu, right now the 3200+ is running for $76 on newegg.

socket 939 at least.

the socket 939 runs very cool and can be overclocked with the stock cooler.

on motherboards: abit, asus, asrock (the 939 dualSATA2 is a good board, I use it :)  and it's 90% functional in dapper, sans the SATA2 port) MSI and gigabyte.

RAM: DDR400, unless you want the newest ram out there, then you may want to look into an AM2 socket based mobo with DDR2 ram.

---

### Post by Vinn on 2006-08-29
Well, I would get a 64 bit processor, but seeing as how this little thing is only gonna sit in my room and be used for light work like web browsing, music, and school work, going for a 64 bit seems overkill. If I wanted to build a computer that would be compatible with the current and next generation of operating systems and software I would definitely go with 64 bit though, or dual core if I had that kind of cash. Maybe I'm wrong, blah. The processor you say that costs 76$ on Newegg looks like it'll work with the kit I want, so it's a possibility as well.

Edit: Well, it's 10 bucks more, what the hell why not.

---

### Post by Vinn on 2006-08-29
Well, after browsing through Newegg I was able to find everything I need for under 600$ (a little more if I added a nice flat screen display, though I don't really need it). So far so good.

---

