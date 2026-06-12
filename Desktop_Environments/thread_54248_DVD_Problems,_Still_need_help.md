---
title: "DVD Problems, Still need help"
date: 2005-08-04
forum: Desktop Environments
---

### Post by jlacroix on 2005-08-04
I'm pretty sure that Ubuntu cannot play video dvd's, due to the incredibly large number of problems I am having with it, and the fact that none of my friends can play DVD's either, but I am going to give it one last shot before I switch to another distro. (I love Ubuntu, but if it can't play DVD's, then I have no choice). Please understand my frustration, I must've been trying to get this working for a month, asking in forums and searching google. Nothing works.

Here is what I have done to get it working:

1. I installed libdvdcss2, libdvdread, basically everything that so much as has the word "DVD" in it.

2. In turned on DMA, but I have to do this every single time I login with hdparm, because adding it to the end of that file (forgot the name of the file in question) makes my computer say "/dev/hdc no such file or directory" when it boots so I have to do it manually every time in Konsole.

Anyway, I tried Mplayer, Xine, Totem, Totem-xine, and VLC and they all have the same problem. The dvd will play for quite some time and then crash out. Some dvd's don't make it passed the intro screen, some will last an hour into the movie and fail out.

Xine gives me this error:
"the source can't be read. maybe you don't have enough rights for this, or source doesn't contain data" That's the error it gives me when it crashes out. For example, I tried playing Spiderman 2 and when selecting a scene I get that immediately. With Dragonball GT, I can play an episode all the way through but it will fail if I let it go by itself. (If that makes sense).

Mplayer:
MPlayer crashes instananeously with signal 11. Mplayer will play all video files fine (even wmv files) but not dvd's.

Vlc:
I forgot what it does, but that player is worthless to me anyway.

Totem-xine:
Crashes at the same points as Xine, but says something about trying to play a dvd without libdvdcss (Although lbdvdcss is installed, and I even tried reinstalling it).

I went through the unofficial ubuntu guide several times and searched google and nothing helps. For the heck of it, I changed the jumpers on my dvd drive so that it is set to master, but still nothing.

When I open Xine in a terminal, here is the output all the way from when I start playing it to when it crashes. In this example I played Spiderman 2, I chose scen 38 in scene selection, and then it crashed.

```

This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
libdvdread: Using libdvdcss version 1.2.8 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000200
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00001680
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00012968
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002e2940
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002e2960
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e3c20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e3c40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0030a5e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0030a600
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0031c480
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0031c4a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0033f480
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0033f4a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00343d80
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00343da0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0034fb20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0034fb40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0035e700
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0035e720
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x00368320
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x00368340
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00374780
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003747a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003810a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003810c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x00387c40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x00387c60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x00395b60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x00395b80
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003983c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003983e0
libdvdread: Elapsed time 0
libdvdread: Found 15 VTS's
libdvdread: Elapsed time 0
jeremy@Athlon:~$   

```

PLEASE someone help.

---

### Post by mrcbrown on 2005-08-04
[QUOTE=jlacroix]
PLEASE someone help.[/QUOTE]
 Try Ogle (gnome) or Okle (kde) - thats pretty much the only DVD app I'll use out there - any distro I have used in the last 3 years its the player I have picked, always seems to run smooth.

---

### Post by cjazz on 2005-08-04
[QUOTE=jlacroix]I'm pretty sure that Ubuntu cannot play video dvd's, due to the incredibly large number of problems I am having with it, and the fact that none of my friends can play DVD's either, but I am going to give it one last shot before I switch to another distro.


Wish I could help. I do have to say, though, that whatever your problem is, your conclusion about Ubuntu appears to be wrong. I installed Ubuntu the other day (after about two and a half years of Debian). I never watch DVDs on my computer, but after seeing your post, I popped "Lord of the Rings: Fellowship of the Ring" into the DVD drive. Gnome detected it right away, automatically brought up Totem and played the entire movie without a problem (except play seemed a little jerky). Just FYI, my hardware is a Dell Dimension 2400 with a PCI NVidia GeForce2 and a SONY DVD-ROM drive. As I said, it's a fresh Ubuntu install, with multimedia codecs and DVD support applied per instructions from the Unofficial Ubuntu Starter Guide.

