---
title: "Dell Inspiron Mini 10"
date: 2009-06-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by marsdend on 2009-06-16
Hi, I have recently purchased the Dell Mini 10. When ive installed Ubuntu the graphics are not very good and the web pages are not in proportion to the screen size.

Any help would be appreciated.

Thanks
Dan

---

### Post by tyroeternal on 2009-06-16
The problems with video are due to the video chipset that the Dell Mini 10 (and 12) use, the Intel GMA 500 (aka Poulsbo) chipset.  Unfortunately there is not a good set of drivers for this chipset, but there is some progress!

You have 3 options:

#1 There are drivers working based on the Hardy LTS release.  If you are not worried about having the most up to date solution, this would not be a bad idea.  Using the Dell Repos will get you a working and generally stable, but older system.  This method will have some functioning 2D and 3D drivers, but nothing amazing.

#2 Last I heard this is a bit of a problem... but there are 2D & 3D drivers working for Intrepid.  A kernel update caused me problems with this system, but for a time it worked well.  I've also heard of people installing Jaunty, and then moving to Intrepid's old Xserver and Kernel versions, then installing the working 2D & 3D drivers on their cross-breed system.

#3 Running Jaunty (the current Ubuntu release).  As you've noted the system works, just not the graphics.  There are working 2D drivers, but no 3D yet.  Use the ubuntu-mobile ppa ([https://launchpad.net/~ubuntu-mobile/+archive/ppa](https://launchpad.net/~ubuntu-mobile/+archive/ppa) - follow the instructions on the page for adding it to your system) to install the needed packages: xserver-xorg-video-psb along with its required packages and you should have a better functioning system.

