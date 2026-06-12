---
title: "Why haven't high res monitor problems been addressed yet?"
date: 2008-01-02
forum: Desktop Environments
---

### Post by EAL on 2008-01-02
Sorry if this is the wrong forum to ask a question not support related.

I spent half the day trying to get my new monitor 1920x1200 to work.  I was googling around, and saw that this has been going on since at least 2005.  The widescreen monitors have been around a while.  Why aren't these workable "out of the box."

---

### Post by TeaSwigger on 2008-01-03
> **EAL said:**
> Sorry if this is the wrong forum to ask a question not support related.

I spent half the day trying to get my new monitor 1920x1200 to work.  I was googling around, and saw that this has been going on since at least 2005.  The widescreen monitors have been around a while.  Why aren't these workable "out of the box."

Please pardon my "ranting" back; I've been in your shoes.

As I understand these things, it may well boil down to the same basic reasons why you could spend half the day getting my monitor to work at the proper resolution. My monitor isn't widescreen, isn't LCD, isn't 1920x1200; in fact it's a 1024x768 CRT that predates such trends and is considered "ancient" now (from 2000). Never the less, it still isn't supported at proper resolutions out of the box. 

It's not Ubuntu. It's not Linux. It's nVidia and their marketing policy to build for a PC running a Microsoft product. Ostensibly, you are their customer, and are buying their hardware product. I would presume that if you wanted to use that product with a compatible PC running not unheard-of software, nVidia should be only too pleased to provide the interface 'ware as they do if you happen to want to use it on a PC running a Microsoft product. It's a sale, right? Your business what you want to use that product with, I'd suggest, if you buy, one might presume they're grateful for your support. If they simply could not accomadate (and nVidia absolutely could), then offering the code required to make it possible for the customer to use the product is (really) the least they could do. 

But no; they didn't and still won't offer their code for the software interface required to use the hardware you already bought on whatever you wish. In time they offered the required software of their own making, but then they make you sign contracts with their lawyer preventing you from looking at that code for the product you bought, and which you're going to be putting into your own personal computer. 

That sounds like a pretty strange business relationship to me, unless I were to consider that perhaps they considered others to be their valued friends instead of their customer. Like, oh for sake of arguement, the Microsoft Corporation. Lucky for them I was too ignorant of computers back then to make a considered purchase and most folks still are, oh and not that there's tons of alternatives; unluckily for us, that's "industry standard" policies.

So here we are, complaining at ubuntu. What can they do about the hardware megacorporation policies? Not a gaul darn blasted thing, that's what. What they can do is:

-Try gathering all the different drivers etc eventually offered by all these manufacturers for all these cards over all these years, and then arrange for them all to be installable in a legally acceptable method. That means you likely have to have the computer already working sufficiently to figure out how to jump the hoops to sign the legal releases from the manufacturers so you can go through the trouble of installing extra stuff needed to use the device you already paid for. 

If it's any consolation, you often have to do the same thing if you install Windows from scratch, only Microsoft, who unlike ubuntu is being paid, makes you go find and get the drivers.

-ubuntu has to provide enough support for all hardware to work to some degree, often without the required code. So they try to include as much of the "non-proprietary" support as can be found out there from all the folks who have kindly offered this software of their own making or adaptation. Unfortunately this sometimes results in some situations where the built-in support isn't complete or ideal, and in those cases the user has to agree to install the proprietary software and sometimes do further adjustment. Not everyone knows how, and frustrations are almost sure to follow.

Now as a "consumer" I may have a very different perspective of my business relationship to the hardware folks than the way they think of it. But that might be a contributing reason why I and most of their "consumers" very likely won't even care about the well being of their businesses and their industry in future.

I wrote the nVidia folks a seven year late letter a little while ago, asking them to provide me with the code they're witholding that would allow me to use the product I paid them for as I wish to use it. You may consider doing the same with the manufacterer you supported, and explain the inconvenience and frustrations that their limited "support" caused you. Of course I don't expect I'll be getting a reply to my nutty letter. :p

Take care and good luck. You can't get any help from the business you supported. Luckily, if you have any problems there are lots of people in the boat with you who will freely offer their time and whatever knowledge they may have to help you. You may have to ask a lot and be patient and persistent, but at least the folks here understand.

---

### Post by EAL on 2008-01-03
I understand what you're saying, and you make great points.  But in my particular situation, Ubuntu worked fine out of the box, with the previous monitor.  To get the new, wide monitor to work, I didn't have to go get any new drivers (like I did to get it to work on Vista) but I did have to spend have a day messing with it.  My point was, it would seem by now they could have made widescreens selectable out of the box.

But hey.  Ubuntu is worth every penny I paid for it, so I don't really have grounds to gripe, I just thought it odd that something like this hasn't been implemented and wanted a behind the scenes look at why it hasn't.

---

### Post by kpkeerthi on 2008-01-04
My LCD is 1920x1200 and it works out of the box (both with open source and binary driver). I know a few who are using 24" LCDs with ubuntu.

---

### Post by jimbudler on 2008-01-04
My high res monitor works fine, but I found out that it doesn't report EDID on the VGA port, only on the DVI port.

So when I booted the first time with it, using the VGA cable,  it was unrecognised and an /etc/X11/xorg.conf.failsafe was created.

All my editing of the xorg.conf file did nothing until I removed the xorg.conf.failsafe file.

1680x1050
:)

---

### Post by jespdj on 2008-01-04
> **EAL said:**
> I spent half the day trying to get my new monitor 1920x1200 to work.  I was googling around, and saw that this has been going on since at least 2005.  The widescreen monitors have been around a while.  Why aren't these workable "out of the box."
It is simply not the case that wide screen and / or high resolution monitors do not work out of the box with Ubuntu. There is no general kind of problem with these kinds of monitors or graphics cards that "hasn't been addressed yet". I have a Dell 2405FPW and it works out of the box on 1920 x 1200.

The problem is not in the monitor, but in the driver for your graphics card. Which graphics driver are you using? Which graphics card do you have in your computer?

---