Good luck.

---

### Post by Chuckaluphagus on 2005-08-05
I don't know what is causing your problem, but it isn't an Ubuntu-wide issue; I installed libdvdcss2 and changed my DMA settings by following the instructions in the Ubuntu Guide:

[http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)
[http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom)

and installed totem-xine through Synaptic, and after that DVDs play perfectly.  I didn't install any other DVD-related software at all.  

Whatever the cause of the problem on your system, it's not a generic Ubuntu problem; there should be a fix somewhere.  Good luck.

---

### Post by iH8forcedRegistration on 2005-08-05
After watching Monty Python's The Holy Grail in its entirety, I can concur with the previous people who have said DVD playback can work under ubuntu.

If this is a hardware thing, I might be able to be more helpful than that if I had slightly more information.

Run ```
xine-check
``` once from a terminal, and let me know if any of the lines it outputs say anything other than "good"

Also, let it play a DVD once until it crashes, then immediately after the crash, run ```
dmesg
``` from a terminal, and paste the last 10 or so lines of output to the forum.

---

### Post by jlacroix on 2005-08-05
xine-check says good on everything. I tried Ogle too and no luck. Those of you that said that you were watching dvd's, you probably only played part of it. My system detects and plays dvds just fine, they just crash after a while. Some crash instantly, like Garfield The Movie. Those of you that have that movie, try that one. It won't even make it to the menu.

Here is DMESG output after Spiderman 2 crashes:
> 

