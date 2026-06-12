---
title: "Latitude D630 - two questions"
date: 2008-05-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by StratosL on 2008-05-13
Hi there!

I have just installed 8.04 on a Dell Latitude D630 and everything looks good, except for two things: screen resolution and wireless.

1) The graphics card is Intel 965. The resolution I get is 1200x800. How can I make it 1440x900 like in windows?

2) I used the instructions in [http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088) to make the wireless Dell 1395 to work. However, I can't seem to be able to connect to wpa2 networks. Is is a feature, a bug, or is it possibly me doing something wrong?

Thanks,

SJL

---

### Post by ubuntu-freak on 2008-05-13
I can only help with your first problem, sorry.
 
Press Alt F2, type "gksudo displayconfig-gtk" and your password when prompted, then select the resolution you mentioned in your post.
 
Nathan

---

### Post by jonpz on 2008-05-13
I too am on a Latitude D630 with the Intel 965 integrated graphics and am running at the 1280x800 resolution.  When I booted into Windoze to double check, that was my highest available resolution there as well.  Are you sure you're getting a 1400 resolution out of your Latitude?  Maybe there's some alternate configuration to the D630 that I'm not aware of.

As to your second issue.  I am experiencing the same thing.  I tried to no avail to get native Linux drivers working for my bcm4310 wireless, and had to resort to ndiswrapper.  But on any network running WPA authentication I get shotty performance if any.  Weird thing is that ndiswrapper and WPA worked beautifully in 7.10.  (BTW, I'm using the x64 version).  I've tried a few things I've seen here and there but no luck yet.  The next thing I think I'll try is compiling the latest version of ndiswrapper from source.  I'll keep ya posted.

Anyone else have any ideas?  Or possibly a way to get this wireless working without ndiswrapper?  That would be oh so lovely.

---

### Post by enchantedsky on 2008-05-13
According to [http://www.dell.com/content/products/productdetails.aspx/latit_d630?c=us&l=en&s=biz&cs=555](http://www.dell.com/content/products/productdetails.aspx/latit_d630?c=us&l=en&s=biz&cs=555) there are two versions of the Dell D630. One has 1440x900 (WXGA+)resolution and the other 1280 x 800 (WXGA).

---

### Post by cacycleworks on 2008-05-14
I've got a D630 ... just today installed ubuntu 8.04 x86_64 desktop "alternate" iso... 1440x900 out of the box. Sound and wireless worked without making any settings (first time ever I have gotten 64bit, sound, and wireless on one go).

Not sure if there is a command one can type to tell the difference between WXGA and WXGA+ ... here's my lspci output:

```

lspci -vvnn
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c) (prog-if 00 [VGA controller])
	Subsystem: Dell Latitude D630 [1028:01f9]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
	Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at eff8 [size=8]

```

The screenshot attached shows that I have a 19" external monitor attached at 1280x1024... and the 14" laptop screen at 1440x900 overlaid. (laptop is closed)

Hope this helps....
Chris

---

### Post by StratosL on 2008-05-14
I'm also using 64bit. Since the laptop is not mine, I have tried installing two ways: 1) through wubi and 2) via installing to an external usb hard drive. Both ways have worked, I stayed with the second one, which is completely non-intrusive.

In both cases, sound worked, video was 1200x800, wireless was dead. 

As far as I can see, there are various configurations available to this laptop, so that's why I posted the chipsets.

In windows, I have 1440x900. Also, I checked and I don't have an option for wpa2 either. The higher security the setup wizard offers is wpa. Strange.

So, if could just have the higher resolution it would be fine. I will try the instruction in the first reply and come back.

---

### Post by StratosL on 2008-05-14
Thanks, that worked

---

### Post by ubuntu-freak on 2008-05-14
> **StratosL said:**
> Thanks, that worked

 
You're welcome.

---

### Post by jonpz on 2008-05-14
cacycleworks, 
What's your wireless card?

---

### Post by cacycleworks on 2008-05-14
> **jonpz said:**
> cacycleworks, 
What's your wireless card?

It's the intel. I tried searching for everything I could before getting this laptop and chose the intel 3945. imho, it's worth [$15 to not need ndiswrapper]("http://cgi.ebay.com/Intel-Pro-3945-Wireless-MINI-Card-802-11-a-b-g-802-11g_W0QQitemZ360051219434QQihZ023QQcategoryZ45000QQssPageNameZWDVWQQrdZ1QQcmdZViewItem").  :-)

The other intel card (4965?) appears more difficult to make work than the broadcomm one. Searching [D630 on the forum]("http://ubuntuforums.org/search.php") should help you get 1440 video. I'm surprised that 1440 isn't working out of the box for you, as the install I did was by a wide margain the easiest I've ever done. 

Piling on to the "easy-ness" is that I next installed the FOSS flash plugin for mozilla and it worked. Then in did apt-get install kubuntu-desktop and *everything* works in kubuntu. I'm shocked, stunned, etc, over how well it went.

Thanks,
Chris

---

### Post by irish8890 on 2008-05-14
Follow the instructions here to get the Broadcomm card working:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

I can connect wirelessly, however, I have not been able to get wireless security to work.  You can try this if you wish:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
I disable wireless security on my home router when I am using my D630 laptop.

I do have 1440X900 screen resolution.  I have the nVidia Quadro NVS135 graphics card.  Hardy works fine out-of-the-box but if you download & install the nVidia drivers you get the nVidia tools and they help with dual monitors, etc.  nVidia drivers are here: 
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

My problem with Hardy is that I get the machine locked up (scroll-lock & caps-lock lights flash) if I am using the touchpad and wireless (at least that is what I have been able to figure out).  Machine is much more stable with wired internet and mouse.  Any others have this problem?

Good luck! & TIA!

John

---

### Post by cacycleworks on 2008-05-15
Hmmm. Mine has the intel 945gm video chipset. :confused: Sounds like the nvidia version is where intel was when the D630 was first released. The only way to get video then was someone compiled their xorg and shared the .deb with the rest of us.

---

### Post by sam_delta on 2008-05-15
hello everyone in here, 
im planning in buying a d630 myself and ill be using ubuntu on it
any suggestions?
ill be getting it w

core 2 duo @ 2gig 2mb cache
2g Ram
120 g HD @ 5400 RPM
integrated graphics, intel X3100
WXGA+ LCD screen
intel wireless 3945 802.11a/g

thats all, what do you think about it, is it a good laptop?, any recomendation on the hardware? for ubuntu compatibillity?

thx sam

---

### Post by ubuntu-freak on 2008-05-16
> **sam_delta said:**
> hello everyone in here, 
im planning in buying a d630 myself and ill be using ubuntu on it
any suggestions?
ill be getting it w

core 2 duo @ 2gig 2mb cache
2g Ram
120 g HD @ 5400 RPM
integrated graphics, intel X3100
WXGA+ LCD screen
intel wireless 3945 802.11a/g

thats all, what do you think about it, is it a good laptop?, any recomendation on the hardware? for ubuntu compatibillity?

thx sam

 
Well, compatibility looks good to me. If you want to play intensive games, you may need an NVIDIA graphics device. If you're not a hardcore gamer, the Intel X3100 will be fine, and desktop effects will work with it in Hardy.
 
Nathan

---

### Post by sam_delta on 2008-05-16
ty very much for the input Nathan, i think ill be fine with the intel as i do not play games at all. i like compiz, but as you say, nothing that cant be handled by the x3100

cant wait!!!!

sam

---

### Post by cacycleworks on 2008-05-16
> **sam_delta said:**
> hello everyone in here, 
im planning in buying a d630 myself and ill be using ubuntu on it
any suggestions?
ill be getting it w

core 2 duo @ 2gig 2mb cache
2g Ram
120 g HD @ 5400 RPM
integrated graphics, intel X3100
WXGA+ LCD screen
intel wireless 3945 802.11a/g

thats all, what do you think about it, is it a good laptop?, any recomendation on the hardware? for ubuntu compatibillity?

thx sam

Sam, that looks great... if available, you may want to consider:
- core2 duo with 4mb cache
- 7200 rpm HD

Both should add some snap to your computer. I later purchased memory separately from an inexpensive vendor.

:-)
chris

