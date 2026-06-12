---
title: "VIA EPIA EN12000E or CN13000 support for linux?"
date: 2006-07-21
forum: Desktop Environments
---

### Post by TuxCrafter on 2006-07-21
Hello,

I have a VIA EPIA ME6000 and got it running on xubuntu 6.06 as my desktop system.

But its time to upgrade, but i am very very afraid that Linux will not work with these new systems. Because of no drivers etc.

[http://www.via.com.tw/en/products/ma...erboard_id=399](http://www.via.com.tw/en/products/ma...erboard_id=399)
[http://www.via.com.tw/en/products/ma...erboard_id=400](http://www.via.com.tw/en/products/ma...erboard_id=400)
[http://www.vntek.com/en/products/velocity/vt6122/](http://www.vntek.com/en/products/velocity/vt6122/)

[http://www.via.com.tw/en/products/mainboards/](http://www.via.com.tw/en/products/mainboards/)
Mini-ITX Series
EPIA CN

and
Mini-ITX Series
EPIA EN

It took a very long time before the old me6000 was working like it should, until the 6.06 xubuntu realize its workable but still not every ting is directly like it should. I have made kernel patches that i use before it will work optimal.. (tryed ubuntu, epiOs, Fedora Core 4 and 5 debian and xubuntu 6.06 was the best for me)

I use the systems as desktop systems for almost everything but mostly networking and programming.

How good is the new GLAN network chip. Does it still use all the cpu load when you want to download with 3 MiB's.

I know passive cooling is more expensive but its also better for the environment and (maybe most important) more silent but look at those prices and there diffrences

VIA EPIA EN12000E 1200MHz Fanless LVDS MiniITX € 195,00 exl vat
VIA EPIA CN10000E 1000MHz Fanless MiniITX € 149,00 exl vat
I can't choos between these to boards. Can anyone help me?

Is the C7 1000 MHz better and faster than the EDEN 1200 MHz? (I know the C7 CPU is more secure)
I don't use fire-wire. I do use Ethernet extensive but if it is a CPU based Ethernet 100 of 1000 LAN wont make a difference

Can any one give me info? Thank you.

---

### Post by axel-vpk on 2006-08-17
The EN12000E has the same C7 nanoBGA2 core processor as the EN15000 and the CN1300.

The EDEN brand simply means that it is fanless by default, so the only difference with the cpu is the default clock and the cooling. 

I've recently bought a 12000E board because of the c7 processor, the ridiculously low TDP (12W!), gigabit ethernet and SATA support. looking forward to make a nice HTPClight/server.

---

### Post by TuxCrafter on 2006-08-18
[http://forums.viaarena.com/categories.aspx?catid=28](http://forums.viaarena.com/categories.aspx?catid=28)

currently i am very disapointed with via. they clame everywere to have linux support but reality is sad. (they also don't give data sheets free to develop the drivers ourself)

I dont have dolby surround (i tryed the latest alsa driver and the newest kernel from kernel.org)

I dont have hotswap sata that i needed. They clame to have sata 1.0 specs (that is with hotswap) and linux support on the site of there chip)

I dont have tv out and hdtv and hdaudio can't vind support anywhere for linux.

I posted all these these things on viaarena as they via say you chould do if you want support. But no one from via helpt so far.

[http://forums.viaarena.com/categories.aspx?catid=28](http://forums.viaarena.com/categories.aspx?catid=28)

I still have to get truecript working with the padlock stuff.

I am still hope it will work soon else it is a misbuy.

---

### Post by patrickfromspain on 2006-08-18
I'm sorry to hear about problems with the VIA stuff.. So far I have an Asus mothermoard with the VIA pm890 (or something similar) and sata support and it works quite fine for my needs.

Anyway.. whats the point on those via stuff? Yes, maybe they are cheap and silent, but for even leess you could get an AMD Athlon 64 3000+ (74&#8364;) and an Asus microATX mainboard (Asus A8V-VM, 49&#8364;). that makes 123&#8364;... and is a lot more powerfull than the via stuff, plus the 3000+ is very energy efficient.

Anyway... I suppose I'm missing a point to buy some VIA stuff.

---

### Post by Salamix on 2006-08-19
An Athlon64 3000+ may be quite energy efficient compared to some other cpus out there, but the system still consumes more then 80W (idle!; with prime95 it goes up to 120W). 
My via cn1300 only consumes 17W(idle) to 23W. So this is the ideal system for a home server (the computing power is more than sufficient for this purpose). If you let the system run 24/7 you definitely notice the difference in the monthly bill you get from your local electricity company.
If you want to play games, use photoshop ... other systems are certainly the better choice. But when it comes to building small home servers, nothing beats the via cpus.

---

### Post by patrickfromspain on 2006-08-19
ok, as I said, I was missing some points of view ;)

---

### Post by kmori on 2006-08-30
> **TuxCrafter said:**
> [url]
I dont have dolby surround (i tryed the latest alsa driver and the newest kernel from kernel.org)

I have a similar system to yours except that it's got the VT1617A audio chip instead of your VT1618 audio.  I can't manage to get normal analog audio out.  I think for me it's a hardware board problem now.  I was able to get surround sound out however.

Using the default Alsa install with Dapper and the standard snd_via82xx driver I managed to hear digital audio with mplayer.  I have to, however, manually modprobe the driver at startup because it's not being autodetected at boot (this also goes for via_agp and my mouse right now).  I'm running 2.6.17 kernel as well.

It's odd though since there's nothing showing up in dmesg when I install the sound driver.

Let me know if this helps you at all.  I understand your frustration as I went from using Redhat for the last 4 years on a server running 24/7 without problems like these to now doing a full move to Ubuntu.  It's been very painful thus far.

---

### Post by TuxCrafter on 2006-08-31
Thanks for the message i now run the 2.6.17.11 kernel. I don't now what kind of motherboard you have with my en12000 xubuntu detects the sound card and all the other stuff but just don't have the correct drivers. 

I begin to think that after years of very happy use of my via epia me6000 that via is a company with a group of lying basters that tell every were on there site that they have linux support. But in reality they don't. Most drivers are made by individuals with little to no help of via. With the newest chips they don't even want to release data sheets. And there own drivers if there are some are just crap and unsafe to use. It is a real shame. Now intel is going open source and have a head start of at least a year. Via will have a hard time to catch up. Maybe the end for via and the start for Intel on the open source and mini-itx low power marked. If it happens it will be VIA own fault because there lack of open source support and there share of lying to customers.

I have more topics on via arena were i ask for help and posted a lot of info about the separate hardware issues.

---

### Post by kmori on 2006-08-31
I figure it's all part of the pain of trying to use an open-source setup with very new hardware.  I expected to spend some hours working to get this all setup but I didn't expect to spend this many.  Unforutately, I think I've spent too much time now to go back to something else.

I agree, once intel has released the ultra low power mobile cpus, it will take away most of via's business on the cpu side.  For me, I couldn't wait until then and I needed something now.  So here I am.

I keep hearing of people having success with HD MPEG2 decoding with  CPU usage <20%.  I think I'm close but I am probably going to have to modify the video driver myself.  Definitely way more effort than I originally signed up for.

Is it strictly the audio drivers you are having problems with now?  I assume you've upgraded your version of alsa?

---

### Post by TuxCrafter on 2006-08-31
I did not now you had video problems, I helpt more people with this script i wrote. it will install the openchrome drivers and dri.

I also have mpeg and < 20% cpu usage when playing dvd.(NO HD) But the general quality of the produced image is sad for something of this age.

some of the problems i can think of right now (there are more)
No dolby surround
No hot swap sata
No speed 1000 setting with ehtertool, do have T1000 autoneq
Bad CPU scalling

Please post the result of the script.
(i am building a extra part on my website with a lot of self made scripts and support)

```
#Company:	PowerCraft Technology
#Author: 	Copyright Jelle de Jong <info@powercraft.nl>
#Note:		Please send me a email if you enhanced the script
#Version:	0.0.1 (test version)
#Date:		30-08-2006
#System:	Xubuntu 6.06
#Description:	Create custom openchrome drivers from cvs
#Information:	http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code
#Comment:	script asumes that the script and makefile are located in ~/scripts/kernel/
#Command:	sudo chmod +x ~/scripts/kernel/openchrome.sh
#Command:	sudo ~/scripts/kernel/openchrome.sh

# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by the
# Free Software Foundation; either version 2, or (at your option) any
# later version.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.

#!/bin/sh

echo -n "install the necessary tools [Y/n]?"
read input
if [ "$input" != "n" ]
then
	sudo apt-get -y update
	sudo apt-get -y install subversion build-essential automake1.9 libtool pkg-config xserver-xorg-dev libxvmc-dev x11proto-gl-dev libglu1-mesa-dev x11proto-core-dev libxvmc-dev xserver-xorg-dev x11proto-gl-dev libgl1-mesa-dev cvs
	sudo apt-get -y install linux-headers-386
fi

cd ~
mkdir openchrome
cd openchrome
svn co http://svn.openchrome.org/svn/trunk
cd trunk
./autogen.sh --prefix=/usr/
configure
make
sudo make install

echo "password for anonymous is empty, just hit enter"
cvs -z3 -d:pserver:anonymous@dri.freedesktop.org:/cvs/dri login
cvs -z3 -d:pserver:anonymous@dri.freedesktop.org:/cvs/dri co drm
echo "install libdrm"
cd drm
./autogen.sh --prefix=/usr/
make
make install
echo "install kernel module"
cd linux-core
sudo make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/
sudo depmod -ae

echo -n "reconfigure xorg [Y/n]?"
read input
if [ "$input" != "n" ]
then
	sudo dpkg-reconfigure xserver-xorg
fi

#Section "Device"
#	Identifier	"Generic Video Card"
#	Driver		"via"
#	Option		"EnableAGPDMA"	"true"
#	Option		"UseFBDev"	"true"
#	Option		"PciRetry"	"true"
#	BusID		"PCI:1:0:0"
#EndSection
#
#Section "Monitor"
#	Identifier	"Generic Monitor"
#	Option		"DPMS"
#	HorizSync	28-96
#	VertRefresh	43-160
#EndSection
#
#Section "Monitor"
#	Identifier	"AL1916W"
#	Option		"DPMS"
#	Modeline 	"1440×900" 106.5 1440 1520 1672 1904 900 901 904 932 -HSync +VSync
#	HorizSync	31-84
#	VertRefresh	56-76
#EndSection
#
#Section "Screen"
#	Identifier	"Default Screen"
#	Device		"Generic Video Card"
#	Monitor		"Generic Monitor"
#	DefaultDepth	24
#	SubSection "Display"
#		Depth		16
#		Modes		"1280x1024" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth		24
#		Modes		"1280x1024" "800x600" "640x480"
#	EndSubSection
#EndSection

```

---

### Post by kmori on 2006-08-31
Not sure what you mean by CPU scaling.  Do you mean the base clock rate?  Mine's set to 100 but I am able to move it around a little and it's stable.  For the dolby issue, have you tried alsaconf?

I can play normal standard defintion MPEG2/4 clips (I'm not sure as to what the cpu usage is though).  I do know that if I try to view some of my recorded broadcast HD TV shows, it stutters like crazy.

If you have a chance, please try downloading this clip and tell me how your setup performs with Xine or Mplayer:

[http://www.eff.org/broadcastflag/LotRclip2-mpg.torrent](http://www.eff.org/broadcastflag/LotRclip2-mpg.torrent)

Today my thought is that the openchrome driver isn't setup to handle the resolution and memory clock rate.  I'll play with it more tonight if I get a chance.

I've seen the basics of your script and used it to get where I am so far.  Like I may have mentioned, the driver seems to be installed ok and DRI is available.  If I run "xine --verbose" I can see messages that indicate it's using XvMC, but I really expect better performance than what I'm seeing.

This whole business of /etc/X11/XvMCConfig doesn't seem to match what I see when I play with that file while running "strace xine".  No matter what I put in that XvMCConfig file, Xine always seems to be opening /usr/lib/libviaXvMC.so.1 even when I specify libviaXvMCPro.so.1 in the config.  Looks almost like Xine is doing it's own hardware probing and always defaulting to the non-pro driver.  To work around this I tried to link libviaXvMC to libviaXvMCPro but it gave no performance improvement.

This all leads me to believe the driver isn't even working properly for my specific hardware setup.  I have DDR2-533 memory and I've read somewhere that this can cause the driver to fail to configure properly.  All the while I thought getting faster memory would help me at some point, not.

---

### Post by TuxCrafter on 2006-09-26
The via cpu's have cpu scaling like mobile processors for powersaving. With the old C4 Samuals i could use this to overclock from 600 to 800 MHz but with the new C7 It is a bit complicated i could not get it to work.

I will download a movie with these specs and see wat happends

Audio : Dolby 2.0 
Bitrate : 448 
CodeC : AVC/H.264 
Frame Rate : 25fps 
Resolution : 1920x1088i

---

### Post by TuxCrafter on 2006-09-27
Oke downloaded a HD video and tried to test it on xubuntu with gxine and xfmedia.

It was a *.ts file

file /media/usbdisk/up_up_and_away_web2.ts
/media/usbdisk/up_up_and_away_web2.ts: MPEG transport stream data

when I trie to play it it takes my 1 GIG DDR2 with a enourmous rate that goes furter with swap and than it crash. look like a major memory leek.

I went furter and tried this command

ffplay /media/usbdisk/up_up_and_away_web2.ts -stats

```
[h264 @ 0x832b248]non existing PPS referenced
[h264 @ 0x832b248]decode_slice_header error
Input #0, mpegts, from '/media/usbdisk/up_up_and_away_web2.ts':
  Duration: 02:03:20.0, start: 68290.155689, bitrate: 11902 kb/s
  Stream #0.0[0x2ff]: Video: h264, yuv420p, 1920x1088, 50.00 fps
[h264 @ 0x832b248]concealing 5280 DC, 5280 AC, 5280 MV errors
[h264 @ 0x832b248]concealing 5280 DC, 5280 AC, 5280 MV errors
[h264 @ 0x832b248]concealing 6720 DC, 6720 AC, 6720 MV errors
68318.44 A-V:  0.000 aq=    0KB vq= 1284KB sq=    0B
```

It plays with 100% cpu load and no audio. But it plays

---

### Post by TuxCrafter on 2006-09-28
I also tested the file on my Readon 9800 Pro with Athlon XP 2800+ but it has exactly the same problems.

---

### Post by TuxCrafter on 2006-12-07
Some updates, Up to this date I still do not have all features of the chips fully suported under Linux, unlike what VIA says they do not have Linux support. Do not buy a VIA EPIA system if you want to run linux on it and expect to have the same features you had with MS Windows.

---

### Post by TuxCrafter on 2006-12-25
Update - I am now using kernel Linux 2.6.19.1 and there is still no dolby and other problems also still exists.

---

### Post by TuxCrafter on 2007-02-21
Update: Don't buy via if you want to have full Linux support on it!

Links:
[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=73445&highlight_key=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=73445&highlight_key=y)

[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=73558&highlight_key=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=73558&highlight_key=y)

[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=73557&highlight_key=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=73557&highlight_key=y)

[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=73235&highlight_key=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=73235&highlight_key=y)

---

### Post by MockY on 2007-09-11
Since its been a while now and Gutsy Gibbon is about to be released, has this Linux support for VIA boards changed?

I'm about to build me a nice and silent little Mythbox with Epia ME 6000. Is that a bad idea. Should I go with another board (newer or older) made by VIA or go with another brand Mini-ITX board?

---

### Post by TuxCrafter on 2007-09-12
Linux support has not been changed significantly, only there close source drivers systems has received some polishing, but this is not very useful for the open source minded.

The VIA Epia ME6000 is a older type of mini-itx motherboard, I had one in the past. Video support will not change, there is hope for smart 5.1 Dolby support, don't know for sure how there support is now. Think that you have to do some physical testing.

---

### Post by nebbe on 2007-09-22
TuxCrafter, what machine do u reccomend? If i was to build a media-computer that is.. Think i need  EPIA of some kind since im building it inside a nes-8bits console.

thx.

---

### Post by TuxCrafter on 2007-09-22
> **nebbe said:**
> TuxCrafter, what machine do u recommend? If i was to build a media-computer that is.. Think i need  EPIA of some kind since im building it inside a nes-8bits console.

I don't know the size of a nes-8bit console. But a summing you need a mini-itx motherboard of 17x17cm. I have the following recommendation:

If you want to be sure it works nice under linux buy a sytem that has standard open source device drivers like the new intel chipsets.
The below is a cheap intel based motherboard.
The Jetway J9F2
You still have to buy a expensive intel cpu for this board. And you have to make a good choice between, power consuming, speed, features and heat.

If you want to take a big gamble , and hope that the openchrome driver project continues there good development and will be able to support all the chipsets features in the future I would recommend the bellow motherboard.
VIA EPIA-EX10000EG

However, If you have little time for troubleshooting, buy expensive intel stuff. The hardware will not be better bye definition but the device drivers currently do. :sad:

Good luck with your system choice

---

### Post by nebbe on 2007-09-22
Thx for such a fast answer.

I will look into Jetways and compare them with EPIA. And no, i dont wanna spend a fortune on this project, but still,.. one woudlnt like to end up with a system and not beeing able to use all hardware due to lack of driver-support etc.

Thx for your tip, i will plan this trough carefully before i make a move. 
Cheers!

---

### Post by Electric Boogaloo on 2007-10-01
nebbe,  I've just completed the same project!  I put a CN13000 inside a NES case along with a 80W Morex power supply and an 80GB SATA laptop hard disk.  It all came together and fits quite nicely, with enough room to easily add a cd-rom later.  

I haven't yet attempted to install the openchrome drivers, it's a bit intimidating because I am very new to Linux.  However, I'll post here if I uncover any enlightening information.  :)

---

### Post by TuxCrafter on 2007-10-24
> **Electric Boogaloo said:**
> nebbe,  I've just completed the same project!  I put a CN13000 inside a NES case along with a 80W Morex power supply and an 80GB SATA laptop hard disk.  It all came together and fits quite nicely, with enough room to easily add a cd-rom later.  

I haven't yet attempted to install the openchrome drivers, it's a bit intimidating because I am very new to Linux.  However, I'll post here if I uncover any enlightening information.  :)

[http://ubuntuforums.org/showthread.php?p=3619455](http://ubuntuforums.org/showthread.php?p=3619455)

That link should do the trick :-p

---

### Post by Lem on 2007-11-15
The J9F2 runs sweet with Ubuntu - smooth compiz out of the box and with a modest cpu will play HD content quite happily (even when you've set totem-xine to xshm video playback, so you can wobble your videos!)

---

### Post by TuxCrafter on 2007-11-15
> **Lem said:**
> The J9F2 runs sweet with Ubuntu - smooth compiz out of the box and with a modest cpu will play HD content quite happily (even when you've set totem-xine to xshm video playback, so you can wobble your videos!)



That's nice to hear. But the [Jetway J9F2 Extreme Core2Duo]("http://www.picco.nl/product_info.php?cPath=37_180&products_id=2535") is not a via chipset based system it is a Intel based system so its obvious it will run great out of the box. The price is also 300% of that of a via system :-D so not a very good comparison. (it is a very nice system thought)

I am waiting until the J7F5M1G2E-VDE is available in the Netherlands and will test it.

---

### Post by Lem on 2007-11-15
You can get the VIA stuff running reasonably ok in ubuntu with the openchrome drivers, but it's not fantastic. For a cheap and cheerful setup, I'd be tempted by the Intel D201GLY although I'm not 100% sure about support for the SiS Mirage VGA chipset.

---

