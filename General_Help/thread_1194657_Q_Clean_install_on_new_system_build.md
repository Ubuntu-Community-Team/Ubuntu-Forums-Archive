---
title: "Q? Clean install on new system build"
date: 2009-06-22
forum: General Help
---

### Post by wanderingarticfox on 2009-06-22
I'm trying to find out what I might need to do as I am planning out my first system build. This is what has me scratching my head.
I plan to use a Gigabyte GA-MA790GP-UD4H mother board; however there is a 'Remark' below the notes on the specifications' page.

Remark 1. Due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset vendors' website or 3rd party website.

This has me wondering if I will be able to do a 'clean' install of Ubuntu without any other OS on the system. Yes I am reading through the pdf manual [dwnlded from Gigi] but I'm still not clear.

I would like to set up with 2 WD RE3 hard drives in a RAID 1 configuration and install Ubuntu as a 'stand-alone' OS.

Any info or help is appreciated; I do have a request into Gigabyte but have not received a reply.:confused:

---

### Post by wanderingarticfox on 2009-06-23
Can someone tell me if I can install Ubuntu as a stand alone operating system, please???????????:confused:

---

### Post by Bucky Ball on 2009-06-23
Please click on the link in my signature and read my thread. You will find it very helpful. It documents a build specifically for a Ubuntu only machine I did about 5 months ago. :)

I suggest you may be able to download the Linux drivers for that board on another machine, put them on a disk, and transfer them to the new machine, but personally, I would go with a motherboard that is known to be compatible 'out of the box'. I understand what a hassle it is to get the right combination of features you are after on the board, but ... if you are going Linux, you have to think about these things.

I find it a bit ambiguous, as they normally are in these situation about Linux; do they mean the chipset on the board or the chipset on or in a piece of hardware you might add to the box? The version of Ubuntu you load may come prepared for any chipset issues, whatever they are, 'out of the box' anyhow. Ambiguous.

This might help in your quest, and good luck to you with it:

[https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards](https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards)

ps: if the Q-Flash feature is what I think it is - super-fast boot time OS - it will more than likely not function in Linux AT ALL and there is no work around for this. It must be set up using Windows (at least on other boards with a similar feature) so check that out thoroughly if that is important to you.

---

### Post by wanderingarticfox on 2009-06-23
Thx for the responce Bucky Ball. I had just gone a checkin' and found this responce from Gigabyte:

Answer - 774226
Answer : 	Dear Customer,

Yes, you may load Ubuntu. Most of the drivers will already be included with the latest Ubuntu version.

Thank you for choosing Gigabyte products
Question - 774226
From : 	 [ [email]enviropond@verizon.net[/email] ]
Sent : 	6/21/2009 12:39
Question : 	I am considering buying the above board for my new home build; however there is a remark reguarding Linux chipset on the info sheet. I just need to know if I can load Ubuntu [Linux] as a stand alone OS then get the chipsets via AMD?


-------------------------------------------------------------------------------
Model Name : GA-MA790GP-UD4H(rev. 1.0)
--------------------------
M/B Rev : 1.0
BIOS Ver : *****
Serial No. :
Purchase Dealer : New Egg
-------------------------------------------------------------------------------
VGA Brand : ATi      Model : onboard MB
CPU Brand : AMD      Model : PIIX3      Speed : 2.8
Operation System : Linux      SP :
Memory Brand : OCZ      Type : DDRII
Memory Size : 4 GB      Speed : 1200
Power Supply : 600 W


Phenom II X3 @2.8 GHz
PC2 9600 1.8v 4Gb
Western Digital RE3 250GB in RAID 1
Ubuntu 9.04 OS 32 bit

Ambiguous is a mild way of saying they think Ubuntu has it covered. Thanks again for the link. I've been doing some research for the RAID 1 I plan to do but you are correct, it needs to actually work 'out of the box'.

I looked art the link and only AM2 socket type has been evaluated; there are now AM2+ and AM3 multicore sockets.  [Note that some AM2+ can use an AM3 CPU but AM3 sockets can not accomidate AM2+ CPU's]  This is similar to AMD trying to keep up their testing and such on all products using AMD and ATI parts. I'm hoping someone will check this thread that has built stand alone Ubuntu recently and with AMD MB chipsets.

I'm going to continue research and add to this thread. Thx again for responding BB:)

---

### Post by QIII on 2009-06-23
Careful with ATI graphics.  There are a lot of people on the forum singing the blues...

With regard to RAID, I think you have to use the Alternate Install CD (or so says the Ubuntu 9.04 Desktop Handbook by Richard Peterson.)

If you have a Kindle, you can download it.  I think it is only available right now for Kindle and one other ebook format.

I'm looking at a page right now that says the Alternate CD supports specialized features like LVM, RAID and encrypted file systems.

And since you have a 64 bit system, you can take advantage of the 64 bit version.

---

### Post by Bucky Ball on 2009-06-23
> **wanderingarticfox said:**
> 
Yes, you may load Ubuntu. Most of the drivers will already be included with the latest Ubuntu version.


You probably won't need to do anything, Ubuntu will take care of the chipsets on the board, but don't take that as gospel, if you know what I mean. I haven't heard of any problems, but ...

As for the onboard ATI, hmm. As mentioned, that could be problematic.

RAID shouldn't be a problem, but that's easy. Choosing your hardware is vitally important, as you know, and once you've nailed a motherboard you can learn your way through the other stuff.

[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)

Do a search for 'raid1 ubuntu', there is too much information out there! (you could also try appending 'ubuntu' to whatever motherboard you are researching)

Just tell me one thing: Why the hell do you need a 600W PSU? Please read my link, do yourself a favour, help the planet and save some money. You are not even using a video card. 

The system you have outlined would quite easily run from an 85+ energy-efficient,  350 or 430W. (Unless, of course, you are looking for it to double as a heater or to power the bar fridge in your office, which I doubt! :)

You should be using 64bit OS for a 64bit processor, not 9.04 32bit. If you are after more stability, the 8.04 LTS (Long Term Support) version has been out over a year, is very stable and may be the go.

---

### Post by wanderingarticfox on 2009-06-24
Thx again Bucky; I was just about to post due to confusion after reading several different articles on setting up RAID 1 while installing Ubuntu. Bookmarked and flagged that one :)