---

### Post by sam_delta on 2008-05-16
alright, yeah, i think theres a 4mb cache processor available, what might be the difference from the 2 mb cache processor? when is it going to b noticeable?

thx for your advice
sam

---

### Post by cacycleworks on 2008-05-20
> **sam_delta said:**
> alright, yeah, i think theres a 4mb cache processor available, what might be the difference from the 2 mb cache processor? when is it going to b noticeable?

Hey Sam, memory always makes things faster. Will you notice? I have no idea!! :) But is my opinion that for small increase in price you can double the memory inside the cpu and it has to be a good thing. 

If the 2MB to 4MB option was very expensive, I wouldn't do it. I personally always try to buy technology when it is priced "in the middle", meaning if a toy is $50 for something 2 years ago, $80 to $110 for last year, and $400 for today, I buy the $110 one. I feel the 4MB option is comparable to the "$110 option" in my example.

Google helped me to find [this page]("http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=2795&p=4"), which says: > if this processor will be the basis for your system for the next several years, we'd strongly recommend picking a 4MB flavor of Core 2

:) Chris

---

### Post by sam_delta on 2008-05-20
thanks cacycleworks , ill be ordering my laptop today and ill be upgrading the processor to 3-4MB depending on the prices, thanks

sam

---

### Post by cacycleworks on 2008-05-21
> **sam_delta said:**
> thanks cacycleworks , ill be ordering my laptop today and ill be upgrading the processor to 3-4MB depending on the prices, thanks -sam