/O error, dev hdc, sector 7203032
Buffer I/O error on device hdc, logical block 900379
Inbound IN=eth0 OUT= MAC=00:05:5d:36:c2:6e:00:30:bd:c8:2a:3a:08:00 SRC=203.173.57.21 DST=192.168.2.62 LEN=65 TOS=0x00 PREC=0x00 TTL=42 ID=3402 PROTO=UDP SPT=6881 DPT=6881 LEN=45
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203040
Buffer I/O error on device hdc, logical block 900380
Inbound IN=eth0 OUT= MAC=00:05:5d:36:c2:6e:00:30:bd:c8:2a:3a:08:00 SRC=24.4.178.83 DST=192.168.2.62 LEN=86 TOS=0x00 PREC=0x00 TTL=116 ID=42818 PROTO=UDP SPT=6881 DPT=6881 LEN=66
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203048
Buffer I/O error on device hdc, logical block 900381
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203056
Buffer I/O error on device hdc, logical block 900382
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203064
Buffer I/O error on device hdc, logical block 900383
Inbound IN=eth0 OUT= MAC=00:05:5d:36:c2:6e:00:30:bd:c8:2a:3a:08:00 SRC=81.218.43.166 DST=192.168.2.62 LEN=65 TOS=0x00 PREC=0x00 TTL=108 ID=10876 PROTO=UDP SPT=55555 DPT=6881 LEN=45
Inbound IN=eth0 OUT= MAC=00:05:5d:36:c2:6e:00:30:bd:c8:2a:3a:08:00 SRC=203.173.57.21 DST=192.168.2.62 LEN=86 TOS=0x00 PREC=0x00 TTL=42 ID=3639 PROTO=UDP SPT=6881 DPT=6881 LEN=66
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203072
Buffer I/O error on device hdc, logical block 900384
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203080
Buffer I/O error on device hdc, logical block 900385
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203088
Buffer I/O error on device hdc, logical block 900386
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203096
Buffer I/O error on device hdc, logical block 900387
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203104
Buffer I/O error on device hdc, logical block 900388
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203112
Buffer I/O error on device hdc, logical block 900389
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203120
Buffer I/O error on device hdc, logical block 900390
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203128
Buffer I/O error on device hdc, logical block 900391
Inbound IN=eth0 OUT= MAC=00:05:5d:36:c2:6e:00:30:bd:c8:2a:3a:08:00 SRC=203.173.57.21 DST=192.168.2.62 LEN=65 TOS=0x00 PREC=0x00 TTL=42 ID=4119 PROTO=UDP SPT=6881 DPT=6881 LEN=45
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203136
Buffer I/O error on device hdc, logical block 900392
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203144
Buffer I/O error on device hdc, logical block 900393
Inbound IN=eth0 OUT= MAC= SRC=192.168.2.62 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7365304
Buffer I/O error on device hdc, logical block 920663
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7365304
Buffer I/O error on device hdc, logical block 920663
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'GARFIELDTHEMOVIE', timestamp 2004/07/29 15:01 (1f10)
Inbound IN=eth0 OUT= MAC=00:05:5d:36:c2:6e:00:30:bd:c8:2a:3a:08:00 SRC=203.173.57.21 DST=192.168.2.62 LEN=86 TOS=0x00 PREC=0x00 TTL=42 ID=5079 PROTO=UDP SPT=6881 DPT=6881 LEN=66
Inbound IN=eth0 OUT= MAC=00:05:5d:36:c2:6e:00:30:bd:c8:2a:3a:08:00 SRC=81.191.180.125 DST=192.168.2.62 LEN=86 TOS=0x00 PREC=0x00 TTL=118 ID=61803 PROTO=UDP SPT=6881 DPT=6881 LEN=66
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7201144
Buffer I/O error on device hdc, logical block 900143
Inbound IN=eth0 OUT= MAC= SRC=192.168.2.62 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7201152
Buffer I/O error on device hdc, logical block 900144
Inbound IN=eth0 OUT= MAC=00:05:5d:36:c2:6e:00:30:bd:c8:2a:3a:08:00 SRC=203.173.57.21 DST=192.168.2.62 LEN=65 TOS=0x00 PREC=0x00 TTL=42 ID=5543 PROTO=UDP SPT=6881 DPT=6881 LEN=45
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7201160
Buffer I/O error on device hdc, logical block 900145
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7202856
Buffer I/O error on device hdc, logical block 900357
Inbound IN=eth0 OUT= MAC=00:05:5d:36:c2:6e:00:30:bd:c8:2a:3a:08:00 SRC=203.173.57.21 DST=192.168.2.62 LEN=86 TOS=0x00 PREC=0x00 TTL=42 ID=5718 PROTO=UDP SPT=6881 DPT=6881 LEN=66
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7202864
Buffer I/O error on device hdc, logical block 900358
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7202872
Buffer I/O error on device hdc, logical block 900359
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7202880
Buffer I/O error on device hdc, logical block 900360
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7202888
Buffer I/O error on device hdc, logical block 900361
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7202896
Buffer I/O error on device hdc, logical block 900362
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7202904
Buffer I/O error on device hdc, logical block 900363
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7202912
Buffer I/O error on device hdc, logical block 900364
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7202920
Buffer I/O error on device hdc, logical block 900365
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7202928
Buffer I/O error on device hdc, logical block 900366
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7202984
Buffer I/O error on device hdc, logical block 900373
Inbound IN=eth0 OUT= MAC= SRC=192.168.2.62 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7202992
Buffer I/O error on device hdc, logical block 900374
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203000
Buffer I/O error on device hdc, logical block 900375
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203008
Buffer I/O error on device hdc, logical block 900376
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203016
Buffer I/O error on device hdc, logical block 900377
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203024
Buffer I/O error on device hdc, logical block 900378
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203032
Buffer I/O error on device hdc, logical block 900379
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203040
Buffer I/O error on device hdc, logical block 900380
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203048
Buffer I/O error on device hdc, logical block 900381
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203056
Buffer I/O error on device hdc, logical block 900382
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203064
Buffer I/O error on device hdc, logical block 900383
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203072
Buffer I/O error on device hdc, logical block 900384
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203080
Buffer I/O error on device hdc, logical block 900385
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203088
Buffer I/O error on device hdc, logical block 900386
Inbound IN=eth0 OUT= MAC= SRC=192.168.2.62 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203096
Buffer I/O error on device hdc, logical block 900387
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203104
Buffer I/O error on device hdc, logical block 900388
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203112
Buffer I/O error on device hdc, logical block 900389
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203120
Buffer I/O error on device hdc, logical block 900390
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203128
Buffer I/O error on device hdc, logical block 900391
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203136
Buffer I/O error on device hdc, logical block 900392
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 7203144
Buffer I/O error on device hdc, logical block 900393
Inbound IN=eth0 OUT= MAC= SRC=192.168.2.62 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
Inbound IN=eth0 OUT= MAC= SRC=192.168.2.62 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
Inbound IN=eth0 OUT= MAC= SRC=192.168.2.62 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
Inbound IN=eth0 OUT= MAC= SRC=192.168.2.62 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
Inbound IN=eth0 OUT= MAC= SRC=192.168.2.62 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
Inbound IN=eth0 OUT= MAC= SRC=192.168.2.62 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
jeremy@Athlon:~$ 

