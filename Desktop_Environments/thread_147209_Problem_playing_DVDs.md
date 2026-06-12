---
title: "Problem playing DVDs"
date: 2006-03-19
forum: Desktop Environments
---

### Post by reuben on 2006-03-19
Hello,

I'm having problems playing DVDs under kaffeine or xine; I get this output on the cli, and then the player freezes. What gives?
...
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00055c41
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00062413
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0006244c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x000782f3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0007832c
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x0007832c)!!
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0007a403
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0007a43c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0007bc03
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0007bc3c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x0007c36b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0007c3a4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x0031ac7e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x0031acb7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x0031aea6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x0031aedf
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_13_1.VOB (0x0031aedf)!!
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x0031b685
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x0031b6be
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_14_1.VOB (0x0031b6be)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x0031c555
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x0031c58e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x0032563e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x00325677

---

### Post by tuxcantfly on 2006-03-19
do you have libdvdcss2? you can get it from the vlc site:

[ftp://ftp.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](ftp://ftp.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb)

also, you might want to try using vlc instead of kaffeine; it works better for me:

sudo apt-get install vlc

---

### Post by reuben on 2006-03-19
Yeah, I have libdvdcss.

Vlc does very similar:


 [00000913] access_file access error: file /dev/hdc is empty, aborting
[00000913] cdda access error: could not read TOCHDR
[00000913] cdda access error: no audio tracks found
[00000911] main input error: no suitable access module for `dvd:///dev/hdc'
[00000915] dvdread demuxer error: DVDRead cannot open source: /dev/hdc
[00000916] vcd access error: could not read TOCHDR
[00000916] vcd access error: no movie tracks found
[00000916] access_file access error: file /dev/hdc is empty, aborting
[00000916] cdda access error: could not read TOCHDR
[00000916] cdda access error: no audio tracks found
[00000914] main input error: no suitable access module for `dvd:///dev/hdc'
[00000918] dvdread demuxer error: DVDRead cannot open source: /dev/hdc
[00000919] vcd access error: could not read TOCHDR
[00000919] vcd access error: no movie tracks found
[00000919] access_file access error: file /dev/hdc is empty, aborting
[00000919] cdda access error: could not read TOCHDR
[00000919] cdda access error: no audio tracks found
[00000917] main input error: no suitable access module for `dvd:///dev/hdc'
[00000921] dvdread demuxer error: DVDRead cannot open source: /dev/hdc
[00000922] vcd access error: could not read TOCHDR
[00000922] vcd access error: no movie tracks found
[00000922] access_file access error: file /dev/hdc is empty, aborting
[00000922] cdda access error: could not read TOCHDR
[00000922] cdda access error: no audio tracks found
[00000920] main input error: no suitable access module for `dvd:///dev/hdc'
[00000924] dvdread demuxer error: DVDRead cannot open source: /dev/hdc
[00000925] vcd access error: could not read TOCHDR
[00000925] vcd access error: no movie tracks found
[00000925] access_file access error: file /dev/hdc is empty, aborting
[00000925] cdda access error: could not read TOCHDR
[00000925] cdda access error: no audio tracks found
[00000923] main input error: no suitable access module for `dvd:///dev/hdc'
[00000262] main playlist: stopping playback

---

### Post by reuben on 2006-03-21
bump

---

### Post by beijingjj on 2006-03-22
I personally have never gotten DVDs to play under and distro of linux no matter how hard I've tried.  Has anyone actually ever succeeded?  Does it play normally in full screen mode without any glitches?  I'd like to be able to do that.

---

### Post by enfield on 2006-03-28
Yes, I can play DVD's full-screen with Totem on Breezy 5.10.  I've also been able to do it previously on FC4 using Kaffeine.

But that doesn't help with Reuben's problem.

---

### Post by tuxcantfly on 2006-04-09
just use ogle. It's a dedicated dvd player, and it always works. to install it, use

sudo apt-get install ogle-gui

---

### Post by keenwerkz on 2006-04-10
@beijingjj-

i do have succeded in playing dvds on the following ubuntu's: kubuntu 5.04, ubuntu 5.04, ubuntu 5.10 and ubuntu 6.04...

imho kubuntu 5.04 is the easiest to setup for me in terms of multimedia playback since the downloads/uipdates needed are only a few files. (libdvdcss, and etc and kaffeine provides instructions)

for 5.10 and 6.04 i used the instructions in [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) although you have to check for file dependencies if you download manually like i do and not w/ apt-get.

but now im using ubuntu 5.10 since i need gimp and oo 2, w/c arent available in kubuntu 5.04, although i like kubuntu 5.10 but there is a problem w/ mounting my fat usb drives (kde error) and i cant download the upgrade since im not online at home.

---

### Post by reuben on 2006-04-10
tuxcantfly - ogle succeeds even less than mplayer or vlc.

OTOH I can backup dvds, and I can play video full screen. It's very strange that I haven't been able to play any, yet.

---

### Post by anasofiapaixao on 2006-08-18
Funny enough no one in any forum have considered this... I tell you why it doesn't work: some cd drives can be 'fooled', others just don't. That's what happens, for example, with my matshita uj-831s. I have the displeasure of having two of these, and trust me I only have done this mistake a second time because I had no choice over such an uncommon computer as THE GODDMNED tecra M4.

I had this problem while I was still using Windoze and for problematic drives like this one, there is nothing you can do - no programs, no firmware flashing (because there is none, even official - the ones available for my model, at least, are for old builds that can't be used), no nothing. Sorry that it has to be me giving the awful news, but I know the feeling and my best advice is try not to smash your drive into little, cracked, pulverized pieces as we all would like to do because it is a loss of money.

The uj-831s at least just sucks. It sucks, it sucks, it sucks, period. Why? Because besides this I had to throw away 20 legitimate, bought in fnac CD-Rs because it would refuse to write on them. I don't want a XPTO drive with serious compatibilty issues. I am NOT buying electronics from panasonic so soon, and I just hope this gets read by as many people as possible.

Sorry if I may be sounding harsh, but it is just that I get so mad because region encoding is just the MOST STUPID MEASURE EVER TAKEN and just blocks the pursue of free market.

Back on topic and in a nutshell: some drives, I don't know how or why, have better protection, and you can't do anyhting out of them regardless of Operating System. And the last time I've searched for anything UJ-831S related was months ago, and things haven't changed.

---

### Post by zoryn on 2006-08-20
I can't play dvds in totem-xine, even with libdvdcss. Odd enough, I can with vlc.. go figure..

/offtopic
anasofiapaixao, good to see girls knowing about and using ubuntu, even better when they're from my country! ;)

---