I hope this all makes sense.  If you have questions be sure to ask and hopefully I can help you out.  As of right now I use Jaunty with the psb video driver (option #3)

---

### Post by marsdend on 2009-06-16
> **tyroeternal said:**
> The problems with video are due to the video chipset that the Dell Mini 10 (and 12) use, the Intel GMA 500 (aka Poulsbo) chipset.  Unfortunately there is not a good set of drivers for this chipset, but there is some progress!

You have 3 options:

#1 There are drivers working based on the Hardy LTS release.  If you are not worried about having the most up to date solution, this would not be a bad idea.  Using the Dell Repos will get you a working and generally stable, but older system.  This method will have some functioning 2D and 3D drivers, but nothing amazing.

#2 Last I heard this is a bit of a problem... but there are 2D & 3D drivers working for Intrepid.  A kernel update caused me problems with this system, but for a time it worked well.  I've also heard of people installing Jaunty, and then moving to Intrepid's old Xserver and Kernel versions, then installing the working 2D & 3D drivers on their cross-breed system.

#3 Running Jaunty (the current Ubuntu release).  As you've noted the system works, just not the graphics.  There are working 2D drivers, but no 3D yet.  Use the ubuntu-mobile ppa ([https://launchpad.net/~ubuntu-mobile/+archive/ppa](https://launchpad.net/~ubuntu-mobile/+archive/ppa) - follow the instructions on the page for adding it to your system) to install the needed packages: xserver-xorg-video-psb along with its required packages and you should have a better functioning system.

I hope this all makes sense.  If you have questions be sure to ask and hopefully I can help you out.  As of right now I use Jaunty with the psb video driver (option #3)

Hi thanks very much for your reply. With the option 3 do you have a crisp display like other systems. My other laptop is a Medion Akoya Mini which was just a cheap one out of Aldi, this worked better out of the box than the dell which was shocking. What are the difference between the 2D drivers and 3D drivers?

Thanks,
Dan

---

### Post by mikewhatever on 2009-06-16
I was just reading [a dell mini 10 review]("http://forums.thoughtsmedia.com/f305/dells-inspiron-mini-10-reviewed-93798.html"), and it appears there are graphical issues with XP too. I wonder if Dell has any quality control at all.

---

### Post by tyroeternal on 2009-06-16
The display will be at the correct resolution, and everything will look correct.

The downsides are:  there is virtually no hardware accelleration on the video, and there is no 3d driver.  Scrolling web pages is really choppy, and viewing things like flash and large videos is painful as well.

Unfortunately, for work to get done, the Ubuntu team has to take packages from Intel... and it is not even their graphics core... Intel licensed it from elsewhere.  This long path to updates seems to be the problem.  That and there seems to be little coming out of intel thus far.  If you add the ubuntu-mobile repository, you'll get updates about as fast as anyone else in the world, though :)

---

### Post by mikewhatever on 2009-06-16
How does dell mini 10 do with Ubuntu 8.04? Does it have the same graphical issues? I understand that 8.04 works fine with GMA950 (which is apparently in mini 10v), but 10v is not available with Ubuntu.

---

### Post by marsdend on 2009-06-17
> **tyroeternal said:**
> The display will be at the correct resolution, and everything will look correct.

The downsides are:  there is virtually no hardware accelleration on the video, and there is no 3d driver.  Scrolling web pages is really choppy, and viewing things like flash and large videos is painful as well.

Unfortunately, for work to get done, the Ubuntu team has to take packages from Intel... and it is not even their graphics core... Intel licensed it from elsewhere.  This long path to updates seems to be the problem.  That and there seems to be little coming out of intel thus far.  If you add the ubuntu-mobile repository, you'll get updates about as fast as anyone else in the world, though :)

Hi thanks, do you get many updates with this or not? The other thing i had problems with was the audio it was really quiet but using windows it was really loud, is there any way to fix this?

Cheers
Dan

---

### Post by R_U_Q_R_U on 2009-06-17
> **tyroeternal said:**
> T  As of right now I use Jaunty with the psb video driver (option #3)

I have one on order and after reading this wonder if I should cancel. 

Would you buy this unit again knowing what you do about GMA 500 support?

---

### Post by tyroeternal on 2009-06-17
Video updates have been sparse.  There was one last month, but it only comes at the speed intel delivers it... which has been slow (i've joined the process of waiting at the start of last month.

As far as audio is concerned, It has always been very quiet.  Opening the volume controls and making sure all sliders are maxed out makes it almost audible.

Buying the mini 10/12 is a big mistake.  There are many other, better offerings.

---

### Post by superm1 on 2009-06-17
> **R_U_Q_R_U said:**
> I have one on order and after reading this wonder if I should cancel. 

Would you buy this unit again knowing what you do about GMA 500 support?
If you still have the option to cancel at this point, cancel and pick up the 10v instead with ubuntu:

[http://www.dell.com/us/en/home/notebooks/laptop-inspiron-10/pd.aspx?refid=laptop-inspiron-10&s=dhs&cs=19&~oid=us~en~29~ubuntu_anav_2~~](http://www.dell.com/us/en/home/notebooks/laptop-inspiron-10/pd.aspx?refid=laptop-inspiron-10&s=dhs&cs=19&~oid=us~en~29~ubuntu_anav_2~~)

---

### Post by R_U_Q_R_U on 2009-06-18
> **tyroeternal said:**
>  ... Buying the mini 10/12 is a big mistake.  There are many other, better offerings.

What models would you suggest that have similar specs to the Mini 10? Specifically, does anyone have an HD screen with a better graphics chip?

I still have time to cancel my order, so I'd really like to check out the better offerings.

---

### Post by marsdend on 2009-06-18
> **R_U_Q_R_U said:**
> What models would you suggest that have similar specs to the Mini 10? Specifically, does anyone have an HD screen with a better graphics chip?

I still have time to cancel my order, so I'd really like to check out the better offerings.

If you do not require dell, I have an Medion Akoya Mini with around 5 hours battery life, 160 HD, Wireless N Technology, Webcam for a lower price! I recently bought the Dell mini 10 and ubuntu i feel is a no go so far. On the medion EVERYTHING works out of the box even the wireless card! so no having to fiddle with ndiswrapper.

This is the link to their website
[https://www.medionshop.co.uk/mdshop/popup/printViewZProductDetailB2C.jsp](https://www.medionshop.co.uk/mdshop/popup/printViewZProductDetailB2C.jsp)

Hope this helps.
Dan

---

### Post by R_U_Q_R_U on 2009-06-18
Well, I cancelled my Mini 10 order after getting an email today that it would be delayed for another month! They must be having some kind of problem with the red ones ;-(
 
In any event, I still want and 10" netbook with an **HD** screen that is capable of running Ubuntu "out of the box". No need for HDMI connector. No GMA -500!
 
Can anyone suggest some models to check out?
 
Thanks.

---

### Post by marsdend on 2009-06-18
> **R_U_Q_R_U said:**
> Well, I cancelled my Mini 10 order after getting an email today that it would be delayed for another month! They must be having some kind of problem with the red ones ;-(
 
In any event, I still want and 10" netbook with an **HD** screen that is capable of running Ubuntu "out of the box". No need for HDMI connector. No GMA -500!
 
Can anyone suggest some models to check out?
 
Thanks.

Did you have a look at the medion one? I dont think it has a HD Screen and I doubt you will find one with a netbook they are mainly just meant for web surfing and basic use. The medion does have a 10" Screen.

Heres the specs:

Product Description

The sleek and stylish netbook for Everyone!

Feel a new level of freedom and independence with the new Medion Akoya Mini E1210. Now with a 160GB hard drive.
Features

    * Genuine Microsoft® Windows® XP Home
    * Intel® Atom TM Processor N270 (1.6GHz)
    * Intel® Graphics Media Accelerator 950
          o based on PCI-Express technology 
    * Integrated loudspeakers
    * 10" TFT widescreen display
          o 1024x600 pixels 
    * 160GB hard disk
    * 1GB DDR2 SDRAM
    * Integrated webcam and microphone
    * Multi-format memory card reader
          o SD, MMC, MS 
    * Wireless LAN 801.11b/g Draft-N
          o up to 300 mbit/s* and 802.11b/g compatibility 
    * Fast Ethernet LAN port (10/100Mbit/s)
    * External AC adapter
    * Li-Ion battery 

Interfaces

    * 3x USB 2.0
    * 1x LAN (RJ45)
    * 1x VGA
    * 1x Microphone
    * 1x Line Out 

Weight and Dimensions

    * Weight: 1.2kg inc. battery
    * Dimensions (WxDxH): 260 x 180 x 19/31.5 mm 

Software

    * Microsoft® Windows® XP Home Edition (SP3)
    * Corel® WordPerfect Office X3
    * OEM Versions preinstalled and /or on CD/DVD or recovery DVD 

Warranty

12 months

 

Image for illustration purposes only

---

### Post by tyroeternal on 2009-06-18
My first recommendation would be the system 76 starling: [http://system76.com/product_info.php?cPath=28&products_id=92](http://system76.com/product_info.php?cPath=28&products_id=92)

System 76 also has its own support section in this forum, and they do a great job of selecting hardware for their pcs.

In general I've heard great things of the eee 1000he, and the acer aspire one.  I cannot speak of their ubuntu/linux friendliness.

---

### Post by aidanb on 2009-11-10
Hi, I also have a Dell Inspiron Mini 10.  I had Windows 7 starter on it for a while but I just installed Ubuntu 9.10 on it from a USB live drive.  Unfortunately it has some issues:

* There seems to be no wireless; I'm not sure where to look for the right drivers, so could someone excuse my noobness and point me in the right direction?

* The disk apparently has many bad sectors.  How bad is this, and is it bad enough to warrant returning my computer?  I got it unexpectedly quickly, it would be a shame to have to wait a long time.  I have an old Macbook as backup though, so it's no biggie.

Thanks for any help, and if I should make a new thread out of this please let me know and I will do so.

---

### Post by fjgaude on 2009-11-10
> **mikewhatever said:**
> How does dell mini 10 do with Ubuntu 8.04? Does it have the same graphical issues? I understand that 8.04 works fine with GMA950 (which is apparently in mini 10v), but 10v is not available with Ubuntu.

I have a mini 10n with the factory install of 8.04 and it is perfect in all respects, and I mean all. I do have a 1366 x 768 screen and what a joy to use, surfing the web and the like. No issues with video speed. I don't play 3D games!

---

### Post by mikewhatever on 2009-11-11
> **aidanb said:**
> ...........

* There seems to be no wireless; I'm not sure where to look for the right drivers, so could someone excuse my noobness and point me in the right direction?

System->Administration->Hardware Drivers. The utility should be able to download and install the proprietary Broadcom driver, but you'll need to connect with a cable for it to work.

> * The disk apparently has many bad sectors.  How bad is this, and is it bad enough to warrant returning my computer?  I got it unexpectedly quickly, it would be a shame to have to wait a long time.  I have an old Macbook as backup though, so it's no biggie.

A lot of false positives has been reported with the new disk checking program. I wouldn't worry if it is a new computer.



> **fjgaude said:**
> I have a mini 10n with the factory install of 8.04 and it is perfect in all respects, and I mean all. I do have a 1366 x 768 screen and what a joy to use, surfing the web and the like. No issues with video speed. I don't play 3D games!

Ah, how I wish Dell sold the 'n' series around the world, and not in a few selected countries.

---

### Post by fwhall on 2009-11-17
> **fjgaude said:**
> I have a mini 10n with the factory install of 8.04 and it is perfect in all respects, and I mean all. I do have a 1366 x 768 screen and what a joy to use, surfing the web and the like. No issues with video speed. I don't play 3D games!


Agreed, I just got a mini 10 with the hi-res screen and there are no graphics problems.  I am having a problem with bluetooth which I haven't sorted out yet and it seems like it runs really hot but so far, it's pretty decent.

---

### Post by Cyn Jade on 2009-12-09
> **fwhall said:**
> Agreed, I just got a mini 10 with the hi-res screen and there are no graphics problems.  I am having a problem with bluetooth which I haven't sorted out yet and it seems like it runs really hot but so far, it's pretty decent.

Has anyone tried to play a DVD on the Dell Mini 10 (using Ubuntu).  Anyone having problems with wireless n connectivity on the same computer?

I'm looking at buying, and would like to know before I order.

---

### Post by trixman on 2009-12-11
> **superm1 said:**
> If you still have the option to cancel at this point, cancel and pick up the 10v instead with ubuntu:

[http://www.dell.com/us/en/home/notebooks/laptop-inspiron-10/pd.aspx?refid=laptop-inspiron-10&s=dhs&cs=19&~oid=us~en~29~ubuntu_anav_2~~](http://www.dell.com/us/en/home/notebooks/laptop-inspiron-10/pd.aspx?refid=laptop-inspiron-10&s=dhs&cs=19&~oid=us~en~29~ubuntu_anav_2~~)

have one on order looking forward to my first all linux pc.

---

### Post by trixman on 2009-12-11
> **fjgaude said:**
> I have a mini 10n with the factory install of 8.04 and it is perfect in all respects, and I mean all. I do have a 1366 x 768 screen and what a joy to use, surfing the web and the like. No issues with video speed. I don't play 3D games!

sounds good,

---

### Post by utrrrongeeb on 2009-12-12
> **Cyn Jade said:**
> Has anyone tried to play a DVD on the Dell Mini 10 (using Ubuntu).  Anyone having problems with wireless n connectivity on the same computer?

I'm looking at buying, and would like to know before I order.

I installed Ubuntu 9.04 Jaunty on a Dell Mini 10 through Wubi, with an external CD drive. Overall I'm satisfied with its performance.

I installed netbook-remix packages, and followed some widely available steps to get proprietary drivers for the GMA500 Poulsbo graphics card. (These aren't available for Karmic, as far as I know.) The drivers provide some acceleration and the full display resolution. SuperTuxKart (which is 3D) runs at a poor but just playable framerate, fullscreen, while SuperTux2, despite being 2D, is far less playable.

I tried a DVD once with the external drive -- it played, perhaps with a stutter once, although the internal speakers are too quiet.

The Bluetooth mouse needed only minimal configuration, and the special keys on the keyboard "just worked." Sleeping works, although it can only be resumed by opening the lid, and it's crashed once or twice on resuming, usually when 3D graphics are involved. Hibernation is disabled due to Wubi.

However, Wubi must have misread the locales from Windows XP, because the keyboard layout was automatically set for Canadian French. This was inconvenient until I found the settings to change it.

I haven't tried the Wifi -- the drivers says it's present, and it appears to "do something," but it didn't notice a password-protected hotspot.

The webcam works, but I haven't gotten the microphone working yet.

---

### Post by utrrrongeeb on 2009-12-19
I quickly tried the WiFi again - (it has 802.11n support -- some have just g) - and it appeared to work unencrypted, but I'm not sure about WPA2 yet. It's promising, though.

It occasionally doesn't resume properly -- the screen doesn't come back on -- but sleeping it again, and resuming again, sometimes fixes this.

---

### Post by warlock43 on 2009-12-29
[FONT="Courier New"][COLOR="DarkOrange"]Ok this is starting to get annoying. I have tried a few different distros/methods and non will seem to work. When i tried the new 9.10 UNR, it gave me some error garbage and made me check a log file. The log file said that i was not an administrator when in fact, i was!
  So if anyone knows any way to get Ubuntu onto my inspiron mini, PPLLEEAASSEE seenndd help!!!!![/COLOR][/FONT]

---

### Post by warlock43 on 2009-12-29
> **utrrrongeeb said:**
> I installed Ubuntu 9.04 Jaunty on a Dell Mini 10 through Wubi, with an external CD drive. Overall I'm satisfied with its performance.

I installed netbook-remix packages


I have a post already in orange at the bottom of the page but could you give a little help on installing because i have tried many things. btw-i have windows 7

---

### Post by fwhall on 2009-12-29
> **warlock43 said:**
> [FONT=Courier New][COLOR=DarkOrange]Ok this is starting to get annoying. I have tried a few different distros/methods and non will seem to work. When i tried the new 9.10 UNR, it gave me some error garbage and made me check a log file. The log file said that i was not an administrator when in fact, i was!
  So if anyone knows any way to get Ubuntu onto my inspiron mini, PPLLEEAASSEE seenndd help!!!!![/COLOR][/FONT]

After trying several different downloads myself, (trying to get a non-existant bluetooth card to work) and shooting my wireless access in the foot by removing maximus, I re-installed 8.04.1.LTS from the DVD and all is good.  I got the resolution, wireless and by chmodding maximus to 000, I can open applications without hogging the whole screen.  My suggestion is to start all over again.

---

### Post by utrrrongeeb on 2009-12-30
In my experience, Ubuntu 9.04 "Jaunty", installed through Wubi, worked alright, once you get the proprietary graphics card drivers.

Ubuntu 9.10 "Karmic" should be avoided, because the graphics drivers aren't available for it yet.

I don't know what you netbook looks like now -- whether you've repartitioned it -- so I can't guess how best to install Ubuntu.

---

### Post by Blackthorne2 on 2009-12-30
Getting mine tomorrow and will update here with my experiences. I gave up on my Compaq TC1000 LOL!

B

---

### Post by Blackthorne2 on 2010-01-17
Well, other than not being able to get the damn built in broadcom wireless to work under 9.10 Netbook Remix, everything has been fine so far. 

I used NDISWRAPPER to get my DWA-130 D-Link USB WiFi adapter working (with WPA as well) and now I am moving along nicely.

I just gave up on Broadcom. TO much work. Thank God for ndiswrapper.

---

### Post by HarshReality on 2010-01-23
Just a thought here guys.. I noticed there are alot of 'doesnt' and 'dont' going on.. Have any of you actually tried the Restore DVD that dell provides? I have a mini 9 and 10v (came with Win 7 *ewwww*) and the DVD slams both out of the gate.. just have to run the updates.

---

### Post by mikewhatever on 2010-01-23
> **HarshReality said:**
> Just a thought here guys.. I noticed there are alot of 'doesnt' and 'dont' going on.. Have any of you actually tried the Restore DVD that dell provides? I have a mini 9 and 10v (came with Win 7 *ewwww*) and the DVD slams both out of the gate.. just have to run the updates.

Does Dell provide a restore DVD of 9.10, or any other release with gma500 driver included? If so, can you link to it, and I mean link to both, the image and the page where it says gma500 is supported.
It would have been ideal, if Dell could provide such an image, but afaik, the ones they provided so far included flash, nvidia and broadcom drivers, some codecs, all easy to install anyway, but not the driver for gma500.

---

