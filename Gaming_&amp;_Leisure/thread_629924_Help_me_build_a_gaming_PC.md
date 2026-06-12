---
title: "Help me build a gaming PC?"
date: 2007-12-02
forum: Gaming &amp; Leisure
---

### Post by raxz on 2007-12-02
Hi,

It's the holiday season and  I'm afraid I have not been keeping up with the trends of processors and video cards these days and I would like some advice, after searching around the net I found [this site]("http://www.alienware.com/product_detail_pages/Area-51_ALX_SLI/area-51_overview.aspx?SysCode=PC-AREA51-ALX-R6&SubCode=SKU-DEFAULT") now THAT is the best build I ever saw for a gaming PC. On the other hand I found [this]("http://www.mjonesweb.com/alienware.htm") so I was wondering if I can build a "clone" of that PC or would it be much cheaper to...iono....look for other builds?

---

### Post by Sammi on 2007-12-02
STAY AWAY FROM ATI. Ati simply haven't made stable and fully functional Linux drivers for their graphics cards. Maybe they have for a few of them, but far from all.

ATM I would go for a Nvidia 8800 GT 512 MB RAM. Great performance and great value + it should work very well in Ubuntu/Linux, though I haven't tried it personally. 

But just to get in to more detail. Do not even look at the 8600 line. They are a disappointment. It's the 8800 line that is interesting, with it's three different cards GTS, GTX and now the new GT. A quick look up on google gave me these benchmarks comparing these cards:
[http://codamon.com/2007/10/nvidia-8800gt-reviews/](http://codamon.com/2007/10/nvidia-8800gt-reviews/) 
[http://www.tomshardware.com/2007/10/29/geforce_8800_gt/page15.html#performance_round_up](http://www.tomshardware.com/2007/10/29/geforce_8800_gt/page15.html#performance_round_up)

As you can see. it's the GTX that is the real top of the line power machine, but costs the most too, while the GT is right behind it in all the performance benchmarks, but is substantially cheaper.

And don't be fooled in to buying the 8800 GT 256 MB. You want the 512 MB model. There is a difference.

---

### Post by matthewcraig on 2007-12-02
Two words:  SYSTEM76.
Wait... one word.  If you are going to buy a computer for Ubuntu gaming, then purchase one backed by support how you will be using it.

---

### Post by Sockerdrickan on 2007-12-02
two words: build urself

nvidia gpu
amd cpu if you want cheap
corsair ram
corsair psu
seagate hdd

:)

---

### Post by mellowd on 2007-12-02
What's your budget?

Get a 8800GT and a core2duo if you got the cash, if not get an AMD X2. Just like my PC in fact :p  And it's more than fast enough for all the latest and greatest games

---

### Post by LinuxGamer on 2007-12-02
Are you looking to build a system, or having a system built?  I have recently been doing a bit of research to build a Linux compatible gaming PC, and could give you the list of parts I am considering. I have built systems professionally for about 14 years, and have spent the time researching these parts.

ASUS p5n-e sli nvidia nforce 650 sli chipset atx form factor 2xpci-e(x16)/1xpci-e(x1)/2xpci/4xddr2 w/sata2 raid,lan(gb),1394,usb 2.0 & audio (cpu type:intel - socket 775)
# CORE 2 DUO E6750 2.66G (1333Mhz)
# CORSAIR 2GB KIT

Most games do not currently support the Quad Core, in fact from what I was reading, some will actually give a MP error. So I went with a nice Dual core with high ratings.

CREATIVE LABS soundblaster x-fi platinum fatal1ty champion series 7.1 24-bit pci (retail)

Dual WD 250gb wd2500ks / wd2500aaks sata300 16mb 7200rpm (bare drive)
Dual ASUS EN8800GT/G/HTDP/512M GF8800GT HTDP PCI-E 512MB DDR3 w/HDTV & DVI

ASUS dvdrw-1814blt sata lightscribe dvd rw dual drive (black retail)

ASUS 22" vw222u 1680x1050 2000:1 2ms (black/silver)(retail)

And I picked a :
ANTEC sonata iii 500 (black) atx super mini tower case w/500w power supply 3x5.25" 2x3.5" 4x3.5"(hidden) w/front i/o connectors & 120mm case fan x 1

I priced all of these parts over at [Mwave.com]("http://www.mwave.com") and came up with a price of around $1800.  I did a lot of checking, and from what I can find, every single part has worked just fine in Linux separately.  So as long as all together they do not cause some sort of horrible conflict, they should create a killer system.

---

### Post by matthewcraig on 2007-12-02
You'll spend more mail ordering computer parts to put together than you will purchasing a unit, but you'll get none of the support.  So, when you buy something like the X-Fi sound card listed above, you will realize only after you've opened it that it doesn't work well with the Linux kernel.  (Why would you recommend that card of all cards? [see below*])  Do yourself a favor and save yourself years of headache.  Support the Linux community by purchasing from a hardware vendor who supports Linux.



* Quote from ALSA: Create Labs X-Fi: [Unsupported] [PCI] Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time.

---

### Post by raxz on 2007-12-03
Well first off don't mind the budget I can always go down a notch or 2 if necessary I still think the basics apply here(CPU+RAM+VID card) I just want to know how much or what would you build to accommodate future games like the "next gen Quake"....

[quote=LinuxGamer]

Dual WD 250gb wd2500ks / wd2500aaks sata300 16mb 7200rpm (bare drive)
Dual ASUS EN8800GT/G/HTDP/512M GF8800GT HTDP PCI-E 512MB DDR3 w/HDTV & DVI

[/quote]

Dual WD 250gb wd2500ks / wd2500aaks sata300 16mb 7200rpm (bare drive)???? is that the hard disk:confused:

could you post more recommendations like:

CPU:XGhz
RAM:Xamount
VID....

...and so on kinda like on alienware's website.

off course Compiz must work on the video card so I imagine that ATI is out of luck (although I am now using ATI+Compiz but it was such a pain getting it to work on the earlier distros)

If Quad core isn't supported now by most games what about in the near future?:)

---

### Post by LinuxGamer on 2007-12-03
> **matthewcraig said:**
> You'll spend more mail ordering computer parts to put together than you will purchasing a unit, but you'll get none of the support.  So, when you buy something like the X-Fi sound card listed above, you will realize only after you've opened it that it doesn't work well with the Linux kernel.  (Why would you recommend that card of all cards? [see below*])  Do yourself a favor and save yourself years of headache.  Support the Linux community by purchasing from a hardware vendor who supports Linux.



* Quote from ALSA: Create Labs X-Fi: [Unsupported] [PCI] Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time.

Stay up to date, read[ newer info]("http://www.phoronix.com/scan.php?page=article&item=857&num=1") also! :)

