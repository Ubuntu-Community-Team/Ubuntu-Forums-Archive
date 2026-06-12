---
title: "Quake 3 and refresh rates"
date: 2005-04-25
forum: Gaming &amp; Leisure
---

### Post by airk on 2005-04-25
Hello all,

Longish post, but i'd be happy if someone with insight in modelines and possibly quake3 could have a look.

I assume my problem is not at all unique, but after trying quite a few different solutions I feel a bit at loss.

Anyways, as my title suggests this is about Quake 3.

I've used gtf to set the correct modelines in xorg.conf, but it seems that my refreshrate refuses to go above 85Hz.

I have a 22" CRT, which i ran in 1600x1200@100Hz, and in Quake3 1024x768@120Hz in Windows 2000. In linux i can't seem to get my refresh rate above 85Hz. And as some might know, the feel of quake3 is quite dependant on refresh rates (imho).

The only error i can se in /var/log/Xorg.0.log is:

airk@moe:~$ cat /var/log/Xorg.0.log | grep WW 

(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID" does not exist.
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): could not detect XFree86 version (query_status=-3)

Any ideas?

So far I've lowerd my resolution and up:ed the resolution with modelines just to se if i get something above 85Hz, but no go. I've had a go with 1600x1200 1024x768 800x600 with modelines @ 100 on 1600x1200 and the 100Hz and 120Hz on 1025x768 and 800x600. All modlines set with gtf.

Am i doing something wrong with modelines? I've commented out the ones I've tested. At the moment i have 85Hz @ 1600x1200 with a modeline that should give me 100Hz.

Section "Monitor"
        Identifier      "Compaq P1220"
        Option          "DPMS"
        HorizSync       30-130
        VertRefresh     50-160
        # 800x600 @ 100.00 Hz (GTF) hsync: 63.60 kHz; pclk: 68.18 MHz
        # Modeline "800x600_100.00"  68.18  800 848 936 1072  600 601 604 636  -HSync +Vsync
        # 1024x768 @ 120.00 Hz (GTF) hsync: 98.76 kHz; pclk: 139.05 MHz
        # Modeline "1024x768_120.00"  139.05  1024 1104 1216 1408  768 769 772 823  +HSync +Vsync
        # 800x600 @ 120.00 Hz (GTF) hsync: 77.16 kHz; pclk: 83.95 MHz
        # Modeline "800x600_120.00"  83.95  800 856 944 1088  600 601 604 643  +HSync +Vsync
        # 1792x1344 @ 100.00 Hz (GTF) hsync: 142.30 kHz; pclk: 352.90 MHz
        # Modeline "1792x1344_100.00"  352.90  1792 1936 2136 2480  1344 1345 1348 1423  -HSync +Vsync
        # 1600x1200 @ 100.00 Hz (GTF) hsync: 127.10 kHz; pclk: 280.64 MHz
        Modeline "1600x1200_100.00"  280.64  1600 1728 1904 2208  1200 1201 1204 1271  -HSync +Vsync
EndSection

---

### Post by airk on 2005-04-25
Moahaha! Solved it!

I'll post my findings so others might be helped.

Basicaly it was the alias of the modeline that i missed.

i.e
airk@moe:~$ gtf 2048 1536 80

  # 2048x1536 @ 80.00 Hz (GTF) hsync: 128.64 kHz; pclk: 364.31 MHz
  Modeline "2048x1536_80.00"  364.31  2048 2216 2440 2832  1536 1537 1540 1608  -HSync +Vsync

This means that in the "Screen" section of xorg.conf one needs to add the "2048x1536_80.00"-part to "Display"-section.

So, in my case:

airk@moe:~$ gtf 1600 1200 99 

  # 1600x1200 @ 99.00 Hz (GTF) hsync: 125.73 kHz; pclk: 277.61 MHz
  Modeline **"1600x1200_99.00"**  277.61  1600 1728 1904 2208  1200 1201 1204 1270  -HSync +Vsync

would give:

Section "Monitor"
        Identifier      "Compaq P1220"
        Option          "DPMS"
        HorizSync       30-130
        VertRefresh     50-160
        Modeline **"1600x1200_99.00"**  277.61  1600 1728 1904 2208  1200 1201 1204 1270  -HSync +Vsync
EndSection

and the important part is to add it to the "Display"-section

SubSection "Display"
                Depth           24            
                Modes           **"1600x1200_99.00"** "1600x1200" "1024x768" "800x600" "640x480"
EndSubSection

I actually haven't tested it regarding quake3 yet, but i'll just (stupidly) assume it'll work. And remember - be absolutly sure what you monitor can handle before tampering with modelines.

---

### Post by airk on 2005-04-25
And, I can confirm that it also works in quake3. Yey!

Apparently there can be an issue regarding the gfx (video cards) pixel dot clock. In some cases there seems to be a problem at the exact refresh rate (i.e 100Hz), but this usually can be fixed by lowering 1Hz. Although i think this mainly is applicable to higher resolution as modern gfx:s quite easily can take on 1600x1200@100Hz.

as such:
if 1600x1200@100 dosen't work, although your monitor specs are in the green.
airk@moe:~$ gtf 1600 1200 100

  # 1600x1200 @ 100.00 Hz (GTF) hsync: 127.10 kHz; pclk: 280.64 MHz
  Modeline "1600x1200_100.00"  280.64  1600 1728 1904 2208  1200 1201 1204 1271  -HSync +Vsync

try, 1600x1200@99Hz
airk@moe:~$ gtf 1600 1200 99

  # 1600x1200 @ 99.00 Hz (GTF) hsync: 125.73 kHz; pclk: 277.61 MHz
  Modeline "1600x1200_99.00"  277.61  1600 1728 1904 2208  1200 1201 1204 1270  -HSync +Vsync

A quite good url on the subject:
[http://polydistortion.net/monkey/archives/2002/10/10/001096.html](http://polydistortion.net/monkey/archives/2002/10/10/001096.html)

Now, I will play quake 3 (1024x768 @ 120Hz) ! :-)

---

