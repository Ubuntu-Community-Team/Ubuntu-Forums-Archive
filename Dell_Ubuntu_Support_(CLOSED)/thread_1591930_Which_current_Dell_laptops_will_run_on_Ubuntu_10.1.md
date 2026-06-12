---
title: "Which current Dell laptops will run on Ubuntu 10.10?"
date: 2010-10-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jonolumb on 2010-10-10
Hi. 

My old Dell laptop is coming to the end of it's days and I was wondering which of the laptops currently on the Dell website will run on Ubuntu 10.10 with full hardware support. It doesn't have to be anything expensive or flashy - I just need full wireless, sound and graphics support out of the box.

Any thoughts or guidance would be much appreciated

Thanks

---

### Post by Gogl on 2010-10-10
I'm using a Studio XPS 16 (1645) with the 10.10 RC. Everything works out of the box except the wireless. But after the install it gives me 2 choices for wireless drivers. The proprietary drivers work just perfect.
The only problem may be the price.

---

### Post by mikewhatever on 2010-10-10
Dell doesn't offer 10.10 according to [dell.com]("http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs"), and personally,  doubt it will.

PS: I hope you are planing to run 10.10 on a laptop and not vise verse.;)

---

### Post by chrisplymouth on 2010-10-10
Does the 3D ATI open source graphics driver work though?

Install Google Earth and check out the result! 

100% guarantee it doesn't!

---

### Post by jonolumb on 2010-10-11
> **Gogl said:**
> I'm using a Studio XPS 16 (1645) with the 10.10 RC. Everything works out of the box except the wireless. But after the install it gives me 2 choices for wireless drivers. The proprietary drivers work just perfect.
The only problem may be the price.

Thanks for the recommendation - but that's probably slightly outside my price range. I don't need flashy graphics or a particularly fast processor. This laptop is mainly to be used for surfing the web, watching films, viewing photos and word processing. Does anybody know if the **Inspiron 15** laptops that Dell sell work Ok? They run the following hardware:

Wireless:
DellTM  Wireless 1501 802.11b/g Half Mini Card (optional)
Atheros Wireless-N 802.11n Mini-Card (standard)

Graphics:
Integrated GMA 4500 MHD

I presume that sound card compatibility isn't normally an issue?

Thanks

---

### Post by Jimtheplanner on 2010-10-11
Hi Folks I use a 1545 (64 bit) my only problem is the hard drive runs very hot indeed with 10.10 and previously with 10.04. It will average 50/52 Deg C. If I use Mandriva on the same set up I get an average 40/42 Deg C.... WD my hard drive maker recommends a max of 60 Deg C.

Apart from that all works well.

Jim

---

### Post by undfined on 2010-10-11
> **jonolumb said:**
> Hi. 

My old Dell laptop is coming to the end of it's days and I was wondering which of the laptops currently on the Dell website will run on Ubuntu 10.10 with full hardware support. It doesn't have to be anything expensive or flashy - I just need full wireless, sound and graphics support out of the box.

Any thoughts or guidance would be much appreciated

Thanks

The Inspiron 15n is similar to the 15 and should work out of the box, with the exception of activating a few recognized drivers.

[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)

---

### Post by CoolJohnB on 2010-10-11
I have a Vostro 3700 works flawlessly with 10.10 Google Earth works great, no problems

---

### Post by jonolumb on 2010-10-11
> **undfined said:**
> The Inspiron 15n is similar to the 15 and should work out of the box, with the exception of activating a few recognized drivers.

[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)

It looks like the Dell Inspiron 15 might be my best bet then? The System76 laptops would be a nice option but I'm in the UK and they seem to be based in the USA.

---

### Post by hkphooey on 2010-10-12
As a general comment, you're more likely to have success if you choose 'last year's model' rather than one that's just come out. Hardware support seems to be better for the older models, as support for wireless, sound etc makes its way into the kernel, and drivers are updated. 

Case in point: my two year old Vostro 1400 started out with some sound card problems and occasionaly wireless flakiness, but over the first year these stabilized and now it works fine. 

Also, of course, do your research online. Pick the model you'd like to buy and then search for the modelname and Ubuntu in google and in these forums to see if people are having problems. Also Dell have a forum I think.

---

### Post by hkphooey on 2010-10-12
> **jonolumb said:**
> 
I presume that sound card compatibility isn't normally an issue?


Can be. Dell takes standard Taiwan chips but then reprograms them to suit the hardware. Eg my Vostro 1400 has two front headphone jacks, one front Mic jack, internal mic at top of screen, and internal speakers. I've never got the front mic working successfully, but the screen mic is good enough for my purposes, so I haven't been too bothered by it. 