---

### Post by matthewcraig on 2007-12-03
You're using an ATI card now, and you still want to experiment with potentially unsupported hardware in Linux?

Take a look at [this system]("http://system76.com/product_info.php?cPath=27&products_id=56") and see if it isn't what you want.  It comes preloaded with Ubuntu.

---

### Post by sirdilznik on 2007-12-03
> **raxz said:**
>  I just want to know how much or what would you build to accommodate future games like the "next gen Quake"....


That's kind of hard to say seeing as the game doesn't exist yet....

Anyway what I can tell you is that I wouldn't go crazy buying the most expensive top of the line stuff and I certainly wouldn't buy from Alienware.  That is unless you like spending WAY too much money.  The fact is that unlike 10 - 15 years ago when advancements in software were constantly pushing the boundaries of the hardware, these days the hardware has far surpassed the software.  My 3 -4 year old 939 Opteron is still plenty fast for everything, and completely overkill for most tasks.  Whatever you do, don't buy very top of the hardware because it is generally 2 -3 X the cost of hardware that is 95 % as effective.

Personally I would wait a bit, if that is an option, as several new technologies are making their way into the market now (or will be very soon) such as the new pcie standards and eventually DDR3 (DDR3 has no real benefits now, but it will eventually) and the new USB standards.  I personally would wait a few months to let the proices drop on those and get something that is future compatible and affordable.

Edit:  While ATI/AMD going open source is a good thing and I believe that their drivers will improve, if I was buying right now i wouldn't even consider anything other than NVIDIA.

---

### Post by fatality_uk on 2007-12-03
Ideal Linux gaming spec: @ UK £ GBP

£170  CPU - Intel Core2 Duo E6850 3.2Ghz (Will overclock to about 3.8-4Ghz relatively easily

£180  Gfx - Evga Geforce880GT Evga do make exceptional gaming cards that usually run faster than a standard 8800GT

£130  Memory 4GB - 2 x Crucial 2GB Kit (2x1GB) Ballistix Memory DDR2 PC2-8500 5-5-5-15 Unbuffered NON-ECC DDR2-1066MHz 2.2V 128Meg x 64

£120  Motherboard - Abit IP35 Pro

£80  PSU - A good quiet one

Total - £680 - Thats a MONSTER PC and will handle pretty much ANY game for the next 18Months at least until 45nm Intel chip comes out, and then with the IP35 spec board, pop out your 65nm chip and throw in your nice new 45 and flog your 65 on eBay :)