---

### Post by coolclassic on 2005-08-05
As you are having so many problems with various dvd's and that playing dvd's in ubuntu is relatively easy I would hazard a guess that there might be a problem with your dvd player. Is there any way that you can check your dvd player in another machine.

---

### Post by Lord Illidan on 2005-08-05
And are your dvds in pristine condition? No scratches or anything?

---

### Post by ssck on 2005-08-05
[QUOTE=jlacroix]I'm pretty sure that Ubuntu cannot play video dvd's, due to the incredibly large number of problems I am having with it, and the fact that none of my friends can play DVD's either, but I am going to give it one last shot before I switch to another distro. (I love Ubuntu, but if it can't play DVD's, then I have no choice). Please understand my frustration, I must've been trying to get this working for a month, asking in forums and searching google. Nothing works.

Here is what I have done to get it working:

1. I installed libdvdcss2, libdvdread, basically everything that so much as has the word "DVD" in it.

2. In turned on DMA, but I have to do this every single time I login with hdparm, because adding it to the end of that file (forgot the name of the file in question) makes my computer say "/dev/hdc no such file or directory" when it boots so I have to do it manually every time in Konsole.

Anyway, I tried Mplayer, Xine, Totem, Totem-xine, and VLC and they all have the same problem. The dvd will play for quite some time and then crash out. Some dvd's don't make it passed the intro screen, some will last an hour into the movie and fail out.

Xine gives me this error:
"the source can't be read. maybe you don't have enough rights for this, or source doesn't contain data" That's the error it gives me when it crashes out. For example, I tried playing Spiderman 2 and when selecting a scene I get that immediately. With Dragonball GT, I can play an episode all the way through but it will fail if I let it go by itself. (If that makes sense).

Mplayer:
MPlayer crashes instananeously with signal 11. Mplayer will play all video files fine (even wmv files) but not dvd's.

Vlc:
I forgot what it does, but that player is worthless to me anyway.

Totem-xine:
Crashes at the same points as Xine, but says something about trying to play a dvd without libdvdcss (Although lbdvdcss is installed, and I even tried reinstalling it).

I went through the unofficial ubuntu guide several times and searched google and nothing helps. For the heck of it, I changed the jumpers on my dvd drive so that it is set to master, but still nothing.

When I open Xine in a terminal, here is the output all the way from when I start playing it to when it crashes. In this example I played Spiderman 2, I chose scen 38 in scene selection, and then it crashed.

```

This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
libdvdread: Using libdvdcss version 1.2.8 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000200
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00001680
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00012968
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002e2940
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002e2960
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e3c20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e3c40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0030a5e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0030a600
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0031c480
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0031c4a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0033f480
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0033f4a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00343d80
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00343da0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0034fb20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0034fb40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0035e700
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0035e720
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x00368320
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x00368340
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00374780
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003747a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003810a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003810c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x00387c40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x00387c60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x00395b60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x00395b80
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003983c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003983e0
libdvdread: Elapsed time 0
libdvdread: Found 15 VTS's
libdvdread: Elapsed time 0
jeremy@Athlon:~$   

```

PLEASE someone help.[/QUOTE]
 

I have the exact same problem and I have applied all the remedy specified in the forum.but none of them solved the dvd viewing.i have even tried different players and i find that ogle could play the dvd the longest.

i have no problems with the hardware because i have no problems listening to cd's and watching vcds.

can anyone help ?

---

### Post by ssck on 2005-08-05
[QUOTE=coolclassic]As you are having so many problems with various dvd's and that playing dvd's in ubuntu is relatively easy I would hazard a guess that there might be a problem with your dvd player. Is there any way that you can check your dvd player in another machine.[/QUOTE]