The alsa module has special Dell switches, which you can add to your modprobe config files in fact. So yes, that indicates that sound can be an issue.

---

### Post by UncleAelfrich on 2010-11-22
My Vostro 3700 works fine on 10.10. There were problems on 10.04. But it works really nice. I even use two monitors with it. I would recommend the i5 rather than the i3 processor if you want to run vmware player with windows 7 inside it. with my i3, it can be slow sometimes with vmware player.

---

### Post by krunalpatel on 2010-11-22
I installed Ubuntu an a really old Dell Inspiron 8200. Works great

---

### Post by gibbylinks on 2010-11-22
No Problems here.

---

### Post by lastguy on 2010-11-22
D620, E4310 ok, E5410 not ok.

---

### Post by wprecht on 2010-11-22
m6400 runs great.

---

### Post by Megaptera on 2010-11-22
Running fine 10.10 desktop edition on Dell Inspiron 1545 - no temperature issues, 32 bit.

---

### Post by jnguyen on 2010-11-22
D630 & D830 works great here.

---

### Post by waynefoutz on 2010-11-23
> **chrisplymouth said:**
> Does the 3D ATI open source graphics driver work though?

Install Google Earth and check out the result! 

100% guarantee it doesn't!

it didn't on mine until about a week ago. I have a Dell D531 with an older ATI Mobility Radeon X1270. I'm running 10.04 Lucid. I added this ppa to my sources:

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")


They are constantly working on the open source drivers and this PPA will give you the latest drivers. 

With Google earth,  I  had to add "enableTips=false" into [General] section in ~/.config/Google/GoogleEarthPlus.conf

Once I did that, it runs more than perfect. 

I fled Ubuntu after 9.10 came out and broke my video, and would only allow me to run the open source drivers. They were awful. So I formatted and decided to run Debian Lenny from then on. I just recently put Ubuntu back on this laptop, the open source drivers are officially up to snuff, in my opinion. My only complaints are the game Urban Terror has lousy framerates for some reason. I'm getting great results in everything else. And then there is flash and compiz. I'm not a compiz guy, the effects are impressive, but I've always run with them turned off. Flash, for what ever reason is flaky with desktop effects turned off, but runs flawlessly with them on. This makes no sense to me, but now I'm running compiz.

---