Yaay, great! I really like my D630 and hope you get as much happiness from yours as I do with mine. :) I think this is one of the best buys on the market.

:) Chris

---

### Post by sam_delta on 2008-05-21
yeah, ordered it yesterday, Cant wait!!!!!, current status: order processing

i ended up with a 2.1G @ 3mb cache dual core, 2g ram, fingerprint reader, bluetooth WXGA+ LCD, 

cant wait bro!!

sam

---

### Post by walterhtx on 2008-06-27
Hi there. I deal with dell notebook PCs regularly. On the D620 and D630 it goes like this:

WXGA LCD will give a max. res. of 1280 X 800
WXGA+ LCD will give a max. res. of 1440 X 900

Hope this helps!

---

### Post by sam_delta on 2008-06-27
> **walterhtx said:**
> Hi there. I deal with dell notebook PCs regularly. On the D620 and D630 it goes like this:

WXGA LCD will give a max. res. of 1280 X 800
WXGA+ LCD will give a max. res. of 1440 X 900

Hope this helps!
thanks for the info walter, i was in debt if going for the wxga or wxga+, i ended up going for the wxga+, got it and its awesome, nice crystal clear display

sam

---

### Post by cacycleworks on 2008-07-01
> **sam_delta said:**
> thanks for the info walter, i was in debt if going for the wxga or wxga+, i ended up going for the wxga+, got it and its awesome, nice crystal clear display

sam

Hi Sam,

Great to hear you have your 630 in! You're welcome to ask me any questions about the 630 you have. Maybe I have the easy answer ... or can help point you in a good direction. :)

I got an inexpensive docking station from ebay and have a 24" monitor at 1920x1280(?) and I use an external keyboard as I tend to wear out the keys on notebooks.

And now Ubuntu is the best ever on the 630. 100% perfect install on the first try, the way it "should be".

:) Chris

---

### Post by sam_delta on 2008-07-01
> **cacycleworks said:**
> Hi Sam,

Great to hear you have your 630 in! You're welcome to ask me any questions about the 630 you have. Maybe I have the easy answer ... or can help point you in a good direction. :)

I got an inexpensive docking station from ebay and have a 24" monitor at 1920x1280(?) and I use an external keyboard as I tend to wear out the keys on notebooks.

And now Ubuntu is the best ever on the 630. 100% perfect install on the first try, the way it "should be".

:) Chris
thank you for the help, 

yeah, dell 630 has a great compability with ubuntu, i installed ubuntu 8.04 64bit, everything working out of the box, bluetooth, sound, video resolution, wireless, just had to install a package for the fingerprint reader, its awesome laptop.

thanks for the support, ill drop you a private message if i have any problem, but i debt ill ever  have any problem with this awesome laptop :)


sam

---

### Post by plindsay on 2008-11-09
I installed 8.10 for AMD64 on my D630 and I get periodic system wedges requiring restart. Memory tests pass.  I noticed that two of left side status lights flash green every time this wedge occurs.
I also seem to think it might be related to using a  bluetooth mouse (not sure about it, but system wedged has not happened since I stop using bluetooth mouse...was happening several times a day before). "Maybe" had one system wedge while not using bt mouse. We'll see..
Anyone else having issues with D630 and 8.10?
-phil

---