As for the 600 watt; I'm not building with PCIx16 but will add later on most likely a pair of Gigi GV-R485MC-1GI's.

After some introductory research I now plan 9.04 64bit host; then Virtual Box installation and at least 1 9.04 guest.

I see the advantage of the 64 bit host as far as physical RAM being increased to 8GB.

The learning curve is still on:)

---

### Post by Bucky Ball on 2009-06-24
This will help you work out what you need as far as PSU goes:

[http://www.antec.outervision.com/index.jsp](http://www.antec.outervision.com/index.jsp)

Go for 85%+ efficient unit. Most PSUs rate at about 70% efficiency or less. You will save money over the 200,000 plus hours you will be using the unit.

---

### Post by wanderingarticfox on 2009-06-24
This is kind of a mute issue Bucky; I already have the seasonic and at the risk of making you cringe I have a Rheobus [4 switch] and a total of 8 fans in the CM 690 case.
Look on the bright side I walk, ride bike or bus; yepper I do not own a car, cell phone or mp3. Still using CD's and cassetes:) And yes I recharge batteries:)

---

### Post by wanderingarticfox on 2009-06-24
> **QIII said:**
> Careful with ATI graphics.  There are a lot of people on the forum singing the blues...

With regard to RAID, I think you have to use the Alternate Install CD (or so says the Ubuntu 9.04 Desktop Handbook by Richard Peterson.)

If you have a Kindle, you can download it.  I think it is only available right now for Kindle and one other ebook format.

I'm looking at a page right now that says the Alternate CD supports specialized features like LVM, RAID and encrypted file systems.

And since you have a 64 bit system, you can take advantage of the 64 bit version.

:confused::confused:I did a search via advanced search back 6 months; seems mostly to be "card" issues with the graphics. The 790GX on-board the MB has ATI 3300; trying to find the trouble there?:confused::confused:

Yes on Alternate CD for RAID

---

### Post by Bucky Ball on 2009-06-24
> **wanderingarticfox said:**
> This is kind of a mute issue Bucky; I already have the seasonic and at the risk of making you cringe I have a Rheobus [4 switch] and a total of 8 fans in the CM 690 case.
Look on the bright side I walk, ride bike or bus; yepper I do not own a car, cell phone or mp3. Still using CD's and cassetes:) And yes I recharge batteries:)

Ha, cool, got ya. If you have the PSU, use it. Better than becoming landfill whilst it has some life left.

---

### Post by wanderingarticfox on 2009-06-25
Yo, Bucky; I'm into the physics too!!!!!
Man I gotta TELL YA' IF i COULD DIAL IT BACK 25 YEARS AN GET 'EM TO LISIN' i WOULD; hOWEVER i'M AN OPTOMISTIC/PESSAMIST>> i HAVE HOPE FOR THE FUTURE BECAUSE i KNOW IT'S NOT BRIGHT.
  iN THE MEAN TIME i'M USING A MODULAR UNIT WHICH WILL HELP WITH THE DRAW.
  cAN YOU IMAGINE i AM IN niagara FALLS ,ny AND PAYING MORE PER kw THAN THE FIVE BORROS DOWN-STATE. fIGURE THE HYDRO IS THREE MILES FROM MY PLACE AND i PAY OVER PREMIUM.
   i ALSO WATCH THE suv'S GO BY AT MY BUS STOPS'.:confused::(

---

### Post by Bucky Ball on 2009-06-25
AAagh! Know what you mean about the suv's. They drive me nuts. I stand at the bus stop near some traffic lights three times a week and count all the cars going by with one person in them (driving, naturally!).

I was thinking of holding a sign that just says 'carpool' or 'public transport' or something. 

The last government we had in Australia commissioned a study at one of the universities regarding base load solar power and was it possible. When studies found it was and here's how ya do it, let's get started, the government pulled funding on the project. Arnie Schwarznegger said to the two guys that had been leading the project, "Hey, Come to sunny California and do it here," and that is exactly what they did! They are there now. Crazy, but there are so many stories like it. 

I figure in twenty years we'll all be using hydrogen fuel cells or better, leaving barely a footprint, or we'll all be screwed and in the process of kissing our asses goodbye!

Good luck with it all and don't leap in the Falls in protest just yet ... :)

---