Hope that helps

---

### Post by raxz on 2007-12-04
> **fatality_uk said:**
> Ideal Linux gaming spec: @ UK £ GBP

£170  CPU - Intel Core2 Duo E6850 3.2Ghz (Will overclock to about 3.8-4Ghz relatively easily

£180  Gfx - Evga Geforce880GT Evga do make exceptional gaming cards that usually run faster than a standard 8800GT

£130  Memory 4GB - 2 x Crucial 2GB Kit (2x1GB) Ballistix Memory DDR2 PC2-8500 5-5-5-15 Unbuffered NON-ECC DDR2-1066MHz 2.2V 128Meg x 64

£120  Motherboard - Abit IP35 Pro

£80  PSU - A good quiet one

Total - £680 - Thats a MONSTER PC and will handle pretty much ANY game for the next 18Months at least until 45nm Intel chip comes out, and then with the IP35 spec board, pop out your 65nm chip and throw in your nice new 45 and flog your 65 on eBay :)

Hope that helps

Thanks it will at least now I'll have some sort of bench mark.

@sirdilznik I have been waiting for far too long so I think I'll take the plunge this time..

---

### Post by cinematography on 2007-12-04
I don't know if anyone has recommended this, but you could always get a Playstation 3 and install Linux on it. I'm not sure if Linux is able to use its 3D hardware acceleration or no though. But, personally, I'd rather get a console. Building a gaming computer costs so much more.

---

### Post by Sammi on 2007-12-04
Linux wont do 3D acceleration on a PS3, because Sony doesn't want us to access the GPU :(

More info here: [http://en.wikipedia.org/wiki/Linux_for_PlayStation_3](http://en.wikipedia.org/wiki/Linux_for_PlayStation_3)

There is a big difference between gaming on a computer and on a console, so I don't think this is even relevant to discuss.

---

### Post by desertboy on 2007-12-04
Speaking from experience, I have 2 gig of ram, a core duo 2.4ghz and an 8800GTS 640meg. It runs games very well but if you're thinking Crysis while it does run well on medium settings at 1680x1050 up the settings to max and the game crawls (Literally a couple of frames a sec.)

I wouldn't worry too much about 4 gig of ram as 2 gig of matched pair low latency ram will give better performance than 4gig of average ram.

I would definitely go for Nvidia (Especially for it's linux support, but they do have the best cards on the market at the moment.) if budget allows I would seriously consider an 8800GTX and an SLI motherboard so you can add a second one next year when they drop in price dramatically.

An xbox360 pad wouldn't go a miss either especially if you want to play 360 ports like gears of war or lost planet.

Unfortunately and no one said it yet, you probably want Vista as well. (Unless you get a directx9 only card)

I use Vista and because I only play a couple of games online all of which work with Ubuntu either native or through Wine I haven't installed an internet connection for Vista (Except on first boot to update and once a month after that) I've found Vista so much more reliable than my friends or work Vista.

---

### Post by ukripper on 2007-12-04
> **Sammi said:**
> Linux wont do 3D acceleration on a PS3, because Sony doesn't want us to access the GPU :(

More info here: [http://en.wikipedia.org/wiki/Linux_for_PlayStation_3](http://en.wikipedia.org/wiki/Linux_for_PlayStation_3)

There is a big difference between gaming on a computer and on a console, so I don't think this is even relevant to discuss.

Blimey just got xbox360 3 months ago could have got ps3 and put my ubuntu on it. Damn never mind next time:)

---

### Post by JurB on 2007-12-04
+1 for the 8800 GT
I've got a EVGA superclocked model, it works great in ubuntu with the latest drivers.

quake wars runs at 60 FPS with everything on max settings (including max AA)

---

### Post by fbmx24 on 2007-12-04
I always say build it yourself or have someone do it for you. It saves alot 

of money and you get better components. 

My system specs:
 CPU: amd 4400x2
 Video card: Nvidia 7600gt
 Ram: 2gb
 
 With this set up I can play wow at 68-75 fps at 1440x900 resolution. This 

is with the settings at medium to high. It also plays game like bio shock and 

half life 2 really well. You can get a good cpu from AMD cheaper than from 

Intel and spend more on a good video card. If money is not a problem go 

for an Intel cpu since the are faster.

---

### Post by ukripper on 2007-12-05
Nowadays parts are really cheap I would recommend highly to build your own customised machine and go for Nvidia cards not ati.

---

### Post by raxz on 2007-12-06
Hi...me again uhm can someone translate this in "english" for me:

> 
2 x Crucial 2GB Kit (2x1GB) Ballistix Memory DDR2 PC2-8500 5-5-5-15 Unbuffered NON-ECC DDR2-1066MHz 2.2V 128Meg x 64


All I understood was "GB" part..:)

---

### Post by s_spiff on 2007-12-07
Correct me if I'm wrong, but it means a Crucial (the company ), the Bllastix Memory series ram, of type DDR2, unbuffered ( which means it won't preprocess, and check for errors and **** ) which comes in a 2 x 1GB pack. And the's reccomending you pick up two such kits, which effectively means 4gb of DDR2 ram ( which is cheaper!). The rest, I dunno :(.