### Post by hkphooey on 2010-11-23
Just in case it helps, there is a Dell-specific forum here. 
  [http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

I was looking around to see if there was a sort of Hardware Compatibility list, like we seem to have compiled above, but it seems not. I'll alert the Dell forum to this thread as well.

---

### Post by CoolJohnB on 2010-11-24
I have a Vostro 3700 and a Vostro 1700 both work really well with Ubuntu, in fact I would say it is far superior to Windows.

---

### Post by Sobster on 2010-11-24
I running it on a Dell XPS 1530 with windows Vista. I boot ubuntu 10.10 with a external hard drive. It was a pain installing, but thats because im sota new at linux and ubuntu. But it dose run great. It might run even better if i new what i was doing o.O :lolflag:

---

### Post by KegHead on 2010-11-24
Hi!

Two of my machines are Dells:

1. Mini 9

2. B-130

Both run 10.10 w/no problems.


KegHead

---

### Post by NEMECOM on 2010-11-24
I use my Dell Latitude D620. Works perfectly fine had to activate wireless drivers, but after that its going strong using 64 bit 10.10.

---

### Post by kamohammed on 2010-11-26
Dell studio 1535... works perfectly...
fresh install of 10.10 catered for all my drivers...
Just had to update the Graphics drivers (ATi Radeon HD 3450) from ATi site.

---

### Post by jeepinpete on 2010-11-28
I am running a Studio 1749, just about a year old now.  AMD 4650 video card.  10.10 is working quite nicely, and Google Earth runs no problems.

---

### Post by dredavis on 2010-11-29
So far so good for me I actually have Ubuntu 10.10 installed on my Dell Latitude e6500 and my Dell Optiplex GX520.  I have not seen any real problems with the OS.  I installed openSUSE on my Dell Inspiron 5100 and it was a little problematic at first but is running pretty smooth. Just trying to get to the point where both my Dell Ubuntu PC's work in sync with my Asus Win7 PC that is about the only thing I have not mastered but considering I am new to Linux I actually find Ubuntu very clean and easy.  Contrary to what I heard coming in the door about how ugly Linux OS's are Ubuntu is actually really well designed and flows pretty good, PC responds well to it.

---

### Post by jwaclawsky on 2010-12-02
I have 10.10 running on my Vostro 1014 (had to fix a speaker/microphone problem when I first installed 10.10), and I have 10.10 my Dell studio XPS. I also have 10.04 running on my Dell mini 9. Everything is working in all my machines. Ubuntu rocks IMHO!!!

---

### Post by pasdechance on 2010-12-03
good day ubuntu peeps.
my lady just bought herself a _dell 1546_, which i guess falls into the 15n category. everything works out of the box except wifi and usb support.
wifi was easy enough to fix, she didn't even ask me for help, but the usb has been posing a problem for the past few days.
i've been through forums for ubuntu and other distros and tried all of the options that have been presented, fiddled with the BIOS to no avail and gotten pretty fed up.

anyone else ever had this problem with a dell? the thing doesn't even detect a usb device: no mention in lsusb, dmesg, etc, etc. we've even tried different options in the grub config files.

(i know this thread isn't for questions, but ubuntu users are generally nice folks so when they tell me to take a walk, they'll do it nicely)

---

### Post by Dlambert on 2010-12-03
Im using the inspiron 1545. Everything works just fine:D.

---

### Post by jwaclawsky on 2010-12-04
> **pasdechance said:**
> good day ubuntu peeps.
my lady just bought herself a _dell 1546_, which i guess falls into the 15n category. everything works out of the box except wifi and usb support.
wifi was easy enough to fix, she didn't even ask me for help, but the usb has been posing a problem for the past few days.
i've been through forums for ubuntu and other distros and tried all of the options that have been presented, fiddled with the BIOS to no avail and gotten pretty fed up.

anyone else ever had this problem with a dell? the thing doesn't even detect a usb device: no mention in lsusb, dmesg, etc, etc. we've even tried different options in the grub config files.

(i know this thread isn't for questions, but ubuntu users are generally nice folks so when they tell me to take a walk, they'll do it nicely)

I have three Dells and never had any problems with USB. I consider USB to be "solid". I would do a new install, if it was my machine (just to make sure something funny didn't happen earlier). In any event you should post a separate question to the forum. Your post is some what obscure in a long post that really isn't about this kind of problem. My 2 cents.

---

### Post by stratosvoukel on 2010-12-04
Guys, I just bought a N5010 Inspiron and almost everything has problems. The touchpad isnt working properly (putting two fingers makes the cursor go crazy and I cant scroll or do anything multitouch), the temperature sometimes goes very high even though the laptop is idle , and since yesterday I cant any sound from the headphones line out. I even tried reinstalling but nothing changed (even the sound problems that used to be fine is still here, which is really weird).

---

### Post by areteichi on 2010-12-12
You might find this website helpful:
[http://webapps.ubuntu.com/certification/make/Dell/laptops/](http://webapps.ubuntu.com/certification/make/Dell/laptops/)

---

### Post by nm_geo on 2010-12-14
Have a Dell D620 here picked up for about $300.00 and I am running XP Pro and three Ubuntu flavors. Well I am testing Natty 11.04 and I would not say it is running, but it is not the computer is just the Alpha 1 version of Ubuntu.

---

### Post by cub on 2011-01-13
> **lastguy said:**
> E4310 ok
It depends on what your definition of "ok" is. As many others I have issues with connecting external monitors and docking/un-docking. Same issue in 10.04 but was said in some threads it would be fixed with 10.10 and newer kernel. However, after upgrading today the docking issue is still there. Other than that it works ok.

---

### Post by timbelish on 2011-01-13
> **hkphooey said:**
> As a general comment, you're more likely to have success if you choose 'last year's model' rather than one that's just come out. Hardware support seems to be better for the older models, as support for wireless, sound etc makes its way into the kernel, and drivers are updated. 

Case in point: my two year old Vostro 1400 started out with some sound card problems and occasionaly wireless flakiness, but over the first year these stabilized and now it works fine. 

Also, of course, do your research online. Pick the model you'd like to buy and then search for the modelname and Ubuntu in google and in these forums to see if people are having problems. Also Dell have a forum I think.
hi everybody i used ubuntu 10.10 notebooke in my laptop dell studio 1555 but after i installed it is too slow how can i make it fast, if it not compatible with dell 1555 studio 32 bit some one please help me as soon as possible 
thanks

---

### Post by mjulius on 2011-01-13
I am running 10.10 on an old Dell Latitude D610 with Compiz enabled. Everything runs perfect, even google earth :)

---