i have the exact same problem but there is no problem with the dvd player.i can play cd's and vcd's with no problems.what else can i do ?

 ](*,)

---

### Post by coolclassic on 2005-08-05
I stiil think you have a hardware problem.
What results does hdparm /dev/hdc and hdparm -i /dev/hdc give.

---

### Post by ssck on 2005-08-05
[QUOTE=coolclassic]I stiil think you have a hardware problem.
What results does hdparm /dev/hdc and hdparm -i /dev/hdc give.[/QUOTE]

for hdparm /dev/hdc, this is the output :-

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

and for 

/dev/hdc:

 Model=QSI CD-RW/DVD-ROM SBW242C, FwRev=UQ81, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2

 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode


i don't start dma automatically.i will switch it on only when i want to attempt watching dvds

appreciate your help

thanks

---

### Post by coolclassic on 2005-08-05
Lets go back to your installation, did you install xine first or last to be sure reinstall xine you don't have to remove files first to do this.

You use hdparm to set your dma mode don't. My system play moves perfect without setting dma on.

---

### Post by coolclassic on 2005-08-05
[QUOTE=jlacroix]

 For the heck of it, I changed the jumpers on my dvd drive so that it is set to master, but still nothing.

[/QUOTE]

Another thought do you have two dvd or cd or either connected to the same ide cable if so try running dvd by itself.

---

### Post by ssck on 2005-08-05
[QUOTE=coolclassic]Lets go back to your installation, did you install xine first or last to be sure reinstall xine you don't have to remove files first to do this.

You use hdparm to set your dma mode don't. My system play moves perfect without setting dma on.[/QUOTE]

i have reinstalled libxine1 from synaptic.will try viewing the dvds when i get home.will let u know the result.

thanks very much.

---

### Post by ssck on 2005-08-05
[QUOTE=ssck]i have reinstalled libxine1 from synaptic.will try viewing the dvds when i get home.will let u know the result.

thanks very much.[/QUOTE]

hi coolclassic,

i tried the dvd again.still having the same problem.the frame freezes after about ten minutes.what else can i do ?  ](*,)

The image freezes as per attachment.although it is blue in color, there is actually an image.

---

### Post by jlacroix on 2005-08-06
I bought a new DVD drive, its a combo drive (which is why I bought it) and I installed it by itself. There is only one drive.

Its fixed, either it was the other drive or the fact I just have one drive only now.

The only problem is that it won't set DMA during boot, it says no such file or directory so I have to hdparm it after logging in.

---

### Post by wmcbrine on 2005-08-06
[QUOTE=jlacroix]The only problem is that it won't set DMA during boot, it says no such file or directory so I have to hdparm it after logging in.[/QUOTE]
[http://ubuntuforums.org/showpost.php?p=107536&postcount=2](http://ubuntuforums.org/showpost.php?p=107536&postcount=2)

---

### Post by coolclassic on 2005-08-07
[QUOTE=ssck]hi coolclassic,

i tried the dvd again.still having the same problem.the frame freezes after about ten minutes.what else can i do ?  ](*,)

The image freezes as per attachment.although it is blue in color, there is actually an image.[/QUOTE]

This may be another problem relating to graphics card check out this link also let me now if you are still getting the same errors from dmesg.