---

### Post by raxz on 2007-12-07
> **s_spiff said:**
> Correct me if I'm wrong, but it means a Crucial (the company ), the Bllastix Memory series ram, of type DDR2, unbuffered ( which means it won't preprocess, and check for errors and **** ) which comes in a 2 x 1GB pack. And the's reccomending you pick up two such kits, which effectively means 4gb of DDR2 ram ( which is cheaper!). The rest, I dunno :(.

hmmm... interesting so there are 2 types of DDR2 RAM nowadays eh and I wasn't aware that there are other huge companies for RAM except for Kingston.

---

### Post by GeorgiaBoot on 2007-12-08
There are many types of ram, DDR, DDR2, DDR3 and different types in each sub category. 

There are many manufactures for memory, Kingston being a big one. I used to only buy Kingston but I found PNY to be half the price and at the same level of workmanship. I would stick with reputable Manufactures for memory. 

Have you ever built a Computer?

I know you would like to get all your info here and it be simple but the fact is you need to do a little research and reading. This is just to help you. As if you bought a bunch of stuff and either it was not compatible or you did not know how to put it all together.

Ask here by all means, just read a bit up on some stuff so it is not soo confusing if someone mentions something. :)

Goodluck

---

### Post by dudeofthedead on 2007-12-08
My graphics card (Asus EN8800GT 512MB) should be available by December 15th and I have already ordered the following pieces:

Intel E6750
Midi Tower ATX Zirco AX
550W power supply
Asus P5K (includes sound card, ethernet card...)
3 GB DDR2 800Mhz
320GB HD Maxtor

Now hoping it'll work smoothly with Debian Etch!

---

### Post by jofo02 on 2007-12-08
I have recently put together a system

Intel Q6600 quad core
Mobo: Asus P5KC (P35 Chipset)
GPU: Asus EN8800GTX
Memory: 4x1gb (Corsair TWIN2X2048-6400C4DHX)
PSU: Corsair PowerSupply (PSU) 620W HX ATX
Midi tower: Antec Performance One P182

Sadly, I read that this motherboard does NOT support SLI, so I cannot add the second 8800GTX I have... Now I am planning to get another motherboard, and looking for suggestions. 

2 16x PCIe in SLI, and ubuntu support. Will that be the Nforce 680i chipset?

---

### Post by jotje on 2007-12-15
Build your self of course.

Processor intel q6600 2.4 ghz
Memory: kingston hyper x 800mhz -1200 mhz DDR2 don't go for ddr3 to expensive
Motherboard: get one with a p35 or a x38 if you want SLi get one with an nVidia chipset
Graphic: card nVidia 9800GTX (release is in feburar(well that's what there say'ing now)
PSU: 700-800W
HDD: Western digital raptor 10000 rpm 150 GB
A big chassis something like a cooler master cosmos(the bigger the better).

and For Jofo2

As of now, no Intel chipset supports nVidia SLI - including X38. If you want to use SLI, you need an nVidia chipset (like 680i). Intel chipsets only support ATI crossfire.

With regard to supporting both technologies:
I have heard that Intel's somewhat-soon-to-be-released 'Skulltrail' chipset will support SLI, but it will also cost an arm and a leg.

I've also heard that Gateway's top of the line gaming machine uses an nVidia 680i motherboard (ASUS Striker Extreme) and can run ATI Crossfire with a trick BIOS.

---