[http://sourceforge.net/mailarchive/forum.php?thread_id=5584261&forum_id=2551](http://sourceforge.net/mailarchive/forum.php?thread_id=5584261&forum_id=2551)
Also this link
[http://xinehq.de/index.php/faq#BLUESCREEN](http://xinehq.de/index.php/faq#BLUESCREEN)

---

### Post by ssck on 2005-08-07
[QUOTE=coolclassic]This may be another problem relating to graphics card check out this link also let me now if you are still getting the same errors from dmesg.

[http://sourceforge.net/mailarchive/forum.php?thread_id=5584261&forum_id=2551](http://sourceforge.net/mailarchive/forum.php?thread_id=5584261&forum_id=2551)
Also this link
[http://xinehq.de/index.php/faq#BLUESCREEN](http://xinehq.de/index.php/faq#BLUESCREEN)[/QUOTE]


this is what i get after watching the dvd for 5 mins :-

*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***


and in dmesg :- 

UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD_VIDEO_RECORDER', timestamp 2003/01/01 08:00 (11e0)
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 257984
Buffer I/O error on device hdc, logical block 64496
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 257988
Buffer I/O error on device hdc, logical block 64497
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 257992
Buffer I/O error on device hdc, logical block 64498
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 257996
Buffer I/O error on device hdc, logical block 64499
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258000
Buffer I/O error on device hdc, logical block 64500
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258004
Buffer I/O error on device hdc, logical block 64501
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258008
Buffer I/O error on device hdc, logical block 64502
hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
hdc: cdrom_decode_status: error=0x40LastFailedSense 0x04
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258012
Buffer I/O error on device hdc, logical block 64503
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258016
Buffer I/O error on device hdc, logical block 64504
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258020
Buffer I/O error on device hdc, logical block 64505
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258024
Buffer I/O error on device hdc, logical block 64506
hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
hdc: cdrom_decode_status: error=0x40LastFailedSense 0x04
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258028
Buffer I/O error on device hdc, logical block 64507
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258032
Buffer I/O error on device hdc, logical block 64508
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258036
Buffer I/O error on device hdc, logical block 64509
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258040
Buffer I/O error on device hdc, logical block 64510
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258044
Buffer I/O error on device hdc, logical block 64511
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
hdc: cdrom_decode_status: error=0x40LastFailedSense 0x04
hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
hdc: cdrom_decode_status: error=0x40LastFailedSense 0x04
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258112
Buffer I/O error on device hdc, logical block 64528
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258116
Buffer I/O error on device hdc, logical block 64529
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258120
Buffer I/O error on device hdc, logical block 64530
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258124
Buffer I/O error on device hdc, logical block 64531
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258128
Buffer I/O error on device hdc, logical block 64532
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258132
Buffer I/O error on device hdc, logical block 64533
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258136
Buffer I/O error on device hdc, logical block 64534
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258140
Buffer I/O error on device hdc, logical block 64535
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258144
Buffer I/O error on device hdc, logical block 64536
ide-cd: cmd 0x28 timed out
hdc: irq timeout: status=0xd0 { Busy }
hdc: irq timeout: error=0x00
hdc: ATAPI reset complete
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258148
Buffer I/O error on device hdc, logical block 64537
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 258152
Buffer I/O error on device hdc, logical block 64538

i have also added the following line (Option "XaaNoOffscreenPixmaps") into xorg.conf file.however, i am not sure how to refresh the xine-lib file.

the errors still persist.

thanks for helping, coolclassic.appreciate it.

---

### Post by iH8forcedRegistration on 2005-08-07
Unfortunately, my research has yielded very little insight into this problem.

The only solutions I've seen for it suggest that it's caused by an incompatibility between the Linux DVD drivers, the standard hardware DVD interface, and the drive's firmware.

You might consider looking on the website of the manufacturer of the drive for a firmware upgrade. Beyond that, I can't really think of anything else to try.

Sorry.

---

### Post by makisupa123 on 2005-08-31
I was getting the same errors and can make a suggestion.  If you where to compile a kernel you would see that error in conjunction for the flag to use multimode by default.  Instead of compiling a new kernel -- i'm pretty new and that is a bit more involved than I wanted to get --  i figured out the command to pass in hdparm.conf.  So, specifically:

```
sudo gedit /etc/hdparm.conf
``` 

Add an entry at the bottom for your dvd drive --- mine is /dev/hdc.  You might already have one if you wanted dma on -- from the hfparm -i earlier in thread it looks like you haven't done this.  Add the following:

/dev/hdc {
        mult_sect_io = 16
	dma = on
}

NOTE:  the hdc is for my drive -- yours may be different.  The multi_sect_io = 16 is for my drive as well -- this will not work if set to 32.  The opposite may be true for your drive.  As always, good luck and YMMV.  I still have some errors like yours early in a post-boot dmesg --- but no longer do i get them when accessing the drive.


/mak

---

### Post by jvictor on 2005-10-31
I agree with makisupa123 , I too faced serious pains with DVD stuff and enabling DMA did the magic

---

