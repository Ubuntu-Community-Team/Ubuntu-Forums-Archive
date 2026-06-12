---
title: "BENCHMARKS - glxgears FPS scores, just for fun"
date: 2005-06-04
forum: Gaming &amp; Leisure
---

### Post by oritpro on 2005-06-04
Since we're all Ubuntu Linux fans here and I am sure there are some that enjoy PC gaming and would like to see more Linux ports of our favorite games, I thought it might be fun to start a benchmarking thread in the hope that we can share tips and tricks (and bragging rights) on making our favorite platform even more capable.

And for the record, I like to tweak my system but tend to lean towards the conservative side.  Better to be safe than sorry  :) 

So here goes:

My glxgears score: 8,345 FPS

My System-
AMD Athlon 3200+ Winchester - clocked at 2.2Ghz (220 HTT)
MSI Neo 2 Platinum Ultra motherboard, Nforce 3.
MSI Nvidia 6600GT AGP, coolbits enabled, core 535Mhz, memory 1148
1 GB Kingston HyperX
200 GB Sata 1

So who can beat this, what are your specs and what tweaks did you do that others might benefit from.  Come on, don't be shy!

---

### Post by jdodson on 2005-06-04
zoiks scoob!  i cant beat that:

AMD 64 3000+ (2 ghz)
1G Ram
Nvidia 5700LE 265M

glxgears: 2800+

---

### Post by Khannie on 2005-06-04
I averaged 4601 (excluding the first set)

System:
Athlon 2800+ @ 3200+
9800 pro (8.12.10 drivers)
768MB ram

---

### Post by equilibrium on 2005-06-04
$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled
$ glxgears
59145 frames in 5.0 seconds = 11829.000 FPS
59045 frames in 5.0 seconds = 11809.000 FPS

CPU: p4 2.8c @ 3.5Ghz
GPU: nvidia 6800le 16pipes
RAM: 1gb PC3200
KERNEL:  2.6.10-5-686-smp

 :grin:

---

### Post by thechitowncubs on 2005-06-04
3,000

2500+
GeForce 5600
512MB

---

### Post by gil-galad on 2005-06-04
3202

2.2ghz athlon xp
Geforce 4ti 4200
768MB

---

### Post by jzke on 2005-06-05
Hehehehehe... well here's mine:

Average 412.6

Athlon XP 2500+
GeForce 2 MX 200 64mb
512mb DDR

---

### Post by rpgcyco on 2005-06-05
Average: 8486.9 FPS

AMD Athlon XP 2000+
512M DDR
256MB GeForce FX 5950 Ultra
NVIDIA 7664 Drivers

- Rpg Cyco

---

### Post by Rumo on 2005-06-05
Average:   3978 FPS

AMD Duron 1.2 GHz
512MB DDR
GeForce 4 Ti 4200
NVIDIA 7664 Drivers

Wouldn't have thought that my aged system competes so well! 

I made just some minor tweaks that shouldn't help much here (swappiness=25, activated 32bit-DMA-mode for harddrive,...).

---

### Post by Curlydave on 2005-06-05
Damn, I'm only getting around 5000-6000 on an X800pro. Something's off. Oh well.

(and I'd be happier if I could get it to fix at 70fps via Vsync...)

---

### Post by tread on 2005-06-05
You should get more jzke .. are you sure glx is loaded in xorg? Check the xorg.conf .. mine jumped from 4500 to 7500 or so.

---

### Post by digby on 2005-06-05
I get about 4700.

Athlon XP 2500+
GeForce4 Ti4800 w/ 128 MB RAM
1 GB PC3200 RAM

I can also cheat and get my score up to about 13.2k if I hide the gears behind my konsole window... ;-)

---

### Post by Spif on 2005-06-05
Laptop:

1,7 Ghz Centrino
512 MB RAM
ATi Radeon Mobility 9700 Pro

I score around 1300 frames per second with the driver from the Ubuntu repositories. With the latest graphics driver installed (followed a guide posted elsewhere on this forum) I get about 2000. A major improvement, but it just shows ATi's Linux drivers still has a long way to go...

---

### Post by oritpro on 2005-06-05
Ha, that's a good one.  I guess I should've stated that the output must not be hidden behind another window.  [-X  :) 

It's interesting to see the different scores across different and similiar hardware combinations though.  

One thing I've noticed is that if you don't completely clear out the old driver before installing the new one, you will suffer performance degradation and possible a non working driver in OpenGL mode.

We need a driverclean package for Linux!


[QUOTE=digby]I get about 4700.

Athlon XP 2500+
GeForce4 Ti4800 w/ 128 MB RAM
1 GB PC3200 RAM

I can also cheat and get my score up to about 13.2k if I hide the gears behind my konsole window... ;-)[/QUOTE]

---

### Post by Paulus on 2005-06-05
with xcompmgr running too!

paulus@ubuntu:~$ glxgears
36988 frames in 5.0 seconds = 7397.600 FPS
45228 frames in 5.0 seconds = 9045.600 FPS
45202 frames in 5.0 seconds = 9040.400 FPS
45217 frames in 5.0 seconds = 9043.400 FPS

Nvidia(of course!) 5900lx softmodded 2 5950u :D

Hey wheres all the overclocked scores now that we have a new driver!

---

### Post by RastaMahata on 2005-06-05
1266
athlon xp 1700+
256 pc2100 value ram (I need to save money...)
GeForce 4 MX 440 AGP 8x (Yes, I need a new video card too)

---

### Post by DarkKnight on 2005-06-06
stevie@Steel:~$ glxgears
3321 frames in 5.0 seconds = 664.200 FPS
3539 frames in 5.0 seconds = 707.800 FPS
3501 frames in 5.0 seconds = 700.200 FPS
3539 frames in 5.0 seconds = 707.800 FPS
3537 frames in 5.0 seconds = 707.400 FPS

System: 
AMD 2500+ (oc'd to 3200+)
512MB GeIL DC DDR400
ATI 9200SE (I use to have a 9550, which got about 3k tops, but I bought a NVidia card so this is my temp card untill it arrives.)

---

### Post by simonkitch on 2005-06-06
kitch@ubuntu:~$ glxgears
44637 frames in 5.0 seconds = 8927.400 FPS
57785 frames in 5.0 seconds = 11557.000 FPS
58010 frames in 5.0 seconds = 11602.000 FPS
58021 frames in 5.0 seconds = 11604.200 FPS
58025 frames in 5.0 seconds = 11605.000 FPS

kitch@ubuntu:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

athlon XP mobile 2500 running at 2 gig
1 gig ram, 266 fsb
NVIDIA 6600GT

---

### Post by jzke on 2005-06-06
[QUOTE=tread]You should get more jzke .. are you sure glx is loaded in xorg? Check the xorg.conf .. mine jumped from 4500 to 7500 or so.[/QUOTE]

 :-x it's in there... but still the low scores! hmm... oh well some thing we just have to live with. ](*,)

---

### Post by NeoChaosX on 2005-06-06
935 fps average  :-| 

Intel Pentium 4 2.66 GHz
768 MB DDR RAM
ATi Mobility Radeon 7500 32MB

How are other people with M. Radeon 7500s breaking the 1000fps mark? I still can't seem to do it.

---

### Post by verbalshadow on 2005-06-06
[QUOTE=NeoChaosX]935 fps average  :-| 

Intel Pentium 4 2.66 GHz
768 MB DDR RAM
ATi Mobility Radeon 7500 32MB

How are other people with M. Radeon 7500s breaking the 1000fps mark? I still can't seem to do it.[/QUOTE]
 verbalshadow@darkspiral:~$ glxgears
841 frames in 5.0 seconds = 168.200 FPS
914 frames in 5.0 seconds = 182.800 FPS
908 frames in 5.0 seconds = 181.600 FPS
988 frames in 5.0 seconds = 197.600 FPS
912 frames in 5.0 seconds = 182.400 FPS
908 frames in 5.0 seconds = 181.600 FPS
816 frames in 5.0 seconds = 163.200 FPS


amd XP-m 2800+
768mb ddr ram
ATI Radeon Mobility U1

Drivers that came with hoary.

---

### Post by ruben_b on 2005-06-06
does anybody use an intel 915GM 128mb shared memory?
i only get 800fps and i can´t believe thats all!?

my old geforce 420 go had allready 1500fps.

---

### Post by mrf on 2005-06-06
63599 frames in 5.0 seconds = 12719.800 FPS

amd64 3500
6800 gt

wish the linux drivers supported sli... reckon I could crack 20k

---

### Post by hard_i on 2005-06-06
7015 frames in 5.0 seconds = 1403.000 FPS
7016 frames in 5.0 seconds = 1403.200 FPS
7015 frames in 5.0 seconds = 1403.000 FPS
7014 frames in 5.0 seconds = 1402.800 FPS

Celeron @ 3.0Ghz
fx5200, 64bit, 250/400
nvidia 71.74

---

### Post by Khannie on 2005-06-07
[QUOTE=simonkitch]kitch@ubuntu:~$ glxgears
44637 frames in 5.0 seconds = 8927.400 FPS
57785 frames in 5.0 seconds = 11557.000 FPS
58010 frames in 5.0 seconds = 11602.000 FPS
58021 frames in 5.0 seconds = 11604.200 FPS
58025 frames in 5.0 seconds = 11605.000 FPS

kitch@ubuntu:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

athlon XP mobile 2500 running at 2 gig
1 gig ram, 266 fsb
NVIDIA 6600GT[/QUOTE]

WHAT THE FUNK?!?!?!?!

I have an Athlon 2800+ running at just short of 3200+ speeds, 768MB of ram and a 6600GT and I got around 7200fps.

Am I doing something wrong? Did you mean 6800GT?

---

### Post by mike998 on 2005-06-07
```
mike@wolfspider:~$ glxgears
2156 frames in 5.0 seconds = 431.200 FPS
10414 frames in 5.0 seconds = 2082.800 FPS
7215 frames in 5.0 seconds = 1443.000 FPS
2616 frames in 5.0 seconds = 523.200 FPS
2634 frames in 5.0 seconds = 526.800 FPS
2635 frames in 5.0 seconds = 527.000 FPS
2619 frames in 5.0 seconds = 523.800 FPS
2629 frames in 5.0 seconds = 525.800 FPS
2620 frames in 5.0 seconds = 524.000 FPS
``` 

Don't know what that wierd jump is...  Although my dmesg for some strange reason shows 

```
[drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corp. 82852/855GM Integrated Graphics Device
[drm] Initialized i915 1.2.0 20040405 on minor 1: Intel Corp. 82852/855GM Integrated Graphics Device (#2)
``` 

No idea what that is all about - two devices?  And I'm buggered if I know how much video ram I have...  I seem to remember something about 64megs, but not sure...

---

### Post by robtotheb on 2005-06-07
55849 frames in 5.0 seconds = 11169.800 FPS
63980 frames in 5.0 seconds = 12796.000 FPS
63955 frames in 5.0 seconds = 12791.000 FPS
63977 frames in 5.0 seconds = 12795.400 FPS
63927 frames in 5.0 seconds = 12785.400 FPS

GeForce 6800 GT 256 MB

---

### Post by simonkitch on 2005-06-09
[QUOTE=simonkitch]kitch@ubuntu:~$ glxgears
44637 frames in 5.0 seconds = 8927.400 FPS
57785 frames in 5.0 seconds = 11557.000 FPS
58010 frames in 5.0 seconds = 11602.000 FPS
58021 frames in 5.0 seconds = 11604.200 FPS
58025 frames in 5.0 seconds = 11605.000 FPS

kitch@ubuntu:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

athlon XP mobile 2500 running at 2 gig
1 gig ram, 266 fsb
NVIDIA 6600GT[/QUOTE]
 Ugh I've broken something! Had to reinstall the driver after having problems with captive-static install. Now I'm only getting 

kitch@ubuntu:~$ glxgears
31656 frames in 5.0 seconds = 6331.200 FPS
33272 frames in 5.0 seconds = 6654.400 FPS
33279 frames in 5.0 seconds = 6655.800 FPS

Have uninstalled captive and reinstalled the Nvidia driver from their website. Are there any opimizations I need to make in the xorg.conf file?

---

### Post by simonkitch on 2005-06-09
No mate I just had to reinstall my Nvidia driver now i'm getting :-

kitch@ubuntu:~$ glxgears
31656 frames in 5.0 seconds = 6331.200 FPS
33272 frames in 5.0 seconds = 6654.400 FPS
33279 frames in 5.0 seconds = 6655.800 FPS

No idea how I achieved that first score unfortunatly :(

---

### Post by Teren on 2005-06-09
[QUOTE=simonkitch]Ugh I've broken something! Had to reinstall the driver after having problems with captive-static install. Now I'm only getting 

kitch@ubuntu:~$ glxgears
31656 frames in 5.0 seconds = 6331.200 FPS
33272 frames in 5.0 seconds = 6654.400 FPS
33279 frames in 5.0 seconds = 6655.800 FPS

Have uninstalled captive and reinstalled the Nvidia driver from their website. Are there any opimizations I need to make in the xorg.conf file?[/QUOTE]
 CPU: Pentium III -s 1.4GHz with 512kb L2 cache (the last of PIII, the better than all P4s with Williamette core)
RAM: 512MB SDR
GFX: GeForce FX5600 non-ultra 128MB

3500 in glxgears

BUT, normally I run Xorg with nv instead of nvidia, I rarely play games now, and I hate those random lockups, that nothing seems to fix.

---

### Post by rider343 on 2005-06-09
glxgears
7314 frames in 5.0 seconds = 1462.800 FPS
8250 frames in 5.0 seconds = 1650.000 FPS
8447 frames in 5.0 seconds = 1689.400 FPS
8447 frames in 5.0 seconds = 1689.400 FPS
8340 frames in 5.0 seconds = 1668.000 FPS
8437 frames in 5.0 seconds = 1687.400 FPS
8445 frames in 5.0 seconds = 1689.000 FPS

Pentium 4 3.2 HT
Asus p4p800-E Deluxe Motherboard
1 Gb DDR 400
Radeon 9600XT

---

### Post by thedaemon on 2005-06-09
43908 frames in 5.0 seconds = 8781.600 FPS
48500 frames in 5.0 seconds = 9700.000 FPS
48466 frames in 5.0 seconds = 9693.200 FPS
48499 frames in 5.0 seconds = 9699.800 FPS
47803 frames in 5.0 seconds = 9560.600 FPS
48391 frames in 5.0 seconds = 9678.200 FPS

amd 64 3000+
1GB ddr
geforce 6800
msi k8t neo
24" LCD @1920x1200  \\:D/

---

### Post by simonkitch on 2005-06-09
[QUOTE=Khannie]WHAT THE FUNK?!?!?!?!

I have an Athlon 2800+ running at just short of 3200+ speeds, 768MB of ram and a 6600GT and I got around 7200fps.

Am I doing something wrong? Did you mean 6800GT?[/QUOTE]
 Just enabled coolbits for the Nvidia driver

Before...
kitch@ubuntu:~$ glxgears
30662 frames in 5.0 seconds = 6132.400 FPS
33702 frames in 5.0 seconds = 6740.400 FPS
33686 frames in 5.0 seconds = 6737.200 FPS
33713 frames in 5.0 seconds = 6742.600 FPS

After
kitch@ubuntu:~$ glxgears
36615 frames in 5.0 seconds = 7323.000 FPS
38931 frames in 5.0 seconds = 7786.200 FPS
38912 frames in 5.0 seconds = 7782.400 FPS
38892 frames in 5.0 seconds = 7778.400 FPS

kitch@ubuntu:~$ cat /proc/driver/nvidia/agp/status
Status: Enabled
Driver: AGPGART
AGP Rate: 8x
Fast Writes: Disabled
SBA: Enabled

athlon XP mobile 2500 running at 2 gig
1 gig ram, 266 fsb
NVIDIA 6600GT

---

### Post by simonkitch on 2005-06-09
Not sure glxgears is  a very reliable benchmark utility. Have a look at this on my 
AMD Mobile 2500 running at 2 gig
Nvidia GT6600
1 gig ram at 266 fsb

kitch@ubuntu:~$ glxgears
36615 frames in 5.0 seconds = 7323.000 FPS
38931 frames in 5.0 seconds = 7786.200 FPS
38912 frames in 5.0 seconds = 7782.400 FPS
38892 frames in 5.0 seconds = 7778.400 FPS
36908 frames in 5.0 seconds = 7381.600 FPS
38765 frames in 5.0 seconds = 7753.000 FPS
35018 frames in 5.0 seconds = 7003.600 FPS
42660 frames in 5.0 seconds = 8532.000 FPS
42382 frames in 5.0 seconds = 8476.400 FPS
53842 frames in 5.0 seconds = 10768.400 FPS
44729 frames in 5.0 seconds = 8945.800 FPS
43303 frames in 5.0 seconds = 8660.600 FPS
65504 frames in 5.0 seconds = 13100.800 FPS
63623 frames in 5.0 seconds = 12724.600 FPS
65355 frames in 5.0 seconds = 13071.000 FPS
66673 frames in 5.0 seconds = 13334.600 FPS
66736 frames in 5.0 seconds = 13347.200 FPS
66341 frames in 5.0 seconds = 13268.200 FPS
66600 frames in 5.0 seconds = 13320.000 FPS
66173 frames in 5.0 seconds = 13234.600 FPS
65768 frames in 5.0 seconds = 13153.600 FPS
65962 frames in 5.0 seconds = 13192.400 FPS
66231 frames in 5.0 seconds = 13246.200 FPS
66379 frames in 5.0 seconds = 13275.800 FPS
65977 frames in 5.0 seconds = 13195.400 FPS
64288 frames in 5.0 seconds = 12857.600 FPS
57514 frames in 5.0 seconds = 11502.800 FPS
66132 frames in 5.0 seconds = 13226.400 FPS
59287 frames in 5.0 seconds = 11857.400 FPS
63453 frames in 5.0 seconds = 12690.600 FPS
66316 frames in 5.0 seconds = 13263.200 FPS
61945 frames in 5.0 seconds = 12389.000 FPS
64154 frames in 5.0 seconds = 12830.800 FPS
65127 frames in 5.0 seconds = 13025.400 FPS
65974 frames in 5.0 seconds = 13194.800 FPS
66868 frames in 5.0 seconds = 13373.600 FPS
64991 frames in 5.0 seconds = 12998.200 FPS
60043 frames in 5.0 seconds = 12008.600 FPS
53037 frames in 5.0 seconds = 10607.400 FPS
63343 frames in 5.0 seconds = 12668.600 FPS
59861 frames in 5.0 seconds = 11972.200 FPS
65571 frames in 5.0 seconds = 13114.200 FPS
61565 frames in 5.0 seconds = 12313.000 FPS
62755 frames in 5.0 seconds = 12551.000 FPS
63384 frames in 5.0 seconds = 12676.800 FPS
61848 frames in 5.0 seconds = 12369.600 FPS
66452 frames in 5.0 seconds = 13290.400 FPS
66345 frames in 5.0 seconds = 13269.000 FPS
65008 frames in 5.0 seconds = 13001.600 FPS
58309 frames in 5.0 seconds = 11661.800 FPS
66671 frames in 5.0 seconds = 13334.200 FPS
66615 frames in 5.0 seconds = 13323.000 FPS
59119 frames in 5.0 seconds = 11823.800 FPS
60475 frames in 5.0 seconds = 12095.000 FPS
54703 frames in 5.0 seconds = 10940.600 FPS
64123 frames in 5.0 seconds = 12824.600 FPS
65226 frames in 5.0 seconds = 13045.200 FPS
63487 frames in 5.0 seconds = 12697.400 FPS
64244 frames in 5.0 seconds = 12848.800 FPS
57570 frames in 5.0 seconds = 11514.000 FPS
64526 frames in 5.0 seconds = 12905.200 FPS
59738 frames in 5.0 seconds = 11947.600 FPS
35921 frames in 5.0 seconds = 7184.200 FPS
46119 frames in 5.0 seconds = 9223.800 FPS
63434 frames in 5.0 seconds = 12686.800 FPS
59721 frames in 5.0 seconds = 11944.200 FPS
65919 frames in 5.0 seconds = 13183.800 FPS
62416 frames in 5.0 seconds = 12483.200 FPS
64368 frames in 5.0 seconds = 12873.600 FPS
63496 frames in 5.0 seconds = 12699.200 FPS
65631 frames in 5.0 seconds = 13126.200 FPS
59284 frames in 5.0 seconds = 11856.800 FPS
53439 frames in 5.0 seconds = 10687.800 FPS
41908 frames in 5.0 seconds = 8381.600 FPS
63303 frames in 5.0 seconds = 12660.600 FPS
65790 frames in 5.0 seconds = 13158.000 FPS
48393 frames in 5.0 seconds = 9678.600 FPS
64320 frames in 5.0 seconds = 12864.000 FPS
66840 frames in 5.0 seconds = 13368.000 FPS
63103 frames in 5.0 seconds = 12620.600 FPS
50600 frames in 5.0 seconds = 10120.000 FPS
61308 frames in 5.0 seconds = 12261.600 FPS
65641 frames in 5.0 seconds = 13128.200 FPS
62578 frames in 5.0 seconds = 12515.600 FPS
45385 frames in 5.0 seconds = 9077.000 FPS
65985 frames in 5.0 seconds = 13197.000 FPS
62852 frames in 5.0 seconds = 12570.400 FPS
65273 frames in 5.0 seconds = 13054.600 FPS
64991 frames in 5.0 seconds = 12998.200 FPS
63335 frames in 5.0 seconds = 12667.000 FPS
65857 frames in 5.0 seconds = 13171.400 FPS
64494 frames in 5.0 seconds = 12898.800 FPS
63973 frames in 5.0 seconds = 12794.600 FPS
63314 frames in 5.0 seconds = 12662.800 FPS
61678 frames in 5.0 seconds = 12335.600 FPS
63696 frames in 5.0 seconds = 12739.200 FPS
63403 frames in 5.0 seconds = 12680.600 FPS
64850 frames in 5.0 seconds = 12970.000 FPS
62619 frames in 5.0 seconds = 12523.800 FPS
58021 frames in 5.0 seconds = 11604.200 FPS
58978 frames in 5.0 seconds = 11795.600 FPS
66259 frames in 5.0 seconds = 13251.800 FPS
65909 frames in 5.0 seconds = 13181.800 FPS
65809 frames in 5.0 seconds = 13161.800 FPS
65948 frames in 5.0 seconds = 13189.600 FPS
65584 frames in 5.0 seconds = 13116.800 FPS
66107 frames in 5.0 seconds = 13221.400 FPS
66621 frames in 5.0 seconds = 13324.200 FPS
63609 frames in 5.0 seconds = 12721.800 FPS
66215 frames in 5.0 seconds = 13243.000 FPS
66121 frames in 5.0 seconds = 13224.200 FPS
66352 frames in 5.0 seconds = 13270.400 FPS
66366 frames in 5.0 seconds = 13273.200 FPS
66773 frames in 5.0 seconds = 13354.600 FPS
66778 frames in 5.0 seconds = 13355.600 FPS
60112 frames in 5.0 seconds = 12022.400 FPS
65344 frames in 5.0 seconds = 13068.800 FPS
61341 frames in 5.0 seconds = 12268.200 FPS
61918 frames in 5.0 seconds = 12383.600 FPS
59658 frames in 5.0 seconds = 11931.600 FPS
57852 frames in 5.0 seconds = 11570.400 FPS
60002 frames in 5.0 seconds = 12000.400 FPS
52059 frames in 5.0 seconds = 10411.800 FPS
57919 frames in 5.0 seconds = 11583.800 FPS
60495 frames in 5.0 seconds = 12099.000 FPS
60416 frames in 5.0 seconds = 12083.200 FPS
56052 frames in 5.0 seconds = 11210.400 FPS
49684 frames in 5.0 seconds = 9936.800 FPS
66196 frames in 5.0 seconds = 13239.200 FPS
65493 frames in 5.0 seconds = 13098.600 FPS
64740 frames in 5.0 seconds = 12948.000 FPS
65438 frames in 5.0 seconds = 13087.600 FPS
66568 frames in 5.0 seconds = 13313.600 FPS
52923 frames in 5.0 seconds = 10584.600 FPS
60423 frames in 5.0 seconds = 12084.600 FPS
66785 frames in 5.0 seconds = 13357.000 FPS
64124 frames in 5.0 seconds = 12824.800 FPS
63130 frames in 5.0 seconds = 12626.000 FPS
66648 frames in 5.0 seconds = 13329.600 FPS
51324 frames in 5.0 seconds = 10264.800 FPS
64561 frames in 5.0 seconds = 12912.200 FPS
56595 frames in 5.0 seconds = 11319.000 FPS
58949 frames in 5.0 seconds = 11789.800 FPS
59832 frames in 5.0 seconds = 11966.400 FPS
52877 frames in 5.0 seconds = 10575.400 FPS
38104 frames in 5.0 seconds = 7620.800 FPS
35716 frames in 5.0 seconds = 7143.200 FPS
35785 frames in 5.0 seconds = 7157.000 FPS
38789 frames in 5.0 seconds = 7757.800 FPS
38851 frames in 5.0 seconds = 7770.200 FPS
38848 frames in 5.0 seconds = 7769.600 FPS
38854 frames in 5.0 seconds = 7770.800 FPS
38846 frames in 5.0 seconds = 7769.200 FPS
38843 frames in 5.0 seconds = 7768.600 FPS
38851 frames in 5.0 seconds = 7770.200 FPS
38847 frames in 5.0 seconds = 7769.400 FPS
38847 frames in 5.0 seconds = 7769.400 FPS
38853 frames in 5.0 seconds = 7770.600 FPS
38846 frames in 5.0 seconds = 7769.200 FPS
38844 frames in 5.0 seconds = 7768.800 FPS
38852 frames in 5.0 seconds = 7770.400 FPS
38849 frames in 5.0 seconds = 7769.800 FPS
38852 frames in 5.0 seconds = 7770.400 FPS
38847 frames in 5.0 seconds = 7769.400 FPS
38849 frames in 5.0 seconds = 7769.800 FPS
38854 frames in 5.0 seconds = 7770.800 FPS
3885
What the heck is going on here  :-?

---

### Post by benplaut on 2005-06-09
a mere 600fps  ](*,)  ](*,)  

no luck with DRI on my Mobility Radeon 7500, so i can't play any games

it sucks because i want to play nexuiz  :-x  :-x  :-x

---

### Post by Snipersnest on 2005-06-09
Well this is what I get.. I can play Counter-Strike, CS: Source and most any of the games with about 60-300fps easy.  Source is the lowest score for me at 50fps. Counter-Strike 1.6 is my highest at 175fps.. YES PEOPLE EVEN ON LINUX.

My Windows scores are 170-219fps for 1.6 and 100-175fps for Source.
[b]
GLXGEARS SCORE:[/b]
[b]63092 frames in 5.0 seconds = 12618.400 FPS
63056 frames in 5.0 seconds = 12611.200 FPS
63073 frames in 5.0 seconds = 12614.600 FPS
[/b]**63125 frames in 5.0 seconds = 12625.000 FPS**

Athlon 2600+ 1.9ghz
1GB PC2700 
BFG Geforce 6800 GT OC (AGP)
250gb HD

Bios settings are your biggest kill for FPS loss... BUT I WILL WARN YOU... IT COULD SCREW YOUR SYSTEM UP. NOTE TO SELF REMEMBER WHAT I CHANGE!!

[www.omegadrivers.net](www.omegadrivers.net)  has a VERY GOOD list for your BIOS settings. Follow those and your scores should go up.

---

### Post by gil-galad on 2005-06-09
If you move your mouse around or do anything on the computer glxgears will not compute correctly.  Don't do anything on your computer and don't look at the first couple numbers.

---

### Post by zaius on 2005-06-09
glxgears;
62838 frames in 5.0 seconds = 12567.600 FPS
62687 frames in 5.0 seconds = 12537.400 FPS
62978 frames in 5.0 seconds = 12595.600 FPS
58074 frames in 5.0 seconds = 11614.800 FPS
56185 frames in 5.0 seconds = 11237.000 FPS
52155 frames in 5.0 seconds = 10431.000 FPS
65145 frames in 5.0 seconds = 13029.000 FPS

Dell Inspiron 9300 laptop
pentium M 1.86 ghz 533 mhz fsb 2mb cache
1 gb of corsair memory
256 mb geforce go 6800

not bad for a laptop :)

---

### Post by Curlydave on 2005-06-09
~5100

Gotta love those ATI drivers.

---

### Post by skoal on 2005-06-09
~4750 FPS.  I think I need more Frame Per Second.  I think I need more cowbells.  I have a feva for FPS, and more cowbells is the solution.

\\//_

---

### Post by dtessier on 2005-06-09
Athlon XP 2500+
1GB RAM
Nforce2 IGP w/64MB RAM

7273 frames in 5.0 seconds = 1454.600 FPS
8423 frames in 5.0 seconds = 1684.600 FPS
8425 frames in 5.0 seconds = 1685.000 FPS
8414 frames in 5.0 seconds = 1682.800 FPS
8417 frames in 5.0 seconds = 1683.400 FPS
8416 frames in 5.0 seconds = 1683.200 FPS
8418 frames in 5.0 seconds = 1683.600 FPS

---

### Post by matthew on 2005-06-09
7030 frames in 5.0 seconds = 1406.000 FPS
7029 frames in 5.0 seconds = 1405.800 FPS
7032 frames in 5.0 seconds = 1406.400 FPS
7030 frames in 5.0 seconds = 1406.000 FPS
7031 frames in 5.0 seconds = 1406.200 FPS
7024 frames in 5.0 seconds = 1404.800 FPS

Pretty stable. Not as fast as I would like, but better than a few days ago... I just got fglrx working yesterday and so ATI decided to release a new driver today. I really want to try it out, but I am also enjoying the fact that everything's working right now.

What to do, what to do??? Risk breaking it to make it faster or just sit on something that works... I just can't decide!

Pentium M 745
1 Gb ram
ATI Mobility Radeon 9700

---

### Post by simonkitch on 2005-06-10
changed the priority for glxgears while it was running. Now I'm rocking!

kitch@ubuntu:~$ glxgears
45896 frames in 5.0 seconds = 9179.200 FPS
61528 frames in 5.0 seconds = 12305.600 FPS
58652 frames in 5.0 seconds = 11730.400 FPS
50483 frames in 6.0 seconds = 8413.833 FPS
35261 frames in 5.0 seconds = 7052.200 FPS
59947 frames in 5.0 seconds = 11989.400 FPS
61918 frames in 5.0 seconds = 12383.600 FPS
59158 frames in 5.0 seconds = 11831.600 FPS
59093 frames in 5.0 seconds = 11818.600 FPS
58466 frames in 5.0 seconds = 11693.200 FPS
60413 frames in 5.0 seconds = 12082.600 FPS
57931 frames in 5.0 seconds = 11586.200 FPS
58566 frames in 5.0 seconds = 11713.200 FPS
61455 frames in 5.0 seconds = 12291.000 FPS
59913 frames in 5.0 seconds = 11982.600 FPS

AMD Mobile 2500 running at 2 gig
Nvidia GT6600
1 gig ram at 266 fsb

This probably explains previous strange results where the frame rate changes suddenly?

---

### Post by jer1ch0 on 2005-06-10
How do you measure the fps  for glxgears?

---

### Post by Curlydave on 2005-06-10
~7000fps. I get around 1250 in fgl_glxgears. I'm using a Radeon x800pro.

Damn, this thread shows just how much you get boned for using ATI with Linux.

---

### Post by vassalle on 2005-06-10
[QUOTE=Snipersnest]Well this is what I get.. I can play Counter-Strike, CS: Source and most any of the games with about 60-300fps easy.  Source is the lowest score for me at 50fps. Counter-Strike 1.6 is my highest at 175fps.. YES PEOPLE EVEN ON LINUX.

My Windows scores are 170-219fps for 1.6 and 100-175fps for Source.
[b]
GLXGEARS SCORE:[/b]
[b]63092 frames in 5.0 seconds = 12618.400 FPS
63056 frames in 5.0 seconds = 12611.200 FPS
63073 frames in 5.0 seconds = 12614.600 FPS
[/b]**63125 frames in 5.0 seconds = 12625.000 FPS**

Athlon 2600+ 1.9ghz
1GB PC2700 
BFG Geforce 6800 GT OC (AGP)
250gb HD

Bios settings are your biggest kill for FPS loss... BUT I WILL WARN YOU... IT COULD SCREW YOUR SYSTEM UP. NOTE TO SELF REMEMBER WHAT I CHANGE!!

[www.omegadrivers.net](www.omegadrivers.net)  has a VERY GOOD list for your BIOS settings. Follow those and your scores should go up.[/QUOTE]
 when u say cs1.6 at 175 fps, is it the highest at 175 or is stable at 175 ? im assuming that ure using developer 1 command rite ? i tried playing cs via cedega and the fps is not great.. its playable, but for a serious gamer like myself, id rather play in M$ (thats why i have it around for anyways). is there any additional settings that u make in cedega ? im using nv 6600gt and im hoping for a solid 99fps as i would get in windows.. in cedega, im getting 99 when theres nobody, but when it gets a bit crowded, it will go to as low as 50 which is bad! please share any additional settings in cedega if u have.. thanks..

---

### Post by Curlydave on 2005-06-10
The HL engine runs at 100fps, so any extra fps is just discarded... And let's not get into vsync, tearing and refresh rate...

---

### Post by mentalinc on 2005-06-10
68780 frames in 5.0 seconds = 13756.000 FPS
68840 frames in 5.0 seconds = 13768.000 FPS
68820 frames in 5.0 seconds = 13764.000 FPS
68308 frames in 5.0 seconds = 13661.600 FPS


so far looks like im winning  :razz: and i havn't even tweaked anything

mentalinc@ubuntu:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled


Have athlon 64 3200+ 
Nvidia 6800 Ultra 256m  - non pcix
driver: 7174

---

### Post by professor_chaos on 2005-06-10
AMD 3200 1+GB DDR RAM
9787 frames in 5.0 seconds = 1957.400 FPS
11155 frames in 5.0 seconds = 2231.000 FPS
11154 frames in 5.0 seconds = 2230.800 FPS
11156 frames in 5.0 seconds = 2231.200 FPS

---

### Post by simonkitch on 2005-06-11
[QUOTE=jer1ch0]How do you measure the fps  for glxgears?[/QUOTE]
 Open a terminal window an type glxgears. The terminal window gives the output.

---

### Post by Ranime on 2005-06-11
ranime@ishtar:~$ fgl_glxgears
1010 frames in 5.0 seconds = 202.000 FPS
1312 frames in 5.0 seconds = 262.400 FPS
1303 frames in 5.0 seconds = 260.600 FPS
1302 frames in 5.0 seconds = 260.400 FPS
1313 frames in 5.0 seconds = 262.600 FPS
1309 frames in 5.0 seconds = 261.800 FPS
1305 frames in 5.0 seconds = 261.000 FPS

(Desktop 1152*864*24 @ 85Hz)

AMD AthlonXP 2800+ @ 2205MHz (Barton)
512MB PC3200 2-2-2 (2x 256MB Dual Channel DDR)
MSI K7N2 Delta-L mainbord
Club3D Ati Radeon 9600 256MB

---

### Post by DarkKnight on 2005-06-11
17832 frames in 5.0 seconds = 3566.400 FPS
17820 frames in 5.0 seconds = 3564.000 FPS
17843 frames in 5.0 seconds = 3568.600 FPS
17823 frames in 5.0 seconds = 3564.600 FPS

AMD 2500+ @ 3200+
512MB DC DRR400
NVidia GeForce4 Ti 4200 (YeY!)

---

### Post by Wardhog on 2005-06-12
9200se kicks butt:
ward@dingwop:~$ glxgears
2697 frames in 5.0 seconds = 539.400 FPS
3325 frames in 5.0 seconds = 665.000 FPS
3324 frames in 5.0 seconds = 664.800 FPS
3325 frames in 5.0 seconds = 665.000 FPS
3325 frames in 5.0 seconds = 665.000 FPS
3324 frames in 5.0 seconds = 664.800 FPS
3325 frames in 5.0 seconds = 665.000 FPS
3325 frames in 5.0 seconds = 665.000 FPS

Woohoo!  Smokin!

AMD XP 3000+
1024MB Kingston PC3200 RAM
and the Smokin(tm) ATi BEAST9200se!

Got the new ATi drivers in :
ward@dingwop:~$ glxgears
3629 frames in 5.0 seconds = 725.800 FPS
3838 frames in 5.0 seconds = 767.600 FPS
3841 frames in 5.0 seconds = 768.200 FPS
3838 frames in 5.0 seconds = 767.600 FPS
3839 frames in 5.0 seconds = 767.800 FPS
3839 frames in 5.0 seconds = 767.800 FPS
3807 frames in 5.0 seconds = 761.400 FPS
That's a bit better.

---

### Post by rwabel on 2005-06-12
[QUOTE=DarkKnight]17832 frames in 5.0 seconds = 3566.400 FPS
17820 frames in 5.0 seconds = 3564.000 FPS
17843 frames in 5.0 seconds = 3568.600 FPS
17823 frames in 5.0 seconds = 3564.600 FPS

AMD 2500+ @ 3200+
512MB DC DRR400
NVidia GeForce4 Ti 4200 (YeY!)[/QUOTE]

I've also a TI4200 with 128mb ram
how do u get that highscore?

```
rwabel@RALPH:~ $ cat /proc/driver/nvidia/agp/status Status:          Enabled Driver:          NVIDIA AGP Rate:        4x Fast Writes:     Disabled SBA:             Disabled rwabel@RALPH:~ $ glxgears 12128 frames in 5.0 seconds = 2425.600 FPS 13790 frames in 5.0 seconds = 2758.000 FPS 13683 frames in 5.0 seconds = 2736.600 FPS 13787 frames in 5.0 seconds = 2757.400 FPS 13743 frames in 5.0 seconds = 2748.600 FPS 13602 frames in 5.0 seconds = 2720.400 FPS 13447 frames in 5.0 seconds = 2689.400 FPS 13507 frames in 5.0 seconds = 2701.400 FPS 13503 frames in 5.0 seconds = 2700.600 FPS 
``` 

What graphiccard would you guys suggest to replace a TI4200? I've seen that FX5500 aren't any better than the good old TI4200? I'm looking for the best price/quality card :-)

---

### Post by simonkitch on 2005-06-12
[QUOTE=rwabel]I've also a TI4200 with 128mb ram
how do u get that highscore?

```
rwabel@RALPH:~ $ cat /proc/driver/nvidia/agp/status Status:          Enabled Driver:          NVIDIA AGP Rate:        4x Fast Writes:     Disabled SBA:             Disabled rwabel@RALPH:~ $ glxgears 12128 frames in 5.0 seconds = 2425.600 FPS 13790 frames in 5.0 seconds = 2758.000 FPS 13683 frames in 5.0 seconds = 2736.600 FPS 13787 frames in 5.0 seconds = 2757.400 FPS 13743 frames in 5.0 seconds = 2748.600 FPS 13602 frames in 5.0 seconds = 2720.400 FPS 13447 frames in 5.0 seconds = 2689.400 FPS 13507 frames in 5.0 seconds = 2701.400 FPS 13503 frames in 5.0 seconds = 2700.600 FPS 
``` 

What graphiccard would you guys suggest to replace a TI4200? I've seen that FX5500 aren't any better than the good old TI4200? I'm looking for the best price/quality card :-)[/QUOTE]
 Nvidia GT6600.

---

### Post by Snipersnest on 2005-06-12
[QUOTE=Snipersnest]Well this is what I get.. I can play Counter-Strike, CS: Source and most any of the games with about 60-300fps easy. Source is the lowest score for me at 50fps. Counter-Strike 1.6 is my highest at 175fps.. YES PEOPLE EVEN ON LINUX.

My Windows scores are 170-219fps for 1.6 and 100-175fps for Source.
[b]
GLXGEARS SCORE:[/b]
[b]63092 frames in 5.0 seconds = 12618.400 FPS
63056 frames in 5.0 seconds = 12611.200 FPS
63073 frames in 5.0 seconds = 12614.600 FPS
[/b]**63125 frames in 5.0 seconds = 12625.000 FPS**

Athlon 2600+ 1.9ghz
1GB PC2700 
BFG Geforce 6800 GT OC (AGP)
250gb HD

Bios settings are your biggest kill for FPS loss... BUT I WILL WARN YOU... IT COULD SCREW YOUR SYSTEM UP. NOTE TO SELF REMEMBER WHAT I CHANGE!!

[www.omegadrivers.net]("http://www.omegadrivers.net")  has a VERY GOOD list for your BIOS settings. Follow those and your scores should go up.[/QUOTE]

Above is with the 7174 Nvidia drivers you can install from apt-get ... [b]I compiled and installed the 7664 drivers and I got MUCH BETTER FPS scores Take a look:

66354 frames in 5.0 seconds = 13270.800 FPS
66368 frames in 5.0 seconds = 13273.600 FPS
66361 frames in 5.0 seconds = 13272.200 FPS
66362 frames in 5.0 seconds = 13272.400 FPS

[/b]

---

### Post by Stemp on 2005-06-12
5167 frames in 5.0 seconds = 1033.400 FPS
5509 frames in 5.0 seconds = 1101.800 FPS
5509 frames in 5.0 seconds = 1101.800 FPS
5509 frames in 5.0 seconds = 1101.800 FPS

Celeron 2.66 256mo
Ati Radeon 9200 SE (fglrx v. 8.14.13)

---

### Post by Teren on 2005-06-12
teren@v133-4:~$ glxgears
17764 frames in 5.0 seconds = 3552.800 FPS
17649 frames in 5.0 seconds = 3529.800 FPS
17899 frames in 5.0 seconds = 3579.800 FPS
17984 frames in 5.0 seconds = 3596.800 FPS
17876 frames in 5.0 seconds = 3575.200 FPS

I'm planning to get a 6600GT, seems to be an awesome card.

---

### Post by circussideshow on 2005-06-12
i average about 4300-4400

compal cl56
dothan 1.8
1gb pc2700
m11 - 9700 128mb

---

### Post by HungSquirrel on 2005-06-13
11476 frames in 5.0 seconds = 2295.200 FPS

```
$ cat /proc/driver/nvidia/agp/status && cat /proc/cpuinfo | grep MHz
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled
cpu MHz         : 1406.305
```

---

### Post by berserker on 2005-06-13
glxgears
68538 frames in 5.0 seconds = 13707.600 FPS
71051 frames in 5.0 seconds = 14210.200 FPS
71085 frames in 5.0 seconds = 14217.000 FPS
71052 frames in 5.0 seconds = 14210.400 FPS
71085 frames in 5.0 seconds = 14217.000 FPS
71065 frames in 5.0 seconds = 14213.000 FPS

Status:  Enabled
Driver:  AGPGART
AGP Rate:  4x
Fast Writes:  Disabled
SBA:  Disabled

P4 3.06
ASUS P4PE
1 GB RAM
Nvidia GeForce 6800 Ultra
Nvidia Driver 1.0-7664

---

### Post by mentalinc on 2005-06-14
berserker

um how can i put this nicely

why the hell are you using AGP 4x?

change your bios to 8x 

either that or looking at your score its not being detected properly as its within 1000 fps as mine and you have the newer version of the drivers which i to noob to figure out how to install.


basically check that you have it set up right i guess.

can anyone point me to a step by step on how to get the drivers installed - assume i know nothing about how to get ti installed.

---

### Post by rwabel on 2005-06-14
What if he cannot change it up to 8x in the BIOS? In my case I've a TI4200 AGP8x, but as it seems my BIOS only supports 4x. Is the fps difference that significant between 4x and 8x?

[QUOTE=mentalinc]berserker

um how can i put this nicely

why the hell are you using AGP 4x?

change your bios to 8x 

either that or looking at your score its not being detected properly as its within 1000 fps as mine and you have the newer version of the drivers which i to noob to figure out how to install.


basically check that you have it set up right i guess.

can anyone point me to a step by step on how to get the drivers installed - assume i know nothing about how to get ti installed.[/QUOTE]

---

### Post by mentalinc on 2005-06-14
this is true in this case and done my research and yes your correct his motherboard only supports 4x AGP

and no there appears to be no difference - in this test anyway.

however he is using a motherboard from 2002 yet has a top of the line GFX card i suggest he shells out $100 or so and buys him self a nice new motherboard better suited to his nice GFX

---

### Post by rwabel on 2005-06-14
well u bring up a very interesting point. As I'm at the moment having a TI4200 AGP 8x with a Mainboard which is at least 2 years old (only AGP 4x).

I'm also considering to buy a new graphiccard.

When I should also buy a new mainboard, it raises the quesiton, why not also a new cpu, etc etc etc....finally a new computer ;-)

to be serious, is it that bad to have an old mainboard (which still works fine) and then having a 6600GT graphic card?

When buying a Mainboard, then I should perhaps change to a  PCI-E System!

I'm no longer up to date with the hardware stuff, what should I then all change in my computer. I'm having a AMD Athlon XP 2200 and 1GB RAM

In general the hardware is sufficiant for my needs, only gaming is a bit a problem

thanks

---

### Post by berserker on 2005-06-14
mentalinc,

Thanks for the tip on buying a new MB.  The one I have is still sufficient for now.

Try this [post](http://ubuntuforums.org/showthread.php?t=39743)  to install the latest drivers from Nvidia.

---

### Post by JConnell on 2005-06-14
32636 frames in 5.0 seconds = 6527.200 FPS
32805 frames in 5.0 seconds = 6561.000 FPS
32780 frames in 5.0 seconds = 6556.000 FPS
32643 frames in 5.0 seconds = 6528.600 FPS

Athlon 64 3000+
Gigabyte 6600GT
2GB PC-3200 DDR (Dual Channel)

---

### Post by Wardhog on 2005-06-14
[QUOTE=Stemp]5167 frames in 5.0 seconds = 1033.400 FPS
5509 frames in 5.0 seconds = 1101.800 FPS
5509 frames in 5.0 seconds = 1101.800 FPS
5509 frames in 5.0 seconds = 1101.800 FPS

Celeron 2.66 256mo
Ati Radeon 9200 SE (fglrx v. 8.14.13)[/QUOTE]

Man, I gotta get those new ATI drivers in.  Did you have any trouble installing the 8.14.13 drivers?  Do you have a step-by-step set of instructions you used?

---

### Post by electrosoccertux on 2005-06-14
Oh yeah well I beat all you all:

101050 frames in 5.0 seconds = 21177.800 FPS
99157 frames in 5.0 seconds = 19831.400 FPS
103554 frames in 5.0 seconds = 20710.800 FPS
105889 frames in 5.0 seconds = 21177.800 FPS

Barton 2500+ with water cooled 6800 Ultra clocked at 653/1384.

---

### Post by ubuntu_demon on 2005-06-15
11217 frames in 5.0 seconds = 2243.400 FPS
11825 frames in 5.0 seconds = 2365.000 FPS
11833 frames in 5.0 seconds = 2366.600 FPS
11830 frames in 5.0 seconds = 2366.000 FPS
11830 frames in 5.0 seconds = 2366.000 FPS
11830 frames in 5.0 seconds = 2366.000 FPS

I've got a P4 2.8 ghz with 1 GB DDR (dual) and a geforce 3 ti 200 videocard
I run the 686-smp kernel

---

### Post by macmasterxiv on 2005-06-15
19625 frames in 5.0 seconds = 3925.000 FPS
22664 frames in 5.0 seconds = 4532.800 FPS
22692 frames in 5.0 seconds = 4538.400 FPS
22620 frames in 5.0 seconds = 4524.000 FPS
22600 frames in 5.0 seconds = 4520.000 FPS
22601 frames in 5.0 seconds = 4520.200 FPS

A64 2800+ @ 2.4ghz
512mb RAM
Radeon 9800 Pro

---

### Post by endy on 2005-06-15
68460 frames in 5.0 seconds = 13692.000 FPS
68452 frames in 5.0 seconds = 13690.400 FPS
68457 frames in 5.0 seconds = 13691.400 FPS
68476 frames in 5.0 seconds = 13695.200 FPS
68450 frames in 5.0 seconds = 13690.000 FPS

AMD64 3500+ (x86 Ubuntu used)
GeForce 6800GT (Leadtek, PCIe)
1GB PC3200 RAM

---

### Post by Ride Jib on 2005-06-15
WTF is wrong with my computer?

# cat /proc/driver/nvidia/agp/status && cat /proc/cpuinfo | grep MHz
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled
cpu MHz         : 2003.307

# glxgears
9763 frames in 5.0 seconds = 1952.600 FPS
12075 frames in 5.0 seconds = 2415.000 FPS
12076 frames in 5.0 seconds = 2415.200 FPS
12071 frames in 5.0 seconds = 2414.200 FPS
12075 frames in 5.0 seconds = 2415.000 FPS
12077 frames in 5.0 seconds = 2415.400 FPS
12069 frames in 5.0 seconds = 2413.800 FPS


Computer specs in signature....

---

### Post by endy on 2005-06-16
My old PC has a nVidia 5700 in it and IIRC that gave similar results (it doens't have a monitor connected right now so I can't test it). I would consider your 5700 LE to be the bottle neck.  :???: 

However, glxgears is not a real benchmark and if your system runs your games ok and you're happy then it doesn't matter what glxgears says  :)

---

### Post by electrosoccertux on 2005-06-16
[QUOTE=electrosoccertux]Oh yeah well I beat all you all:

101050 frames in 5.0 seconds = 21177.800 FPS
99157 frames in 5.0 seconds = 19831.400 FPS
103554 frames in 5.0 seconds = 20710.800 FPS
105889 frames in 5.0 seconds = 21177.800 FPS

Barton 2500+ with water cooled 6800 Ultra clocked at 653/1384.[/QUOTE]

LOL I wish I had this. I don't think this is possible. Sorry to let you down.

I've got a Riva TNT2 with ~200fps.

I'm just about to buy a 6600GT tho, if that counts.

---

### Post by senectus on 2005-06-16
IBM thinkpad A31p
with 64 meg ATI piece of crap onboard..
4698 frames in 5.0 seconds = 939.600 FPS
5522 frames in 5.0 seconds = 1104.400 FPS
5490 frames in 5.0 seconds = 1098.000 FPS
5523 frames in 5.0 seconds = 1104.600 FPS
5427 frames in 5.0 seconds = 1085.400 FPS


:-( 
I used to get better but hoary did something nasty to my OpenGL capabilities.. now I can't even run OpenGL screensavers

---

### Post by skoal on 2005-06-17
[QUOTE=electrosoccertux]Oh yeah well I beat all you all:[...] Barton 2500+ with water cooled 6800 Ultra clocked at 653/1384.[/QUOTE]
Nice scores!  Water cooled and overclocked eh?.  How often do you scrub those control rods before your case becomes a mini Chernobyl?

\\//_

---

### Post by leohart on 2005-06-17
[QUOTE=equilibrium]$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled
$ glxgears
59145 frames in 5.0 seconds = 11829.000 FPS
59045 frames in 5.0 seconds = 11809.000 FPS

CPU: p4 2.8c @ 3.5Ghz
GPU: nvidia 6800le 16pipes
RAM: 1gb PC3200
KERNEL:  2.6.10-5-686-smp

 :grin:[/QUOTE]

Awesome ^_^ :razz: 

Here is my specs (while listening to music and downloading some stuff)
50091 frames in 5.0 seconds = 10018.200 FPS
78750 frames in 5.0 seconds = 15750.000 FPS
79833 frames in 5.0 seconds = 15966.600 FPS
79779 frames in 5.0 seconds = 15955.800 FPS
75918 frames in 5.0 seconds = 15183.600 FPS

Specs:
AMD64 3400+ 939-pin
2GB Dual Channel DDR3200 (4 x 512MB Corsair VS)
BFG Nvidia 6800 (haven't OCed yet, thinking of using RivaTuner)

[B]Nevermind my above FPS, it drops down to an average of 9600 now.

Hmm, interesting. when I am using RthymBox then it tops up to 15k again no idea why. It should decreases not increases  :roll: [/B]  :^o

---

### Post by firas on 2005-06-17
43528 frames in 5.0 seconds = 8705.600 FPS
43529 frames in 5.0 seconds = 8705.800 FPS
43514 frames in 5.0 seconds = 8702.800 FPS
43517 frames in 5.0 seconds = 8703.400 FPS

CPU: Intel(R) Pentium(R) 4 CPU 3.20GHz
Video: GeForce FX 5900 Ultra
 RAM: Kingston 2 GB PC3200
 KERNEL:  2.6.10-5-686-smp

$ cat /proc/driver/nvidia/version 
NVRM version: NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 200

$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:           AGPGART
AGP Rate:      8x
Fast Writes:    Disabled
SBA:               Enabled

---

### Post by benplaut on 2005-06-17
I HAVE FOUND IT!

THE SECRET TO GETTING HIGH SCORES IN GLXGEARS!

this is on my mobile radeon 7500 (64mb):

> ben@ben:~$ glxgears
19934 frames in 5.0 seconds = 3986.800 FPS
42200 frames in 5.0 seconds = 8440.000 FPS
42295 frames in 5.0 seconds = 8459.000 FPS
40634 frames in 5.0 seconds = 8126.800 FPS
42282 frames in 5.0 seconds = 8456.400 FPS
42261 frames in 5.0 seconds = 8452.200 FPS
41796 frames in 5.0 seconds = 8359.200 FPS


[SIZE=1]switch to another desktop while it's running [/SIZE] \\:D/ 

 :roll:

---

### Post by mp3guy on 2005-06-18
Pentium 4 2.4GHz @ 2.61GHz
512MB DDR 400MHz PC3200 Ram
GeForce 3 Ti 500 64MB AGPX4

15787 frames in 5.0 seconds = 3157.400 FPS

---

### Post by keyshawn on 2005-06-19
Ack...I need to figure out how to improve my results !


Vendor: GenuineIntel
Speed: 2406.142 MHz
Model:  IntelR PentiumR 4 CPU 2.40GHz
512 MB DDR [i forget what Mhz]
kernel:2.6.10-5-386
Video card: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
[hmm...I thought it was a 5200X series, *shrugs* maybe it wasn't detected correctly] [64 MB]

**My results [with firefox running in the background]**

 ```
1469 frames in 5.0 seconds = 293.800 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1469 frames in 5.0 seconds = 293.800 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1469 frames in 5.0 seconds = 293.800 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1469 frames in 5.0 seconds = 293.800 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1469 frames in 5.0 seconds = 293.800 FPS

``` 

Do I win the Bart Simpson award for underachievement ? \\:D/

[b]My new and improved results, after installing the nvidia drivers - thanks to a wiki page, which I can't find now....

[/b] ```
2051 frames in 5.0 seconds = 410.200 FPS
2035 frames in 5.0 seconds = 407.000 FPS
1886 frames in 5.0 seconds = 377.200 FPS
1962 frames in 5.0 seconds = 392.400 FPS
2026 frames in 5.0 seconds = 405.200 FPS
2040 frames in 5.0 seconds = 408.000 FPS
2041 frames in 5.0 seconds = 408.200 FPS
2044 frames in 5.0 seconds = 408.800 FPS

``` 

I'm presuming my linux config files need to be edited, since I'm able to run counterstrike on windows with no problems, except for the occasional lag, due to 20-30 players on the server....

I'm able to run nexiuz fairly well now :D 
cya,
keyshawn

---

### Post by hard_i on 2005-06-21
wee..  got my fx5200 replaced to ati 9600pro + 1GB of RAM .. yeah,i know nvidia card would be better and i don't like ati anyway ..
 , but since i got_it_all_for_free  , then i'm not complaining.  :) 

14523 frames in 5.0 seconds = 2904.600 FPS
14522 frames in 5.0 seconds = 2904.400 FPS
14523 frames in 5.0 seconds = 2904.600 FPS
14523 frames in 5.0 seconds = 2904.600 FPS

with fx5200 i got ~1400 FPS

---

### Post by -Rick- on 2005-06-21
In FreeBSD:
18368 frames in 5.0 seconds = 3673.600 FPS
20600 frames in 5.0 seconds = 4120.000 FPS
20605 frames in 5.0 seconds = 4121.000 FPS
20541 frames in 5.0 seconds = 4108.200 FPS
20618 frames in 5.0 seconds = 4123.600 FPS
20572 frames in 5.0 seconds = 4114.400 FPS
20531 frames in 5.0 seconds = 4106.200 FPS
20605 frames in 5.0 seconds = 4121.000 FPS
20226 frames in 5.0 seconds = 4045.200 FPS

I think its slightly lower on ubuntu

Specs: Athlon XP 1800+ with a gf ti 4800

---

### Post by dezgot on 2005-06-21
[QUOTE=-Rick-]In FreeBSD:
18368 frames in 5.0 seconds = 3673.600 FPS
20600 frames in 5.0 seconds = 4120.000 FPS
20605 frames in 5.0 seconds = 4121.000 FPS
20541 frames in 5.0 seconds = 4108.200 FPS
20618 frames in 5.0 seconds = 4123.600 FPS
20572 frames in 5.0 seconds = 4114.400 FPS
20531 frames in 5.0 seconds = 4106.200 FPS
20605 frames in 5.0 seconds = 4121.000 FPS
20226 frames in 5.0 seconds = 4045.200 FPS

I think its slightly lower on ubuntu

Specs: Athlon XP 1800+ with a gf ti 4800[/QUOTE]
 7166 frames in 5.0 seconds = 1433.200 FPS
7199 frames in 5.0 seconds = 1439.800 FPS
7201 frames in 5.0 seconds = 1440.200 FPS
7035 frames in 5.0 seconds = 1407.000 FPS
7130 frames in 5.0 seconds = 1426.000 FPS
7093 frames in 5.0 seconds = 1418.600 FPS
7117 frames in 5.0 seconds = 1423.400 FPS
7093 frames in 5.0 seconds = 1418.600 FPS
7179 frames in 5.0 seconds = 1435.800 FPS
7129 frames in 5.0 seconds = 1425.800 FPS
7201 frames in 5.0 seconds = 1440.200 FPS
7109 frames in 5.0 seconds = 1421.800 FPS

With my Sony S360 (if anyone else has one please PM me):
Pentium M @ 1.7Ghz
512Mb DDR 2700 (soon to be 1Gb)
ATI Radeon 9700 Mobility 64Mb
Drivers Ubuntu came with:  I couldn't get the new ones to work.  Will there be a package of the newer ones eventually?

Yep, ATI's drivers are crap, this thread proves it.  I thought the ATI linux drivers were just hard to get running, i didn't realize that they were actually far inferior in performance to nVidia's.

---

### Post by nybble on 2005-06-22
$ cat /proc/driver/nvidia/cards/0
Model: GeForce Go 6800
IRQ: 16
Video BIOS: 05.41.02.29.a8
Card Type: PCI-E

$ glxgears
31290 frames in 5.0 seconds = 6258.000 FPS

CPU: Intel Pentium M @ 1.73Ghz (2048kb Cache)
Ram: 1Gb DDR-ish
Kernel: 2.6.10-5-686

This is on a notebook. A [Dell Inspiron 9300](http://www1.ca.dell.com/content/products/productdetails.aspx/inspn_9300?c=ca&cs=CADHS1&l=en&s=dhs).

Wow, that was impressive! ... lol

**nybble**

---

### Post by bgstratt on 2005-06-22
Another way to increase is to cut your color to 16 bit instead of 24/32, that is why MEPIS seemed to run faster than UBUNTU on one of my machines, its (MEPIS's)XFREE86 defaulted to 16 bit instead of the 24 I had running on Xorg in Ubuntu.

This is also why when some upgrading from warty to hoary had a decrease in FPS, the 16 to 24/32 bit color

---

### Post by logic on 2005-06-23
9269 FPS (10 run average, excluding first)

AMD64 3200+ Winchester @ 2410mhz
2x512MB Patriot TCCD @ 2-2-2-5 1T
MSI 6600GT PCI-E @ 575/1225mhz
MSI K8N Neo4 Platinum SLi mobo 
Maxtor DiamondMax 10 300GB hdd (16MB buffer)
76.64 Nvidia drivers
2.6.10-5-686 kernel
KDE version 3.4.0
No special tweaks aside from overclocking, X running at 24/32bit, 1600x1200
100% air-cooled

 \\:D/

---

### Post by artinla on 2005-06-23
OK, someone top this one!

upuranus@oompa-loompa:~$ sh vidinfo.sh
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled
Model:           GeForce 6800 Ultra
IRQ:             16
Video BIOS:      05.40.02.03.00
Card Type:       AGP
cpu MHz         : 2200.114
upuranus@oompa-loompa:~$ glxgears
95278 frames in 5.0 seconds = 19055.600 FPS
104654 frames in 5.0 seconds = 20930.800 FPS
104562 frames in 5.0 seconds = 20912.400 FPS
104653 frames in 5.0 seconds = 20930.600 FPS
104594 frames in 5.0 seconds = 20918.800 FPS
104594 frames in 5.0 seconds = 20918.800 FPS
104016 frames in 5.0 seconds = 20803.200 FPS

AMD FX51
ASUS SK8N Mainboard
BFG 6800 Ultra 256
512M PC2700 ECC DDR
Audigy 2

7174 drivers on a clean Ubuntu install w/24 bit color.

---

### Post by glasscleaner on 2005-06-24
Athlon Xp 2400+
1gb ram
Radeon 9600 Pro Advantage 256mb (446mhz)

6410 frames in 5.0 seconds = 1282.000 FPS
6408 frames in 5.0 seconds = 1281.600 FPS
6420 frames in 5.0 seconds = 1284.000 FPS
6424 frames in 5.0 seconds = 1284.800 FPS


i suck :(

---

### Post by dezgot on 2005-06-26
but you only suck because ATI refuses to write decent linux drivers.  

(or is nVidia's hardware actually better for OpenGL?)

---

### Post by DarkKnight on 2005-06-27
NVidia have always supported OpenGL better then ATI.
And IIRC, NVidia hardware is optimized for OpenGL applications, or favours them, something like that. (It's not -just- drivers)

Personally, I prefer OpenGL over DeflunkedX, Every issue I've had with Linux and graphics has been with my config, in Windblows I get DeflunkedX and config issues.

---

### Post by Omnios on 2005-06-27
glxgears!
3945 frames in 5.0 seconds = 789.000 FPS
3965 frames in 5.0 seconds = 793.000 FPS
3962 frames in 5.0 seconds = 792.400 FPS
3966 frames in 5.0 seconds = 793.200 FPS
3961 frames in 5.0 seconds = 792.200 FPS
3965 frames in 5.0 seconds = 793.000 FPS
3959 frames in 5.0 seconds = 791.800 FPS

 P4 1.6ghz, 256meg ram
Nvidia Gforce2 100/200
64megs

 This is at a color depth setting of 16 and the desktop still looks ok. 
Is this ok to play most games with a 64meg requirment?

 Finaly got around to loading Xfce windows enviorment to check it out for game launching and game performance. 

 Gnome 791fps
 Xfce4   795fps

 On an up note I found the fps to be more consistant in Xfce4. After I install a few games im going to see if they run better in Xfce4 as for some odd reason a low requirement game is unplayable in gnome. Recomend 800ghz "mine 1.6ghz." Also notices my frame rate drops drasticly with odd heavy firewall activity and I mean a huge drop maybe thats why my low end games are unplayable. Anyways Xfce4 may help people with slower systems for game launching just have to log out and log in under Xfce. Also a footnote Xfce has a small footprint 60 megs download and 100meg install I think and it aint all that bad I expected a lot less from it..

---

### Post by mingster on 2005-06-27
ok, why is it doing this???

11954 frames in 5.0 seconds = 2390.800 FPS
15526 frames in 5.0 seconds = 3105.200 FPS
15524 frames in 5.0 seconds = 3104.800 FPS
33159 frames in 5.0 seconds = 6631.800 FPS
40518 frames in 5.0 seconds = 8103.600 FPS
39632 frames in 5.0 seconds = 7926.400 FPS
39970 frames in 5.0 seconds = 7994.000 FPS
40188 frames in 5.0 seconds = 8037.600 FPS
38755 frames in 5.0 seconds = 7751.000 FPS
12435 frames in 5.0 seconds = 2487.000 FPS
14367 frames in 5.0 seconds = 2873.400 FPS
15532 frames in 5.0 seconds = 3106.400 FPS
15525 frames in 5.0 seconds = 3105.000 FPS
15529 frames in 5.0 seconds = 3105.800 FPS
15526 frames in 5.0 seconds = 3105.200 FPS
15529 frames in 5.0 seconds = 3105.800 FPS
15526 frames in 5.0 seconds = 3105.200 FPS
15525 frames in 5.0 seconds = 3105.000 FPS
15530 frames in 5.0 seconds = 3106.000 FPS
15516 frames in 5.0 seconds = 3103.200 FPS
27969 frames in 5.0 seconds = 5593.800 FPS
39008 frames in 5.0 seconds = 7801.600 FPS
40323 frames in 5.0 seconds = 8064.600 FPS
40550 frames in 5.0 seconds = 8110.000 FPS
39676 frames in 5.0 seconds = 7935.200 FPS
39359 frames in 5.0 seconds = 7871.800 FPS
32618 frames in 5.0 seconds = 6523.600 FPS
28405 frames in 5.0 seconds = 5681.000 FPS
15391 frames in 5.0 seconds = 3078.200 FPS
15524 frames in 5.0 seconds = 3104.800 FPS
15311 frames in 5.0 seconds = 3062.200 FPS

the frams rate shoots down when the glxgears window is visible...

radeon 9800 pro
amd64 3000+

---

### Post by skoal on 2005-06-27
Hail Ming! err...Hail mingster!

\\//_

---

### Post by mrt75 on 2005-06-27
10960 frames in 5.0 seconds = 2192.000 FPS
11308 frames in 5.0 seconds = 2261.600 FPS
11306 frames in 5.0 seconds = 2261.200 FPS
11305 frames in 5.0 seconds = 2261.000 FPS
11303 frames in 5.0 seconds = 2260.600 FPS
11312 frames in 5.0 seconds = 2262.400 FPS
11297 frames in 5.0 seconds = 2259.400 FPS
11246 frames in 5.0 seconds = 2249.200 FPS

AMD Athlon 2500+
512MB Ram
128MB ATI Radeon 9800 Pro

---

### Post by ctqucl on 2005-06-28
ctqucl@welcome:~$ glxgears
10282 frames in 5.0 seconds = 2056.400 FPS
11777 frames in 5.0 seconds = 2355.400 FPS
11785 frames in 5.0 seconds = 2357.000 FPS
11786 frames in 5.0 seconds = 2357.200 FPS
11785 frames in 5.0 seconds = 2357.000 FPS
11785 frames in 5.0 seconds = 2357.000 FPS
11784 frames in 5.0 seconds = 2356.800 FPS
Radeon9100 AthlonXP1800+  1G DDR400 RAM
It's enough for me

---

### Post by ctqucl on 2005-06-28
ctqucl@welcome:~$ glxgears
10282 frames in 5.0 seconds = 2056.400 FPS
11777 frames in 5.0 seconds = 2355.400 FPS
11785 frames in 5.0 seconds = 2357.000 FPS
11786 frames in 5.0 seconds = 2357.200 FPS
11785 frames in 5.0 seconds = 2357.000 FPS
11785 frames in 5.0 seconds = 2357.000 FPS
11784 frames in 5.0 seconds = 2356.800 FPS
Radeon9100 -4ns AthlonXP1800+  1G DDR400 RAM
It's enough for me

---

### Post by DarkKnight on 2005-06-29
[QUOTE=mingster]ok, why is it doing this???

11954 frames in 5.0 seconds = 2390.800 FPS
15526 frames in 5.0 seconds = 3105.200 FPS
15524 frames in 5.0 seconds = 3104.800 FPS
33159 frames in 5.0 seconds = 6631.800 FPS
40518 frames in 5.0 seconds = 8103.600 FPS
39632 frames in 5.0 seconds = 7926.400 FPS
39970 frames in 5.0 seconds = 7994.000 FPS
40188 frames in 5.0 seconds = 8037.600 FPS
38755 frames in 5.0 seconds = 7751.000 FPS
12435 frames in 5.0 seconds = 2487.000 FPS
14367 frames in 5.0 seconds = 2873.400 FPS
15532 frames in 5.0 seconds = 3106.400 FPS
15525 frames in 5.0 seconds = 3105.000 FPS
15529 frames in 5.0 seconds = 3105.800 FPS
15526 frames in 5.0 seconds = 3105.200 FPS
15529 frames in 5.0 seconds = 3105.800 FPS
15526 frames in 5.0 seconds = 3105.200 FPS
15525 frames in 5.0 seconds = 3105.000 FPS
15530 frames in 5.0 seconds = 3106.000 FPS
15516 frames in 5.0 seconds = 3103.200 FPS
27969 frames in 5.0 seconds = 5593.800 FPS
39008 frames in 5.0 seconds = 7801.600 FPS
40323 frames in 5.0 seconds = 8064.600 FPS
40550 frames in 5.0 seconds = 8110.000 FPS
39676 frames in 5.0 seconds = 7935.200 FPS
39359 frames in 5.0 seconds = 7871.800 FPS
32618 frames in 5.0 seconds = 6523.600 FPS
28405 frames in 5.0 seconds = 5681.000 FPS
15391 frames in 5.0 seconds = 3078.200 FPS
15524 frames in 5.0 seconds = 3104.800 FPS
15311 frames in 5.0 seconds = 3062.200 FPS

the frams rate shoots down when the glxgears window is visible...

radeon 9800 pro
amd64 3000+[/QUOTE]
 It's doing it because your graphics card doesn't have to reneder the gears onscreen. The operations to render the screen is a lot simpler without moving gears ;) 

17488 frames in 5.0 seconds = 3497.600 FPS
14903 frames in 5.0 seconds = 2980.600 FPS
17560 frames in 5.0 seconds = 3512.000 FPS
43942 frames in 5.0 seconds = 8788.400 FPS
74860 frames in 5.0 seconds = 14972.000 FPS
74404 frames in 5.0 seconds = 14880.800 FPS

You can clearly see where I hide the window.
(AMD 2500+ @ 3200+, GeForce4 Ti 4200)

---

### Post by virgule on 2005-06-29
4.7 fps.. yes thats four dot seven fps :cry:

PowerMac G3/300
'Gossamer' rev2.. whatever that is
320RAM
ATI Mach64  - 6MB VRAM (so-called 3D RAGE II)
1MB L2 backside cache

EDIT: huh oh.. I've been running 'Gears' found in xscreensaver.. wrong test :D
glxgears actual performance is 365 frames in 7.0 seconds = 52.143 FPS

---

### Post by Teroedni on 2005-06-29
15697 frames in 5.0 seconds = 3139.400 FPS
15812 frames in 5.0 seconds = 3162.400 FPS
15813 frames in 5.0 seconds = 3162.600 FPS
15827 frames in 5.0 seconds = 3165.400 FPS
15822 frames in 5.0 seconds = 3164.400 FPS
15823 frames in 5.0 seconds = 3164.600 FPS
15818 frames in 5.0 seconds = 3163.600 FPS
15817 frames in 5.0 seconds = 3163.400 FPS
15816 frames in 5.0 seconds = 3163.200 FPS
15817 frames in 5.0 seconds = 3163.400 FPS
15802 frames in 5.0 seconds = 3160.400 FPS
15816 frames in 5.0 seconds = 3163.200 FPS
15809 frames in 5.0 seconds = 3161.800 FPS
15825 frames in 5.0 seconds = 3165.000 FPS
15803 frames in 5.0 seconds = 3160.600 FPS
15810 frames in 5.0 seconds = 3162.000 FPS
15811 frames in 5.0 seconds = 3162.200 FPS
15811 frames in 5.0 seconds = 3162.200 FPS
15820 frames in 5.0 seconds = 3164.000 FPS


amd athlon 2700 geforce nv25 ti4200
priority normal 0

---

### Post by Yagisan on 2005-06-30
Default Hoary install on amd64. Nvidia binary drivers.
```

jamie@workhorse:~/benchmark$ ./script.sh
Model:           GeForce4 MX 440
IRQ:             16
Video BIOS:      04.17.00.52.00
Card Type:       AGP
model name      : AMD Athlon(tm) 64 Processor 3000+
cpu MHz         : 2010.139
MemTotal:      1540656 kB
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled
Linux workhorse 2.6.10-5-amd64-generic #1 Tue Apr 5 12:21:57 UTC 2005 x86_64 GNU/Linux
NVRM version: NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:45:40 PST 2005
GCC version:  gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
9773 frames in 5.0 seconds = 1954.600 FPS
11355 frames in 5.0 seconds = 2271.000 FPS
11357 frames in 5.0 seconds = 2271.400 FPS
11361 frames in 5.0 seconds = 2272.200 FPS
11348 frames in 5.0 seconds = 2269.600 FPS
11367 frames in 5.0 seconds = 2273.400 FPS
11360 frames in 5.0 seconds = 2272.000 FPS
11363 frames in 5.0 seconds = 2272.600 FPS
11364 frames in 5.0 seconds = 2272.800 FPS
11364 frames in 5.0 seconds = 2272.800 FPS
11358 frames in 5.0 seconds = 2271.600 FPS
11364 frames in 5.0 seconds = 2272.800 FPS

``` 
Enabled fastwrites to see if it made a difference. It didn't.
```

jamie@workhorse:~/benchmark$ ./script.sh
Model:           GeForce4 MX 440
IRQ:             16
Video BIOS:      04.17.00.52.00
Card Type:       AGP
model name      : AMD Athlon(tm) 64 Processor 3000+
cpu MHz         : 2010.139
MemTotal:      1540656 kB
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Enabled
SBA:             Disabled
Linux workhorse 2.6.10-5-amd64-generic #1 Tue Apr 5 12:21:57 UTC 2005 x86_64 GNU/Linux
NVRM version: NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:45:40 PST 2005
GCC version:  gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
9150 frames in 5.0 seconds = 1830.000 FPS
11369 frames in 5.0 seconds = 2273.800 FPS
11363 frames in 5.0 seconds = 2272.600 FPS
11321 frames in 5.0 seconds = 2264.200 FPS
11370 frames in 5.0 seconds = 2274.000 FPS
11367 frames in 5.0 seconds = 2273.400 FPS
11374 frames in 5.0 seconds = 2274.800 FPS
11369 frames in 5.0 seconds = 2273.800 FPS
11368 frames in 5.0 seconds = 2273.600 FPS
11371 frames in 5.0 seconds = 2274.200 FPS
11372 frames in 5.0 seconds = 2274.400 FPS
11368 frames in 5.0 seconds = 2273.600 FPS

```

---

### Post by Hokputooy on 2005-07-02
I get ~2150 fps

AMD Athlon 1.2 ghz overclocked to 1.66
Nvidia geforce 4 mx 440 64mb agp 4x
768mb pc-133

---

### Post by Skye on 2005-07-02
CPU: AMD 3500+
GPU: BFG Nvidia GeForce 6800 GT (core: 370/Memory: 1000)
Ram: 2 x 512 Corsair XMS DDR400

$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:           AGPGART
AGP Rate:      8x
Fast Writes:   Enabled
SBA:              Enabled

$ glxgears
61534 frames in 5.0 seconds = 12306.800 FPS
60834 frames in 5.0 seconds = 12166.800 FPS
61641 frames in 5.0 seconds = 12328.200 FPS
60246 frames in 5.0 seconds = 12049.200 FPS
61487 frames in 5.0 seconds = 12297.400 FPS
61521 frames in 5.0 seconds = 12304.200 FPS

I originally built this PC as a gaming rig, but I've since switched over to mostly linux... although I keep a small windows partition about to play the occasional game on.

Oh, and i almost forgot:  Nvidia drivers from the repositories, kernel 2.6.10-5-k7.

---

### Post by Fiskarn on 2005-07-02
P4 3.0 GHz

Nvidia 6600 GT

1 Gb ram

6344.400 FPS

---

### Post by holr on 2005-07-03
for me: 
10368 frames in 5.0 seconds = 2073.600 FPS
10372 frames in 5.0 seconds = 2074.400 FPS
10380 frames in 5.0 seconds = 2076.000 FPS
10373 frames in 5.0 seconds = 2074.600 FPS
10351 frames in 5.0 seconds = 2070.200 FPS
10305 frames in 5.0 seconds = 2061.000 FPS


im running an ibm t41p laptop, 512mb ram, 1.7 centrino and a mobility fire gl2 graphics card (kinda like a 9600 mobility). 

Using the latest ati-driver-installer-8.14.13 for drivers. When I used the apt-get ones I think i was only getting like 1500 or so...

Been using the original unreal as a testbed for cedega, shame it runs a bit sluggish in wide open spaces :-( runs great in windows (well it is an old game afterall!)

I like using linux/kubuntu as an alternative to windows. but next time i get a computer, its going to have nvidia inside ;-)

---

### Post by t2kburl on 2005-07-03
3 year old system ...

2.5 p4 oc to 2.7
1gb ddr400
nvidia geforce fx 5200
7174 driver from apt

`1000 in kde and gnome
`5000 in fluxbox and icewm

I think I'll be gaming in Fluxbox   :roll:

---

### Post by Error_Msg on 2005-07-03
PII 400Mh 256Mb RAM 10G HD with a 3dfx Voodoo Banshee.
:~$ glxgears
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
libGL warning: 3D driver claims to not support visual 0x35
libGL warning: 3D driver claims to not support visual 0x36
libGL warning: 3D driver claims to not support visual 0x39
libGL warning: 3D driver claims to not support visual 0x3a
libGL warning: 3D driver claims to not support visual 0x3d
libGL warning: 3D driver claims to not support visual 0x3e
libGL warning: 3D driver claims to not support visual 0x41
libGL warning: 3D driver claims to not support visual 0x42
426 frames in 5.0 seconds = 85.200 FPS
226 frames in 5.0 seconds = 45.200 FPS
226 frames in 5.0 seconds = 45.200 FPS
226 frames in 8.0 seconds = 28.250 FPS

E_M

Ps: I got y'all beat! :grin:

---

### Post by t2kburl on 2005-07-03
I tried to update my nvidia drivers to 7667 ....   after it broke X and I got it all put back together, I'm now getting sub 500 fps   ](*,) 

and I can't use nvidia drivers at all
 have to use nv in xorg.conf or X doesn't even start


update ...  got the new driver installed after all ...  I found in another article somewhere (linked from this forum) that informed me I had to remove the restricted kernel modules along with the previous nvidia packages in synaptic prior to installing the downloaded script ... its all good now

back over 1000 fps again  `1200 ... minimal gain for all that work  :roll:

---

### Post by 4rc on 2005-07-04
Hello, a new ubuntu user here. After a long and hard battle I have prevailed and got ATI's new binary drivers installed!  :grin: 

AMD64 3500+ Winchester
ATI X800 XL PCIe
1GB DDR400 RAM

When glxgears is active window:

41365 frames in 5.0 seconds = 8273.000 FPS
41342 frames in 5.0 seconds = 8268.400 FPS
41347 frames in 5.0 seconds = 8269.400 FPS
41349 frames in 5.0 seconds = 8269.800 FPS

When not:

66522 frames in 5.0 seconds = 13304.400 FPS
66498 frames in 5.0 seconds = 13299.600 FPS
66485 frames in 5.0 seconds = 13297.000 FPS
66495 frames in 5.0 seconds = 13299.000 FPS

Quite fast for ATI, no?  :) 

fgl_glxgears

11293 frames in 5.0 seconds = 2258.600 FPS
11300 frames in 5.0 seconds = 2260.000 FPS
11308 frames in 5.0 seconds = 2261.600 FPS
11323 frames in 5.0 seconds = 2264.600 FPS

---

### Post by mingster on 2005-07-04
[QUOTE=DarkKnight]It's doing it because your graphics card doesn't have to reneder the gears onscreen. The operations to render the screen is a lot simpler without moving gears ;) 

17488 frames in 5.0 seconds = 3497.600 FPS
14903 frames in 5.0 seconds = 2980.600 FPS
17560 frames in 5.0 seconds = 3512.000 FPS
43942 frames in 5.0 seconds = 8788.400 FPS
74860 frames in 5.0 seconds = 14972.000 FPS
74404 frames in 5.0 seconds = 14880.800 FPS

You can clearly see where I hide the window.
(AMD 2500+ @ 3200+, GeForce4 Ti 4200)[/QUOTE]


HAHAHAHHAHAAA!!! god, i can be a total retard at times... *hangs head in shame and reinstalls gatesVirus XP*

---

### Post by cyanideoverdose on 2005-07-04
AMD 64 3000+ 1.8ghz
Geforce FX 5200
with coolbits

7270 frames in 5.0 seconds = 1454.000 FPS
7633 frames in 5.0 seconds = 1526.600 FPS
7646 frames in 5.0 seconds = 1529.200 FPS
7640 frames in 5.0 seconds = 1528.000 FPS

I must be doing something wrong...

---

### Post by ponk on 2005-07-11
Intel P4 2.0@2.6ghz
1 gb ram
Radeon 9600pro@XT

14251 frames in 5.0 seconds = 2850.200 FPS
14252 frames in 5.0 seconds = 2850.400 FPS
14253 frames in 5.0 seconds = 2850.600 FPS
14253 frames in 5.0 seconds = 2850.600 FPS
14251 frames in 5.0 seconds = 2850.200 FPS

Ati really sucks.  :-| 

I'm gonna buy gf 6600gt.  \\:D/

---

### Post by Soulfly on 2005-07-11
[QUOTE=t2kburl]3 year old system ...

2.5 p4 oc to 2.7
1gb ddr400
nvidia geforce fx 5200
7174 driver from apt

`1000 in kde and gnome
`5000 in fluxbox and icewm

I think I'll be gaming in Fluxbox   :roll:[/QUOTE]

I'm running KDE and I also see different glxgear behaviour which I think is window-manager related (see below).

I'm running all fps-critical games in a separate x-server though to have a separate gamma-settings for the game and because CTRL-ALT-F7 / CTRL-ALT-F8 is a conveinent way to switch from/to the desktop. I also usually run a less resource-hungry WM/desktop in combination with games (ion3). I think i'll try fluxbox though :)

GeForce FX 5700 LE
Driver: NVIDIA-Linux-x86-1.0-7664-pkg1.run
AMD Athlon(tm) XP 2500+ ( 1837.387 mhz)
1Gb DDR333


In konsole in KDE (from a fresh KDE start, no manually started applications except konsole/glxgears):
```

$ glxgears
11448 frames in 5.0 seconds = 2289.600 FPS
11535 frames in 5.0 seconds = 2307.000 FPS
11536 frames in 5.0 seconds = 2307.200 FPS
11407 frames in 5.0 seconds = 2281.400 FPS
11536 frames in 5.0 seconds = 2307.200 FPS

```

If I run glxgears on a fresh x server (no window manager) I get better results

CTRL-ALT-F2 + login as user
$ echo >gogears "xterm -geometry 80x24+320+0"
$ chmod a+x gogears
$ xinit ./gogears -- :1 vt8

```

$ glxgears
11536 frames in 5.0 seconds = 2307.200 FPS
11734 frames in 5.0 seconds = 2346.800 FPS
11734 frames in 5.0 seconds = 2346.800 FPS
11735 frames in 5.0 seconds = 2347.000 FPS
11735 frames in 5.0 seconds = 2347.000 FPS

```

Logging out of KDE and killing kdm  ( /etc/init.d/kdm stop ) didn't help (stable fps at 2347) . So my guess is that it is the window-manager that is stealing the performance.

For some reason I was unable to run the X-server as a user from within KDE. but starting with sudo here gave not stable results despite new x-server.
<from KDE-konsole> $ sudo xinit ./gogears -- :1 vt8
```

# glxgears
11291 frames in 5.0 seconds = 2258.200 FPS
11366 frames in 5.0 seconds = 2273.200 FPS
11428 frames in 5.0 seconds = 2285.600 FPS
11494 frames in 5.0 seconds = 2298.800 FPS

```

Exiting this x-server I saw that the konsole was outputing things in the terminal window, so I guess these results are because of that.

---

### Post by oneybm on 2005-07-12
I'm  thinking mine may not be configured correctly.  I ran glxgears just for fun and barely got over 1200.

System info:
ECS K7SA Pro
Athlon XP 2000+ (clocked 1667)
Geforce FX 5200 (4X)
512 DDR Ram

---

### Post by RJARRRPCGP on 2005-07-12
[QUOTE=simonkitch]Just enabled coolbits for the Nvidia driver

Before...
kitch@ubuntu:~$ glxgears
30662 frames in 5.0 seconds = 6132.400 FPS
33702 frames in 5.0 seconds = 6740.400 FPS
33686 frames in 5.0 seconds = 6737.200 FPS
33713 frames in 5.0 seconds = 6742.600 FPS

After
kitch@ubuntu:~$ glxgears
36615 frames in 5.0 seconds = 7323.000 FPS
38931 frames in 5.0 seconds = 7786.200 FPS
38912 frames in 5.0 seconds = 7782.400 FPS
38892 frames in 5.0 seconds = 7778.400 FPS

kitch@ubuntu:~$ cat /proc/driver/nvidia/agp/status
Status: Enabled
Driver: AGPGART
AGP Rate: 8x
Fast Writes: Disabled
SBA: Enabled

athlon XP mobile 2500 running at 2 gig
1 gig ram, 266 fsb
NVIDIA 6600GT[/QUOTE]

How can I enable CoolBits under Linux? I was OC'ing with CoolBits under Windows 2000 Pro.

---

### Post by Talamius on 2005-07-13
Not at my PC but I'm only getting around 4400 and 1000-1100 in fgl_glxgears.

Ubuntu 5.04 Hoary with 2.6.10-5-686 kernel
ATI Radeon 9800 Pro with 8.14.13 drivers <--problem
Athlon XP 3000+
1 gig RAM
Audigy 2 ZS sound

From what I've seen nVidia cards seem to give hold a huge OpenGL advantage over ATi cards so I'm going to swap out. I can get a 6600 GT for under $200. Ubuntu has impressed me enough that it's become my everyday use OS so I'm in Linux 99% of the time.

Anyone want to share any horror stories about switching brands of cards? Anything I should be prepared to do besides the obvious? (uninstall fglrx first, etc.)

---

### Post by Fizile on 2005-07-13
44702 frames in 5.0 seconds = 8940.400 FPS
59098 frames in 5.0 seconds = 11819.600 FPS
58816 frames in 5.0 seconds = 11763.200 FPS
57234 frames in 5.0 seconds = 11446.800 FPS
58530 frames in 5.0 seconds = 11706.000 FPS
58243 frames in 5.0 seconds = 11648.600 FPS
58628 frames in 5.0 seconds = 11725.600 FPS
58646 frames in 5.0 seconds = 11729.200 FPS
59236 frames in 5.0 seconds = 11847.200 FPS
57921 frames in 5.0 seconds = 11584.200 FPS
57887 frames in 5.0 seconds = 11577.400 FPS
66644 frames in 5.0 seconds = 13328.800 FPS
57743 frames in 5.0 seconds = 11548.600 FPS
** 71441 frames in 5.0 seconds = 14288.200 FPS
85621 frames in 5.0 seconds = 17124.200 FPS
84751 frames in 5.0 seconds = 16950.200 FPS
85407 frames in 5.0 seconds = 17081.400 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

When i hit the ** i had put the glx gear window behind my firefox window heh.
Ubuntu Hoary 5.04
AMD mobile 2600+ @ 2.3ghz
chaintech 6800gt AGP
512mb kingston value ram...
Biostar m7ncd pro

---

### Post by rwabel on 2005-07-14
[QUOTE=Fizile]44702 frames in 5.0 seconds = 8940.400 FPS
59098 frames in 5.0 seconds = 11819.600 FPS
58816 frames in 5.0 seconds = 11763.200 FPS
57234 frames in 5.0 seconds = 11446.800 FPS
58530 frames in 5.0 seconds = 11706.000 FPS
58243 frames in 5.0 seconds = 11648.600 FPS
58628 frames in 5.0 seconds = 11725.600 FPS
58646 frames in 5.0 seconds = 11729.200 FPS
59236 frames in 5.0 seconds = 11847.200 FPS
57921 frames in 5.0 seconds = 11584.200 FPS
57887 frames in 5.0 seconds = 11577.400 FPS
66644 frames in 5.0 seconds = 13328.800 FPS
57743 frames in 5.0 seconds = 11548.600 FPS
** 71441 frames in 5.0 seconds = 14288.200 FPS
85621 frames in 5.0 seconds = 17124.200 FPS
84751 frames in 5.0 seconds = 16950.200 FPS
85407 frames in 5.0 seconds = 17081.400 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

When i hit the ** i had put the glx gear window behind my firefox window heh.
Ubuntu Hoary 5.04
AMD mobile 2600+ @ 2.3ghz
chaintech 6800gt AGP
512mb kingston value ram...
Biostar m7ncd pro[/QUOTE]
 cat /proc/driver/nvidia/version
NVRM version: NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
GCC version:  gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)

cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

glxgears
19940 frames in 5.0 seconds = 3988.000 FPS
24399 frames in 5.0 seconds = 4879.800 FPS
24563 frames in 5.0 seconds = 4912.600 FPS
24771 frames in 5.0 seconds = 4954.200 FPS
24733 frames in 5.0 seconds = 4946.600 FPS
24731 frames in 5.0 seconds = 4946.200 FPS

I have a MSI 6600GT, my FPS are terrible. What can I do? Normally I should get around 10'000 FPS

---

### Post by Hamman on 2005-07-18
23256 frames in 5.0 seconds = 4651.200 FPS

Sempron 2600+ s754@ 3300+ 250mhz FSB
512mb RAM
Radeon 9600 Pro 400/446 (slower than stock... original is 600 for a Pro card)

---

### Post by Jmonti on 2005-07-18
I get a bit over 13,000 after the 1st run, and it goes up from there, although I never ran it for more than six or seven tests. My other P3 box only gets 200-300  :-|

---

### Post by DarthBagel on 2005-07-18
jonathan@stewie:~$ glxgears
4291 frames in 5.0 seconds = 858.200 FPS
5228 frames in 5.0 seconds = 1045.600 FPS
5229 frames in 5.0 seconds = 1045.800 FPS
6810 frames in 5.0 seconds = 1362.000 FPS
4860 frames in 5.0 seconds = 972.000 FPS
3697 frames in 5.0 seconds = 739.400 FPS


Maybe I should install the newer fglrx dirvers  :?

---

### Post by JayCnrs on 2005-07-18
Well I'm not getting those kind of numbers, but I am doing good a laptop:

jason@stewie:~$ glxgears
2041 frames in 5.0 seconds = 408.200 FPS
2188 frames in 5.0 seconds = 437.600 FPS
2187 frames in 5.0 seconds = 437.400 FPS
2190 frames in 5.0 seconds = 438.000 FPS
2187 frames in 5.0 seconds = 437.400 FPS
2188 frames in 5.0 seconds = 437.600 FPS
2188 frames in 5.0 seconds = 437.600 FPS
2189 frames in 5.0 seconds = 437.800 FPS
2189 frames in 5.0 seconds = 437.800 FPS

jason@stewie:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

I have a Dell 2650, 1.6 ghz, 256 MB RAM with a 16MB GeForce2Go card.

I couldn't get the Ubuntu Nvidia drivers to work, I am using Nvidia 7664 drivers from Nvidia.

---

### Post by losvedir on 2005-07-18
gabedurazo@ubuntu:~$ glxgears
4639 frames in 5.0 seconds = 927.800 FPS
6020 frames in 5.0 seconds = 1204.000 FPS
7458 frames in 5.0 seconds = 1491.600 FPS
7458 frames in 5.0 seconds = 1491.600 FPS
7456 frames in 5.0 seconds = 1491.200 FPS
7416 frames in 5.0 seconds = 1483.200 FPS
7458 frames in 5.0 seconds = 1491.600 FPS

1Ghz Apple powerbook, with 512MB RAM, from about 2.5 years ago.

---

### Post by Darh on 2005-07-21
$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        2x
Fast Writes:     Disabled
SBA:             Disabled
$ glxgears
3535 frames in 5.0 seconds = 707.000 FPS
3989 frames in 5.0 seconds = 797.800 FPS
3984 frames in 5.0 seconds = 796.800 FPS

PII Klamath 266Mhz
192MB SD Ram
Abit Siluro GF 32MB

---

### Post by Bandit on 2005-07-22
11355 frames in 5.0 seconds = 2271.000 FPS
12467 frames in 5.0 seconds = 2493.400 FPS
12521 frames in 5.0 seconds = 2504.200 FPS
12483 frames in 5.0 seconds = 2496.600 FPS
12506 frames in 5.0 seconds = 2501.200 FPS
12494 frames in 5.0 seconds = 2498.800 FPS
12564 frames in 5.0 seconds = 2512.800 FPS


AMD 2400+ @ 2.1GHz
1GB PC2100
Gigabyte FX5500 256MB 128bit (running at only AGP 4x)

---

### Post by python_guy on 2005-07-23
I grab this FX5200 from FNAC yesterday (60eu).... isn't it too slow?

4617 frames in 5.0 seconds = 923.400 FPS
(1024x768)
670 frames in 5.0 seconds = 134.000 FPS

cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

mATX SIS741
Sempron 2200+
1G Kingston DDR

---

### Post by strikeforce on 2005-07-24
Pentium 4 3.2 Ghz
1 Gig RAM
Nvidia 6800 GT 128 meg

Glxgears

marc@ubuntu:~$ glxgears
50506 frames in 5.0 seconds = 10101.200 FPS
53780 frames in 5.0 seconds = 10756.000 FPS
53799 frames in 5.0 seconds = 10759.800 FPS
53785 frames in 5.0 seconds = 10757.000 FPS
53792 frames in 5.0 seconds = 10758.400 FPS
53754 frames in 5.0 seconds = 10750.800 FPS
53783 frames in 5.0 seconds = 10756.600 FPS
53776 frames in 5.0 seconds = 10755.200 FPS

---

### Post by shawn on 2005-07-24
shawn@ubuntu:~$ glxgears
36066 frames in 5.0 seconds = 7213.200 FPS
37498 frames in 5.0 seconds = 7499.600 FPS
37498 frames in 5.0 seconds = 7499.600 FPS
37495 frames in 5.0 seconds = 7499.000 FPS
37500 frames in 5.0 seconds = 7500.000 FPS

Whoooo! Beats the 800 I had on my GeForce 4 MX 4000  :) 


Athlon XP 1900+
768MB
BFG GF6600GT OC 128MB

---

### Post by rwabel on 2005-07-24
[QUOTE=shawn]shawn@ubuntu:~$ glxgears
36066 frames in 5.0 seconds = 7213.200 FPS
37498 frames in 5.0 seconds = 7499.600 FPS
37498 frames in 5.0 seconds = 7499.600 FPS
37495 frames in 5.0 seconds = 7499.000 FPS
37500 frames in 5.0 seconds = 7500.000 FPS

Whoooo! Beats the 800 I had on my GeForce 4 MX 4000  :) 


Athlon XP 1900+
768MB
BFG GF6600GT OC 128MB[/QUOTE]
wow that's great, I've GF6600GT 128MB, Athlon XP 2200+ & 1GB RAM, but I only get a bit more than 5000 FPS. I guess I've to install another Ubuntu on another partition to test if somehting with my nvidia drivers is fucked up

---

### Post by shawn on 2005-07-24
Hmmmm, that would have me worried too! Also this mobo is only AGP 4X:

shawn@ubuntu:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

The BFG cards come pre overclocked but you should be kicking my arse sir!

---

### Post by evilghost on 2005-07-24
LeadTek 6800GT AGP, oc'd to 6800 Ultra speeds (400Mhz/1100Mhz).  Using 7667 Nvidia Drivers.

**System Info/etc**:
```

Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0xff000e1b:0x1f004312
Host Bridge:     Intel Corp. 82875P Memory Controller Hub
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f004a1b:0x00000b12
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3

```

**Xorg.conf snippets:**
```

Section "Device"
        Identifier      "NV6600GT"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoDCC"
        Option          "NvAGP"                 "3"
        Option          "RenderAccel"           "true"
        Option          "Coolbits"              "1"
        Option          "NoLogo"
        VideoRam        262144
EndSection

```

**glxgears scores:**
```

luser@400sc:~$ glxgears
59419 frames in 5.0 seconds = 11883.800 FPS
60680 frames in 5.0 seconds = 12136.000 FPS
60670 frames in 5.0 seconds = 12134.000 FPS
60643 frames in 5.0 seconds = 12128.600 FPS
60680 frames in 5.0 seconds = 12136.000 FPS
60659 frames in 5.0 seconds = 12131.800 FPS

```

---

### Post by Vaego on 2005-07-25
21468 frames in 5.0 seconds = 4293.600 FPS
22508 frames in 5.0 seconds = 4501.600 FPS
22506 frames in 5.0 seconds = 4501.200 FPS
22511 frames in 5.0 seconds = 4502.200 FPS
22506 frames in 5.0 seconds = 4501.200 FPS

AMD 64 3200+
512 mb Ram
Geforce 3 @ 230/500

---

### Post by dtfinch on 2005-07-25
david@ubuntu:~$ glxgears
3770 frames in 5.0 seconds = 754.000 FPS
4047 frames in 5.0 seconds = 809.400 FPS
4050 frames in 5.0 seconds = 810.000 FPS
4047 frames in 5.0 seconds = 809.400 FPS

Dell Dimension 2400
Intel 845GV integrated graphics
2.4ghz celeron
512mb ram
1024x768x16bit@85hz

If I maximize the glxgears window, it goes down to 110fps

---

### Post by Teren on 2005-07-26
PCs from my signature, both run @ 24bpp, PC1 - xfce4 - my main pc, PC2 - default Ubuntu - pc for my mom. PC1 has a crappy server motherboard, need to buy a normal one :P.

PC1:
```

$ cat /var/log/Xorg.0.log | grep 'GPU detected'
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce FX 5600

/proc/driver/nvidia/agp/card:
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f000e1b:0x1f004312

/proc/driver/nvidia/agp/host-bridge:
Host Bridge:     Intel Corp. 82875P Memory Controller Hub
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f004a1b:0x00000b12

/proc/driver/nvidia/agp/status:
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled


9881 frames in 5.0 seconds = 1976.200 FPS
11003 frames in 5.0 seconds = 2200.600 FPS
11055 frames in 5.0 seconds = 2211.000 FPS
11052 frames in 5.0 seconds = 2210.400 FPS
11052 frames in 5.0 seconds = 2210.400 FPS
11047 frames in 5.0 seconds = 2209.400 FPS
11019 frames in 5.0 seconds = 2203.800 FPS
10939 frames in 5.0 seconds = 2187.800 FPS
11045 frames in 5.0 seconds = 2209.000 FPS
11042 frames in 5.0 seconds = 2208.400 FPS

```


PC2:
```

$ cat /var/log/Xorg.0.log | grep 'GPU detected'
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce2 GTS/GeForce2 Pro

/proc/driver/nvidia/agp/card:
Fast Writes:   Supported
SBA:     Not Supported
AGP Rates:   4x 2x 1x
Registers:   0x1f000017:0x1f000104

/proc/driver/nvidia/agp/host-bridge:
Host Bridge:   Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub
Fast Writes:   Not Supported
SBA:     Supported
AGP Rates:   4x 2x 1x
Registers:   0x1f000207:0x00000104

/proc/driver/nvidia/agp/status:
Status:    Enabled
Driver:    AGPGART
AGP Rate:    4x
Fast Writes:   Disabled
SBA:     Disabled

$ glxgears
7316 frames in 5.0 seconds = 1463.200 FPS
7316 frames in 5.0 seconds = 1463.200 FPS
7318 frames in 5.0 seconds = 1463.600 FPS
7315 frames in 5.0 seconds = 1463.000 FPS
7316 frames in 5.0 seconds = 1463.200 FPS
7315 frames in 5.0 seconds = 1463.000 FPS
7308 frames in 5.0 seconds = 1461.600 FPS
7315 frames in 5.0 seconds = 1463.000 FPS
7308 frames in 5.0 seconds = 1461.600 FPS

```

---

### Post by smack on 2005-07-26
smack@smack:~$ glxgears
59790 frames in 5.0 seconds = 11958.000 FPS
60076 frames in 5.0 seconds = 12015.200 FPS
60079 frames in 5.0 seconds = 12015.800 FPS
60102 frames in 5.0 seconds = 12020.400 FPS
60069 frames in 5.0 seconds = 12013.800 FPS

 :)  7800GTX and opteron 1.4

---

### Post by Norrad on 2005-07-28
1360 FPS Average  ](*,) 

System:
AMD XP 2600+
512MB Ram
Geforce FX5200

---

### Post by Yagisan on 2005-07-30
I got an upgrade :) Stock 6800LE (no softmodding yet)
```
jamie@workhorse:~/benchmark$ ./script.sh
Model:           GeForce 6800 LE
IRQ:             16
Video BIOS:      05.40.02.26.00
Card Type:       AGP
model name      : AMD Athlon(tm) 64 Processor 3000+
cpu MHz         : 2010.082
MemTotal:      1540600 kB
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled
Linux workhorse 2.6.10-5-amd64-generic #1 Fri Jun 24 16:54:18 UTC 2005 x86_64 GNU/Linux
NVRM version: NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:45:40 PST 2005
GCC version:  gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
44393 frames in 5.0 seconds = 8878.600 FPS
44876 frames in 5.0 seconds = 8975.200 FPS
44869 frames in 5.0 seconds = 8973.800 FPS
44884 frames in 5.0 seconds = 8976.800 FPS
44871 frames in 5.0 seconds = 8974.200 FPS
44874 frames in 5.0 seconds = 8974.800 FPS
44869 frames in 5.0 seconds = 8973.800 FPS
44849 frames in 5.0 seconds = 8969.800 FPS
44871 frames in 5.0 seconds = 8974.200 FPS
44874 frames in 5.0 seconds = 8974.800 FPS
44877 frames in 5.0 seconds = 8975.400 FPS
```

---

### Post by pmj on 2005-07-30
145.400 FPS

Lowest score yet? :)

---

### Post by Yagisan on 2005-08-01
6800LE Softmodded to 12x1,6vp stock speeds (300/700)```
jamie@workhorse:~/benchmark$ ./script.sh
Model:           GeForce 6800 LE
IRQ:             16
Video BIOS:      05.40.02.26.00
Card Type:       AGP
model name      : AMD Athlon(tm) 64 Processor 3000+
cpu MHz         : 2010.139
MemTotal:      1540600 kB
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled
Linux workhorse 2.6.10-5-amd64-generic #1 Fri Jun 24 16:54:18 UTC 2005 x86_64 GNU/Linux
NVRM version: NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:45:40 PST 2005
GCC version:  gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
38791 frames in 5.0 seconds = 7758.200 FPS
47439 frames in 5.0 seconds = 9487.800 FPS
47340 frames in 5.0 seconds = 9468.000 FPS
47445 frames in 5.0 seconds = 9489.000 FPS
47368 frames in 5.0 seconds = 9473.600 FPS
47451 frames in 5.0 seconds = 9490.200 FPS
47459 frames in 5.0 seconds = 9491.800 FPS
47460 frames in 5.0 seconds = 9492.000 FPS
47441 frames in 5.0 seconds = 9488.200 FPS
47436 frames in 5.0 seconds = 9487.200 FPS
47455 frames in 5.0 seconds = 9491.000 FPS
47456 frames in 5.0 seconds = 9491.200 FPS
```

---

### Post by smoon on 2005-08-01
[QUOTE=Norrad]1360 FPS Average  ](*,) 

System:
AMD XP 2600+
512MB Ram
Geforce FX5200[/QUOTE]

:? I got a Mobile Athlonx XP 2600+ that's running at 2.2GHz with 512 MB Ram and a Geforce FX5200 graphicscard. Well, this is what I get:

860 FPS average :(

---

### Post by Sephiriz on 2005-08-01
71360 frames in 5.0 seconds = 14272.000 FPS


I'm running with a GeForce 6800 LE (All 16 pipes are opened up though).

---

### Post by grofaz on 2005-08-01
I'm not sure my nvidia card is set up correctly. Look:

 cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

I have an Nvidia GeForce FX 5600XTP 128mb card and I'm getting 912 fps using the synaptic nvidia driver package. Can anyone help me set this puppy up properly??? Please???

Thanks!

---

### Post by drummer on 2005-08-01
AMD64 3000 (2GHz)
512 Mb RAM
Radeon 9250

1361 FPS (very modest compared to some  :razz: )

---

### Post by Hairy_Palms on 2005-08-01
somethings def wrong with your card grofaz but i cudnt tell you what it was.
everyones marks are soo high! mine are a bit lower

Amd AthlonXP1800+
512mb Ram
64mb Geforce 3

5207.200 FPS

---

### Post by AdmiralSenn on 2005-08-02
31776 frames in 5.0 seconds = 6355.200 FPS


BFG Nvidia fx5500 oc - no overclocking in linux (until I figure out the nvidia driver installation).
Intel Pentium 4 @ 2.4 GHz
256 PC3200 DDR 
And a malfunctioning MSI 6730 motherboard. Woo!

---

### Post by strawberry on 2005-08-02
[-X 

2530 frames in 5.0 seconds = 506.000 FPS

p iii 500@560
384mb sdram
tnt32 pro

 \\:D/

---

### Post by qrazi on 2005-08-03
getting an average of 400 fps, with an celeron @1.06, 320mb pc133 and a 16mb savage4 agp card....

i'm going to put my old voodoo5 5500 in, wonder if that will be any faster.....

---

### Post by drizek on 2005-08-04
[QUOTE=qrazi]getting an average of 400 fps, with an celeron @1.06, 320mb pc133 and a 16mb savage4 agp card....

i'm going to put my old voodoo5 5500 in, wonder if that will be any faster.....[/QUOTE]
7500 with a 2800 @2.5ghz a gig of ram(not like it matters) and 128mb agp 8 6600GT with latest drivers. 

im gonna try to OC the card though, i heard that the new drivers have support for that now. i can probably break 8k with an OC.

---

### Post by polo_step on 2005-08-06
[QUOTE=AdmiralSenn]31776 frames in 5.0 seconds = 6355.200 FPS
BFG Nvidia fx5500 oc - no overclocking in linux (until I figure out the nvidia driver installation).
Intel Pentium 4 @ 2.4 GHz
256 PC3200 DDR 
And a malfunctioning MSI 6730 motherboard. Woo![/QUOTE]

Interesting.

I have a BFG GeForce FX5500oc 128M also.

It's in a box with a AMD Sempron 2200 CPU & 512 of PC2700 memory.  Running glxgears OFFSCREEN, I get:

anonymous@beatdown:~$ glxgears
[change to off-screen]
20280 frames in 5.0 seconds = 4056.000 FPS
20286 frames in 5.0 seconds = 4057.200 FPS

Seems a little anemic compared to the other stuff I'm seeing.

Here's what I have, if anyone has any suggestions:
======================
anonymous@beatdown:~$ cat /var/log/Xorg.0.log | grep 'GPU detected'
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce FX 5500

anonymous@beatdown:~$ cat /proc/driver/nvidia/agp/host-bridge
Host Bridge:     Silicon Integrated Systems [SiS] 741/741GX/M741 Host
Fast Writes:     Not Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f004e0b:0x00000f02

anonymous@beatdown:~$ cat /proc/driver/nvidia/agp/card
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f000e1b:0x1f004302

xorg.conf:
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#	Load	"dri"       [commented out per nVidia instructions]
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option		"NoLogo"

---

### Post by drizek on 2005-08-06
he must have done something different, like minimize the window or something. there is no way that card can get 6k+.

here look at mine

32283 frames in 5.0 seconds = 6456.600 FPS
33766 frames in 5.0 seconds = 6753.200 FPS

and then i minimize it:

59303 frames in 5.0 seconds = 11860.600 FPS
59456 frames in 5.0 seconds = 11891.200 FPS
61223 frames in 5.0 seconds = 12244.600 FPS
59298 frames in 5.0 seconds = 11859.600 FPS

---

### Post by ujin on 2005-08-08
cpu: amd athlon-xp barton 2800+
gpu  geforce 6600 GT 
mem 512 ddr samsung  
mother board asrock k7vta+

glxgears 
                        **  7729.800 fps**

damn my system is slow ! :neutral:

---

### Post by evilghost on 2005-08-08
[QUOTE=ujin]cpu: amd athlon-xp barton 2800+
gpu  geforce 6600 GT 
mem 512 ddr samsung  
mother board asrock k7vta+

glxgears 
                        **  7729.800 fps**

damn my system is slow ! :neutral:[/QUOTE]

You were getting what I was when I was a 6600GT user.  Be sure you're running the newest (7667) drivers, and you've follow some of the optimization threads.  Specifically, check out the UT2004 one I wrote (HOWTO) on how to optimize your 6600 GT card.  Not all sections will apply.

---

### Post by atf487 on 2005-08-08
i got 2200 or so with a 1.2 ghz duron, 256 megs of ram and a geforce fx5700 le with 256 megs of ram. i've been meaning to get more system ram but it hasn't really been an issue.

---

### Post by najames on 2005-09-17
This thread is kind of interesting to scroll through and see all the different machines, what a variety!!   I am not really a gamer, I hope these frame rates are ok for this setup.  Maybe I'll find sumpin for my wife to play to test it out.

Udated Breezy Kubuntu tonight!!

Chaintech NF4 Ultra
AMD64 3000 Winny
Gigabyte 6600 passive cooled
1gig Corsair Valueram

20807 frames in 5.0 seconds = 4161.383 FPS
20813 frames in 5.0 seconds = 4162.460 FPS
20814 frames in 5.0 seconds = 4162.792 FPS
20815 frames in 5.0 seconds = 4162.871 FPS
20816 frames in 5.0 seconds = 4163.132 FPS
20815 frames in 5.0 seconds = 4162.894 FPS
20817 frames in 5.0 seconds = 4163.297 FPS

---

### Post by janga on 2005-09-18
13908 frames in 5.0 seconds = 2781.600 FPS
15157 frames in 5.0 seconds = 3031.400 FPS
15154 frames in 5.0 seconds = 3030.800 FPS
15061 frames in 5.0 seconds = 3012.200 FPS
15146 frames in 5.0 seconds = 3029.200 FPS
15127 frames in 5.0 seconds = 3025.400 FPS
15123 frames in 5.0 seconds = 3024.600 FPS
15077 frames in 5.0 seconds = 3015.400 FPS

CPU Athlon 3000+ Barton
PCB Asus A7N8X-E
RAM 1GB Corsair Value
VGA Xelo GF4 4200 128MB

Actually, my Geforce is running in 4x AGP mode, although it should be capable of 8x.
My xorg.conf setting is "[COLOR=Red]Option   	"NvAGP" "3"[/COLOR]"
Did I get something wrong?

---

### Post by prelude on 2005-09-18
Nvidia 6600GT @ 544 core, 1151 memory 
(note, this is the best speed setting that gives me no artifacts in windows with 3dmark05)

```

43219 frames in 5.0 seconds = 8643.719 FPS
43221 frames in 5.0 seconds = 8644.007 FPS
43173 frames in 5.0 seconds = 8644.505 FPS
43221 frames in 5.0 seconds = 8644.102 FPS

```

stock speeds @ 500 core, 900 memory (shouldnt a 6600GT have higher stock ram speeds?)

```

34743 frames in 5.0 seconds = 6948.468 FPS
34744 frames in 5.0 seconds = 6948.753 FPS
34743 frames in 5.0 seconds = 6948.548 FPS
34744 frames in 5.0 seconds = 6948.699 FPS
34748 frames in 5.0 seconds = 6949.544 FPS

```

hardware
Pentium 4 2.5Ghz
1.5GB ram
Leadtech 6600GT 128MB

as for the tweaks, I belive Ive covered them all.
my xorg.conf
```

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"		"true"
	Option		"HWcursor"		"true"
	Option		"NvAgp"			"3"
	Option		"coolbits"		"1"
	Option		"NoLogo"		"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"ConnectedMonitor"	"DFP"
	Option		"IgnoreDisplayDevices"	"CRT"	
EndSection

Section	"Extensions"
	Option		"Composite"		"Enable"
	Option		"RENDER"		"true"
	Option		"DAMAGE"		"true"
EndSection

```

---

### Post by bob_c_b on 2005-09-18
Not mind blowing by any measure...

13951 frames in 5.0 seconds = 2790.200 FPS
13938 frames in 5.0 seconds = 2787.600 FPS
13939 frames in 5.0 seconds = 2787.800 FPS
13941 frames in 5.0 seconds = 2788.200 FPS

Celeron D 3.06, 2x512 Corsair Value, FX5200 128bit

Really missing my old Ti4200 but I will say I get playable frames on Quake III and UT2K4 which is currently about all I play. Might get tipped over the edge if I can't get decent performance on NWN, which I will pick up soon.

---

### Post by Curlydave on 2005-09-18
~5200 fps.  :-?  Gotta love ATI on Linux. (x800 pro)

---

### Post by draugen on 2005-09-19
average just above 6700fps. stock 6600gt agp , amd64 3000+, 1 g ram, nforce3. nvida 7667 drivers on ubuntu64. enabling some tweaks now to se if that helps :)

---

### Post by frodon on 2005-09-19
[QUOTE=ujin]cpu: amd athlon-xp barton 2800+
gpu  geforce 6600 GT 
mem 512 ddr samsung  
mother board asrock k7vta+

glxgears 
                        **  7729.800 fps**

damn my system is slow ! :neutral:[/QUOTE]Really !!!!!
AMD k7 700Mhz
geforce FX5200 PCI
mem 512 SDRAM

glxgears : 1130 FPS and it's enough to play CS !

---

### Post by cutOff on 2005-09-20
[QUOTE=Hairy_Palms]somethings def wrong with your card grofaz but i cudnt tell you what it was.
everyones marks are soo high! mine are a bit lower

Amd AthlonXP1800+
512mb Ram
64mb Geforce 3

5207.200 FPS[/QUOTE]
How can it be?

```
5018 frames in 5.0 seconds = 1003.535 FPS
5017 frames in 5.0 seconds = 1003.324 FPS
5016 frames in 5.0 seconds = 1003.109 FPS
5017 frames in 5.0 seconds = 1003.333 FPS
5016 frames in 5.0 seconds = 1003.146 FPS
``` 
AMD Athlon XP1800+
256mb Ram
64mb Geforce4 mx 440


cutoff@this[09:05:29]:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:01:04 PDT 2005
GCC version:  gcc versión 3.3.6 (Ubuntu 1:3.3.6-8ubuntu1)

cutoff@this[09:06:14]:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

***Xorg.conf***

```
Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 MX 440]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAGP" "1"
        Option          "NoLogo"
        Option          "RenderAccel" "Off"
        Option          "DPMS" "true"
        VideoRam        65536
EndSection
```

---

### Post by fserve on 2005-09-20
geforce 4 mx 440 sux, geforce 3 is better then mx series...


my config
AXP 1700+ @ 200*10 = 2000mhz
512 DDR
MSI K7N2 Delta L
MX440se 250/333 @ 360/433 (using nvclock)

result:
6159 frames in 5.0 seconds = 1231.800 FPS
6243 frames in 5.0 seconds = 1248.600 FPS
5982 frames in 5.0 seconds = 1196.400 FPS

---

### Post by arcticwolf_86 on 2005-09-21
13,540 fps in glxgears    :smile:  :)  \\:D/ 


Athlon64 3000+ 754
nForce3 250 Gb
1 gig DDR333
6800 GT OC

---

### Post by khalil on 2005-09-22
Pentium 3 866mhz
Geforce 3 ti 
256 ram


20906 frames in 5.0 seconds = 4181.200 FPS
27658 frames in 5.0 seconds = 5531.600 FPS
27139 frames in 5.0 seconds = 5427.800 FPS
14806 frames in 5.0 seconds = 2961.200 FPS

---

### Post by cutOff on 2005-09-22
[QUOTE=fserve]geforce 4 mx 440 sux, geforce 3 is better then mx series...
[/QUOTE]
I didn't know, thanks for the info.

---

### Post by qb4ever on 2005-09-22
Somethings wrong here  :neutral: 

Amd athlon xp mobile 2400+ @ 2.5ghz

nvidia FX5700le @500mhz core 440mhz ram
running the newest nvidia driver

18615 frames in 5.0 seconds = 3723.000 FPS
14331 frames in 5.0 seconds = 2866.200 FPS
12229 frames in 5.0 seconds = 2445.800 FPS
12225 frames in 5.0 seconds = 2445.000 FPS
12229 frames in 5.0 seconds = 2445.800 FPS

time to start tweaking...... ](*,)

---

### Post by oneybm on 2005-09-22
Well here is my first post on here... 

>  I'm thinking mine may not be configured correctly. I ran glxgears just for fun and barely got over 1200. 

Sys info then was and still is:
Athonlon XP 2000+
512 MB DDR RAM
FX5200 (4x)
ECS K7S5A (then Pro now normal) Motherboard.

I just ran it on a new install with the 7676 drive and got around 1364 if memory serves.

What am I doing wrong or is that what I should be seeing?

---

### Post by thecdn on 2005-09-26
Well, considering my machine has the following:
X800 XL card
AMD 3500+
2 gb ram
it looks like these numbers pretty much suck:

5500 frames in 5.0 seconds = 1100.000 FPS
6424 frames in 5.0 seconds = 1284.800 FPS
5221 frames in 5.0 seconds = 1044.200 FPS
6384 frames in 5.0 seconds = 1276.800 FPS
6398 frames in 5.0 seconds = 1279.600 FPS
6408 frames in 5.0 seconds = 1281.600 FPS
6383 frames in 5.0 seconds = 1276.600 FPS

I finally got rid of the Mesa drivers info:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XL Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

To repeat the mantra of those with puny numbers like mine, what tweaks/actions can we take to get better results?

---

### Post by Ampersand on 2005-09-27
7321 frames in 5.0 seconds = 1464.089 FPS
7288 frames in 5.0 seconds = 1457.419 FPS
7306 frames in 5.0 seconds = 1461.078 FPS
7307 frames in 5.0 seconds = 1461.323 FPS
7301 frames in 5.0 seconds = 1460.064 FPS

(AMD64 3200+, 128Mb Nvidia 5700 LE, 1Gb ram)

Tweaking time for me as well, possibly...

---

### Post by GameManK on 2005-09-27
glxgears
12735 frames in 5.0 seconds = 2547.000 FPS
14551 frames in 5.0 seconds = 2910.200 FPS
14314 frames in 5.0 seconds = 2862.800 FPS
14545 frames in 5.0 seconds = 2909.000 FPS
14255 frames in 5.0 seconds = 2851.000 FPS

fgl_glxgears
2013 frames in 5.0 seconds = 402.600 FPS
2518 frames in 5.0 seconds = 503.600 FPS
2533 frames in 5.0 seconds = 506.600 FPS
2529 frames in 5.0 seconds = 505.800 FPS
2541 frames in 5.0 seconds = 508.200 FPS

Powercolor ATI Radeon 9800se 256-bit 380/340
Athlon XP Barton @ 180x8
1GB kingston value ram pc3200

---

### Post by katu on 2005-09-27
glxgears:
10480 frames in 5.0 seconds = 2095.865 FPS
10410 frames in 5.0 seconds = 2081.985 FPS
10410 frames in 5.0 seconds = 2081.858 FPS
10260 frames in 5.0 seconds = 2051.888 FPS
10413 frames in 5.0 seconds = 2082.583 FPS
10409 frames in 5.0 seconds = 2081.748 FPS

AMD Barton XP 2500+
Radeon 9200
512 MB Ram...
;)

---

### Post by Perfect Storm on 2005-09-27
23554 frames in 5.0 seconds = 4710.800 FPS
23971 frames in 5.0 seconds = 4794.200 FPS
23976 frames in 5.0 seconds = 4795.200 FPS
23983 frames in 5.0 seconds = 4796.600 FPS
23966 frames in 5.0 seconds = 4793.200 FPS
23978 frames in 5.0 seconds = 4795.600 FPS

P4 2,4 ghz 1024 mb, gf4 ti4600 128mb

---

### Post by bob_c_b on 2005-09-28
[QUOTE=bob_c_b]Not mind blowing by any measure...
13951 frames in 5.0 seconds = 2790.200 FPS
13938 frames in 5.0 seconds = 2787.600 FPS
13939 frames in 5.0 seconds = 2787.800 FPS
13941 frames in 5.0 seconds = 2788.200 FPS
Celeron D 3.06, 2x512 Corsair Value, FX5200 128bit
Really missing my old Ti4200 but I will say I get playable frames on Quake III and UT2K4 which is currently about all I play. Might get tipped over the edge if I can't get decent performance on NWN, which I will pick up soon.[/QUOTE]
Got my hands on a 6200 AGP (HSI bridge model so unlocked pipes are a possibility) and got these results....
bob@phobos:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled
bob@phobos:~$ glxgears
17096 frames in 5.0 seconds = 3419.200 FPS
18105 frames in 5.0 seconds = 3621.000 FPS
18100 frames in 5.0 seconds = 3620.000 FPS
18096 frames in 5.0 seconds = 3619.200 FPS
18103 frames in 5.0 seconds = 3620.600 FPS
18105 frames in 5.0 seconds = 3621.000 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
bob@phobos:~$


more importanly I got a huge boost in Doom 3 performance and can now pull steady 60fps @ 800x600.

---

### Post by llebegue on 2005-09-30
7600 frames in 5.0 seconds = 1520.000 FPS
7645 frames in 5.0 seconds = 1529.000 FPS
7608 frames in 5.0 seconds = 1521.600 FPS
7497 frames in 5.0 seconds = 1499.400 FPS
5853 frames in 5.0 seconds = 1170.600 FPS
8023 frames in 5.0 seconds = 1604.600 FPS
9780 frames in 5.0 seconds = 1956.000 FPS
8695 frames in 5.0 seconds = 1739.000 FPS
12153 frames in 5.0 seconds = 2430.600 FPS
12182 frames in 5.0 seconds = 2436.400 FPS
12130 frames in 5.0 seconds = 2426.000 FPS
12171 frames in 5.0 seconds = 2434.200 FPS
12173 frames in 5.0 seconds = 2434.600 FPS
12167 frames in 5.0 seconds = 2433.400 FPS
8383 frames in 5.0 seconds = 1676.600 FPS
9341 frames in 5.0 seconds = 1868.200 FPS
12065 frames in 5.0 seconds = 2413.000 FPS
9902 frames in 5.0 seconds = 1980.400 FPS
9983 frames in 5.0 seconds = 1996.600 FPS
11867 frames in 5.0 seconds = 2373.400 FPS
11909 frames in 5.0 seconds = 2381.800 FPS
11758 frames in 5.0 seconds = 2351.600 FPS
12018 frames in 5.0 seconds = 2403.600 FPS
11593 frames in 5.0 seconds = 2318.600 FPS
11336 frames in 5.0 seconds = 2267.200 FPS
12126 frames in 5.0 seconds = 2425.200 FPS
12075 frames in 5.0 seconds = 2415.000 FPS
10476 frames in 5.0 seconds = 2095.200 FPS
8511 frames in 5.0 seconds = 1702.200 FPS
8167 frames in 5.0 seconds = 1633.400 FPS
11787 frames in 5.0 seconds = 2357.400 FPS
11333 frames in 5.0 seconds = 2266.600 FPS
11099 frames in 5.0 seconds = 2219.800 FPS
9531 frames in 5.0 seconds = 1906.200 FPS
7588 frames in 5.0 seconds = 1517.600 FPS
9367 frames in 5.0 seconds = 1873.400 FPS
9940 frames in 5.0 seconds = 1988.000 FPS
10878 frames in 5.0 seconds = 2175.600 FPS
8056 frames in 5.0 seconds = 1611.200 FPS
11385 frames in 5.0 seconds = 2277.000 FPS
9846 frames in 5.0 seconds = 1969.200 FPS
11837 frames in 5.0 seconds = 2367.400 FPS
11884 frames in 5.0 seconds = 2376.800 FPS
10116 frames in 5.0 seconds = 2023.200 FPS
10309 frames in 5.0 seconds = 2061.800 FPS
7305 frames in 5.0 seconds = 1461.000 FPS
10923 frames in 5.0 seconds = 2184.600 FPS
11142 frames in 5.0 seconds = 2228.400 FPS
9049 frames in 5.0 seconds = 1809.800 FPS
11739 frames in 5.0 seconds = 2347.800 FPS
8134 frames in 5.0 seconds = 1626.800 FPS
10442 frames in 5.0 seconds = 2088.400 FPS
11918 frames in 5.0 seconds = 2383.600 FPS
11728 frames in 5.0 seconds = 2345.600 FPS
11864 frames in 5.0 seconds = 2372.800 FPS
11932 frames in 5.0 seconds = 2386.400 FPS
11639 frames in 5.0 seconds = 2327.800 FPS
11875 frames in 5.0 seconds = 2375.000 FPS
12030 frames in 5.0 seconds = 2406.000 FPS
7881 frames in 5.0 seconds = 1576.200 FPS
9289 frames in 5.0 seconds = 1857.800 FPS
11566 frames in 5.0 seconds = 2313.200 FPS
8501 frames in 5.0 seconds = 1700.200 FPS
8102 frames in 5.0 seconds = 1620.400 FPS


Guess it's around 1700 FPS

AMD 2800+
ATI Radeon X800XT / AGP 8x
2Go DDR

---

### Post by fsshl on 2005-09-30
would I ask hwo to get that glxgear number?  execute what command in Ubuntu(I use 5.10)?

---

### Post by 23meg on 2005-10-01
2250 - 2500 fps with Nvidia Geforce Go6200 64MB on a Pentium M 1.73ghz Sonoma laptop as opposed to 900 - 1000 fps on my old P4 laptop with ATI Mobility Radeon 7500.

---

### Post by Velox Letum on 2005-10-01
[QUOTE=fsshl]would I ask hwo to get that glxgear number?  execute what command in Ubuntu(I use 5.10)?[/QUOTE]
Just type *glxgears* into a terminal and execute it.

---

### Post by fsshl on 2005-10-01
[QUOTE=Velox Letum]Just type *glxgears* into a terminal and execute it.[/QUOTE]
it showed a window with 3 gears, blue, yellow, red
I let it run about 5 minutes, then close the window
it did not reponse any fps number

I also tried glxgears OFFSCREEN
it reponse bad parameter OFFSCREEN

I alos tried
cat /var/log/Xorg.0.log | grep 'GPU detected'
it reponse notheing

I am in 5.10, kernel 2.6.12-9 

I also read above posts, tried 
~# fgl_glxgears
bash: fgl_glxgears: command not found

please help, fsshl

---

### Post by Yagisan on 2005-10-01
[QUOTE=fsshl]it showed a window with 3 gears, blue, yellow, red
I let it run about 5 minutes, then close the window
it did not reponse any fps number
[/QUOTE] try looking in the terminal you typed glxgears in.

---

### Post by mthaddon on 2005-10-01
you may also need to use the inane switch:

glxgears -iacknowledgethatthistoolisnotabenchmark

Thanks, Tom

---

### Post by fsshl on 2005-10-01
thanks Tom, it works, mine is 272.828 FPS
on P4M, sl6cg 1.6Ghz 478 512Kb/400fsb
Matsonic 9127C motherboard
AGP x2 x4 powercolor 64MB video card
1G ddr266

---

### Post by WhoKnows on 2005-10-01
18790 frames in 5.0 seconds = 3758.000 FPS
18780 frames in 5.0 seconds = 3756.000 FPS
18799 frames in 5.0 seconds = 3759.800 FPS
18629 frames in 5.0 seconds = 3725.800 FPS


P3 1ghz, 384 sdram, Ti4200.

---

### Post by Some_Bored_Dude on 2005-10-02
Pentium 4 - 2.4GHz 533fsb
1GB Ram
Geforce 6600GT
Fresh Install of Ubuntu (Not the 1st install, just 1st install on this PC)

40411 frames in 5.0 seconds = 8082.200 FPS
61253 frames in 5.0 seconds = 12250.600 FPS
61935 frames in 5.0 seconds = 12387.000 FPS
61979 frames in 5.0 seconds = 12395.800 FPS
61951 frames in 5.0 seconds = 12390.200 FPS
61982 frames in 5.0 seconds = 12396.400 FPS
61921 frames in 5.0 seconds = 12384.200 FPS

Screenshot attached. :cool: 

[IMG]http://fastcars.org.au/sbd/scaledsh.jpg[/IMG]

---

### Post by rlange on 2005-10-08
100403 frames in 5.0 seconds = 20080.600 FPS
99314 frames in 5.0 seconds = 19862.800 FPS
100433 frames in 5.0 seconds = 20086.600 FPS
99242 frames in 5.0 seconds = 19848.400 FPS
100276 frames in 5.0 seconds = 20055.200 FPS
99263 frames in 5.0 seconds = 19852.600 FPS
100315 frames in 5.0 seconds = 20063.000 FPS
:smile: 


System specs:
AMD 3500 64 bit
1GB Ram
evga 6800GT
MSI Neo2 Plat

---

### Post by liquidtenmillion on 2005-10-08
Resolution and color depth make a HUGE difference on these results.  Mine is 1024x768@24

anthony@Pismire:~$ glxgears
4849 frames in 5.0 seconds = 969.800 FPS
5936 frames in 5.0 seconds = 1187.200 FPS
5928 frames in 5.0 seconds = 1185.600 FPS
5887 frames in 5.0 seconds = 1177.400 FPS
5890 frames in 5.0 seconds = 1178.000 FPS
5888 frames in 5.0 seconds = 1177.600 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
anthony@Pismire:~$


Pentium 3 800mhz
Nvidia Geforce FX5200 128mb(regular PCI card, not pci express or agp)
Kernel 2.6.13

And with vsync enabled i get:

anthony@Pismire:~$ glxgears
259 frames in 5.0 seconds = 51.800 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS

anthony@Pismire:~$


My monitor's refresh rate has a max of 60hz(it's a 13" monitor)

---

### Post by Curlydave on 2005-10-08
~7000. I'm using an x800pro, and I'm getting beat by 6600GT's. W00t!!! (I just love ATI when using Linux. :???: ) 

So, who has a 6800GT that wants to switch with me? :)

---

### Post by Curlydave on 2005-10-08
[QUOTE=liquidtenmillion]
And with vsync enabled i get:

anthony@Pismire:~$ glxgears
259 frames in 5.0 seconds = 51.800 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS

anthony@Pismire:~$


My monitor's refresh rate has a max of 60hz(it's a 13" monitor)[/QUOTE]

Don't get me wrong-- I love Vsync and ALWAYS have it enabled in games (in Windows--- it won't work on ATI in Linux as far as I can tell.:mad: ) However, the one time i would turn off vsync is for any type of framerate test, as it will completely mess it up as it caps your framerate.

---

### Post by BLTicklemonster on 2005-10-09
Yikes. I'm a total newb, and am having problems here.

Check this out:
> bill@ubuntumonster:~$ cat /proc/driver/nvidia/agp/status
cat: /proc/driver/nvidia/agp/status: No such file or directory
bill@ubuntumonster:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
1499 frames in 5.0 seconds = 299.800 FPS
1689 frames in 5.0 seconds = 337.800 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1808 frames in 5.0 seconds = 361.600 FPS
1695 frames in 5.0 seconds = 339.000 FPS


Hmmm, no agp... but it's an agp card... must install drivers, eh? well, how easy is that? Not easy at all, and I'm afraid to mess with going to the command prompt again. I got stuck in "no-x server-ville" earlier and had to reinstall ubuntu, so unless I can install the nvidia drivers without going to the command line, I'm kinda thinking maybe I'm stuck with windows. Which is unacceptable. 

So I get all synaptic and try installing everything that says xlib and or xfree, but there's no making XFree86-DRI show up. I then go to check on Nvidia drivers, nope a bunch missing. So I get all synaptic on them, too. And I get this error:
> 
E: /cdrom//pool/restricted/l/linux-restricted-modules-2.6.10/nvidia-glx_1.0.7174-0ubuntu1_i386.deb:  subprocess pre-installation script returned error exit status 2

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

So ah, shoot. What now? How can I get nvidia-glx to install in synaptic?

I really really really want to get unreal tournament playing at higher than 2 fps!!!

---

### Post by dcarpenter on 2005-10-09
24327 frames in 5.0 seconds = 4865.206 FPS
24293 frames in 5.0 seconds = 4858.591 FPS
24291 frames in 5.0 seconds = 4858.058 FPS
24289 frames in 5.0 seconds = 4857.643 FPS

Intel P4 3.2ghz
Intel D875PBZ Motherboard
1Gb Corsair XMS low latency ram
ATI Radeon 9800xt

---

### Post by skyhorse on 2005-10-10
skyhorse@skybuntu:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
10291 frames in 5.0 seconds = 2058.139 FPS
10262 frames in 5.0 seconds = 2052.398 FPS
10260 frames in 5.0 seconds = 2051.876 FPS
10220 frames in 5.0 seconds = 2043.961 FPS

skyhorse@skybuntu:~$ fgl_glxgears
993 frames in 5.0 seconds = 198.600 FPS
1216 frames in 5.0 seconds = 243.200 FPS
1225 frames in 5.0 seconds = 245.000 FPS
1217 frames in 5.0 seconds = 243.400 FPS
1216 frames in 5.0 seconds = 243.200 FPS

Acer Aspire 1600:
512 RAM
P4 @ 2.8
ATI Radeon Mobility 9000

---

### Post by davidjneff on 2005-10-10
[QUOTE=Error_Msg]PII 400Mh 256Mb RAM 10G HD with a 3dfx Voodoo Banshee.
:~$ glxgears
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
libGL warning: 3D driver claims to not support visual 0x35
libGL warning: 3D driver claims to not support visual 0x36
libGL warning: 3D driver claims to not support visual 0x39
libGL warning: 3D driver claims to not support visual 0x3a
libGL warning: 3D driver claims to not support visual 0x3d
libGL warning: 3D driver claims to not support visual 0x3e
libGL warning: 3D driver claims to not support visual 0x41
libGL warning: 3D driver claims to not support visual 0x42
426 frames in 5.0 seconds = 85.200 FPS
226 frames in 5.0 seconds = 45.200 FPS
226 frames in 5.0 seconds = 45.200 FPS
226 frames in 8.0 seconds = 28.250 FPS

E_M

Ps: I got y'all beat! :grin:[/QUOTE]

I have a similar system, Celeron, 450Mhz, 128megs RAM, Voodoo3.  Just put ubunto onto it to dual boot with Windows98.  Get the same error messages and similar speeds.  After tweaking down the color depth to 16 and screen resolution to 1024x768, it doubled my glxgears speed from 50 to 107!!  Wooo hoo!  My x11 log file confirms it is using DRI.

So, you still have me beat.  Was going to ask if my speed was as good as it gets on such an old system, and I guess it is.  Older 3d games are quite playable on this in Win98, but not on Ubuntu -- I assume the tdfx driver doesn't take full advantage of the card?  I guess I can quit fiddling, and work harder on convincing the wife to let me buy a new, but bare bones, Linux box for Ubuntu.  I had a hard time believing this was as good as it could be, given how much better the card works in Win98 :confused: 

Tried the glx driver as an option, but it didn't find the screen.  Oddly, on a different Linux debian distribution, this used to work -- until I got a new monitor -- which even broke the live CD (mepis) that used to work with my old monitor.  But I didn't know enough then how to do the speed tests then.  My new monitor has a very long plug and play name, and I wonder if that is confusing glx -- it seems to find the Voodoo3 card fine,  but then barfs on no default display.  Odd.  Will try a different monitor one of these days.  Amazing that replacing a monitor can make a live CD not work ...

I also have ubunto on an old laptop, also dual booted, with an ATI graphics chip -- glxgears gets around 2500 on that.

---

### Post by Kirzzy_Boy on 2005-10-11
34090 frames in 5.0 seconds = 6818.000 FPS
34097 frames in 5.0 seconds = 6819.400 FPS
34700 frames in 5.0 seconds = 6940.000 FPS
34619 frames in 5.0 seconds = 6923.800 FPS
34735 frames in 5.0 seconds = 6947.000 FPS
34456 frames in 5.0 seconds = 6891.200 FPS

XP3000+
MSI FX5900XT

---

### Post by GameManK on 2005-10-11
[QUOTE=GameManK]glxgears
12735 frames in 5.0 seconds = 2547.000 FPS
14551 frames in 5.0 seconds = 2910.200 FPS
14314 frames in 5.0 seconds = 2862.800 FPS
14545 frames in 5.0 seconds = 2909.000 FPS
14255 frames in 5.0 seconds = 2851.000 FPS

fgl_glxgears
2013 frames in 5.0 seconds = 402.600 FPS
2518 frames in 5.0 seconds = 503.600 FPS
2533 frames in 5.0 seconds = 506.600 FPS
2529 frames in 5.0 seconds = 505.800 FPS
2541 frames in 5.0 seconds = 508.200 FPS

Powercolor ATI Radeon 9800se 256-bit 380/340
Athlon XP Barton @ 180x8
1GB kingston value ram pc3200[/QUOTE]

[A little overclocking for ATI]("http://ubuntuforums.org/showthread.php?t=74049"), and nearly a 20% improvement!!

Core: 411.75 MHz, Mem: 351.0 MHz
yuriy@YURIKU:~/rovclock-0.6b$ glxgears
14031 frames in 5.0 seconds = 2806.200 FPS
16925 frames in 5.0 seconds = 3385.000 FPS
17010 frames in 5.0 seconds = 3402.000 FPS
16752 frames in 5.0 seconds = 3350.400 FPS
16959 frames in 5.0 seconds = 3391.800 FPS
yuriy@YURIKU:~/rovclock-0.6b$ fgl_glxgears
2792 frames in 5.0 seconds = 558.400 FPS
3020 frames in 5.0 seconds = 604.000 FPS
3024 frames in 5.0 seconds = 604.800 FPS
2997 frames in 5.0 seconds = 599.400 FPS
3033 frames in 5.0 seconds = 606.600 FPS

---

### Post by qewl on 2005-10-16
128MB GeForce 6800

At first (when web browser was covering gears):

70725 frames in 5.0 seconds = 14144.930 FPS
70747 frames in 5.0 seconds = 14149.257 FPS
70743 frames in 5.0 seconds = 14148.538 FPS

Then after I activated the gears window:

40823 frames in 5.0 seconds = 8164.597 FPS
40833 frames in 5.0 seconds = 8166.589 FPS
40823 frames in 5.0 seconds = 8164.479 FPS

Interesting that you have to highlight the window to get accurate results.. Also resolution affects the rate. Wish glxgears was less influenceable but still very handy.
(All on 1280x1024)

Also freezes old ATI based laptop when window is dragged. Only 326 FPS there.

---

### Post by sanjose on 2005-10-16
P4 @ 3.2 Ghz 
2GB ram
ATI Radeon 7200 64mb

19049 frames in 5.0 seconds = 3809.767 FPS
29463 frames in 5.0 seconds = 5892.563 FPS
16575 frames in 5.0 seconds = 3314.969 FPS
16577 frames in 5.0 seconds = 3315.337 FPS
16211 frames in 5.0 seconds = 3242.016 FPS

---

### Post by Quartus on 2005-10-16
P4 512Kb 2.6 @ 1.3 :D 
512 Mb x 2 Dual
ATI 9200 SE (128 Mb)

glxgears:
5375 frames in 5.0 seconds = 1074.946 FPS
5375 frames in 5.0 seconds = 1074.946 FPS
5375 frames in 5.0 seconds = 1074.930 FPS
5375 frames in 5.0 seconds = 1074.959 FPS
(I got around 500 FPS with the open sauce drivers)

fgl_glxgears:
676 frames in 5.0 seconds = 135.200 FPS
705 frames in 5.0 seconds = 141.000 FPS
709 frames in 5.0 seconds = 141.800 FPS
682 frames in 5.0 seconds = 136.400 FPS

It's good to have some power when you're running xpenguins. :D

---

### Post by colonelpanic on 2005-10-17
Radeon 9200
Athlon 750MHz
256MB RAM

glxgears:
10026 frames in 5.0 seconds = 2005.200 FPS
10022 frames in 5.0 seconds = 2004.400 FPS
10026 frames in 5.0 seconds = 2005.200 FPS
10027 frames in 5.0 seconds = 2005.400 FPS
10027 frames in 5.0 seconds = 2005.400 FPS
10027 frames in 5.0 seconds = 2005.400 FPS
10025 frames in 5.0 seconds = 2005.000 FPS
10027 frames in 5.0 seconds = 2005.400 FPS
10028 frames in 5.0 seconds = 2005.600 FPS

glxinfo:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 DDR Generic
OpenGL version string: 1.3.1003 (X4.3.0-8.14.13)

Oh, and I'm running Gentoo... could be why the FPS is kind of high for an old Athlon and a lowly Radeon 9200. Three cheers for architecture-specific optimizations! Yay!

----
By all means... *do* panic.

---

### Post by SilentCacophony on 2005-10-19
Some good tips here. :) Made my old mish-mash dinosaur of a computer more than double on glxgears.

**System specs:**
CPU: Pentium III 600Mhz
GPU: 32MB GeForce2 MX 200
MB : GVC QS440BX
RAM: 448MB PC100 SDRAM

```
brian@ubuntu:~$ glxgears -printfps
4230 frames in 5.0 seconds = 845.996 FPS
4236 frames in 5.0 seconds = 847.195 FPS
4236 frames in 5.0 seconds = 847.088 FPS
4231 frames in 5.0 seconds = 846.084 FPS
4238 frames in 5.0 seconds = 847.423 FPS
4233 frames in 5.0 seconds = 846.563 FPS
4232 frames in 5.0 seconds = 846.203 FPS
4238 frames in 5.0 seconds = 847.409 FPS
4234 frames in 5.0 seconds = 846.776 FPS
4232 frames in 5.0 seconds = 846.254 FPS
```
```
brian@ubuntu:~$ cat /proc/driver/nvidia/agp/card
Fast Writes:     Not Supported
SBA:             Not Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000007:0x1f000102

brian@ubuntu:~$ cat /proc/driver/nvidia/agp/host-bridge
Host Bridge:     Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
Fast Writes:     Not Supported
SBA:             Supported
AGP Rates:       2x 1x
Registers:       0x1f000203:0x00000102

brian@ubuntu:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        2x
Fast Writes:     Disabled
SBA:             Disabled

From /etc/X11/xorg.conf:

Section "Module"
	# Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	# Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"		"true"
	Option          "NvAGP"                 "3"
	Option		"RenderAccel"		"true"
EndSection
```

---

### Post by clearnitesky on 2005-11-02
AMD Sempron 3000+
GeForce 5500FX, AGP 8X, 256MB
512MB RAM

and I'm clocking out glxgears @ between 2300 and 3000 FPS
but I really don't know if it's configured properly... I'm sure it used to be different when I was using slackware, but I don't remember if it was better or worse!

---

### Post by Yagisan on 2005-11-04
Updated to breezy:
6800LE Softmodded to 12x1,6vp stock speeds (300/700)
```
(amd64)jamie@doomguy:~/benchmark$ ./script.sh
Model:           GeForce 6800 LE
IRQ:             16
Video BIOS:      05.40.02.26.00
Card Type:       AGP
model name      : AMD Athlon(tm) 64 Processor 3000+
cpu MHz         : 2010.139
MemTotal:      1538888 kB
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled
Linux doomguy 2.6.12-9-amd64-k8 #1 Mon Oct 10 13:13:36 BST 2005 x86_64 GNU/Linux
NVRM version: NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:14:03 PDT 2005
GCC version:  gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)
43057 frames in 5.0 seconds = 8611.256 FPS
42522 frames in 5.0 seconds = 8504.240 FPS
41816 frames in 5.0 seconds = 8363.176 FPS
42622 frames in 5.0 seconds = 8524.241 FPS
42269 frames in 5.0 seconds = 8453.786 FPS
42478 frames in 5.0 seconds = 8495.519 FPS
42289 frames in 5.0 seconds = 8455.636 FPS
42335 frames in 5.0 seconds = 8466.993 FPS
42684 frames in 5.0 seconds = 8536.702 FPS
42466 frames in 5.0 seconds = 8492.962 FPS
42327 frames in 5.0 seconds = 8465.359 FPS
```
6800LE Softmodded to 12x1,6vp maximum stable overclock (375/875)
```
(amd64)jamie@doomguy:~/benchmark$ ./script.sh
Model:           GeForce 6800 LE
IRQ:             16
Video BIOS:      05.40.02.26.00
Card Type:       AGP
model name      : AMD Athlon(tm) 64 Processor 3000+
cpu MHz         : 2010.139
MemTotal:      1538888 kB
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled
Linux doomguy 2.6.12-9-amd64-k8 #1 Mon Oct 10 13:13:36 BST 2005 x86_64 GNU/Linux
NVRM version: NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:14:03 PDT 2005
GCC version:  gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)
55826 frames in 5.0 seconds = 11165.166 FPS
55377 frames in 5.0 seconds = 11075.400 FPS
55293 frames in 5.0 seconds = 11058.552 FPS
55341 frames in 5.0 seconds = 11068.055 FPS
55465 frames in 5.0 seconds = 11092.915 FPS
55422 frames in 5.0 seconds = 11084.376 FPS
55415 frames in 5.0 seconds = 11082.880 FPS
55431 frames in 5.0 seconds = 11086.134 FPS
55221 frames in 5.0 seconds = 11043.789 FPS
55280 frames in 5.0 seconds = 11055.849 FPS
55303 frames in 5.0 seconds = 11060.159 FPS
```
Compared to hoary, I drop 1000FPS in glxgears, do I care no - glxgears isn't a game ;)

---

### Post by proditaki on 2005-11-20
60172 frames in 5.0 seconds = 12034.312 FPS
62144 frames in 5.3 seconds = 11690.138 FPS
68042 frames in 5.0 seconds = 13608.366 FPS
71847 frames in 5.5 seconds = 13146.263 FPS
73661 frames in 5.0 seconds = 14729.375 FPS
74687 frames in 5.0 seconds = 14937.357 FPS
80536 frames in 5.0 seconds = 16107.126 FPS
78632 frames in 5.0 seconds = 15662.762 FPS
78312 frames in 5.0 seconds = 15662.286 FPS
78301 frames in 5.0 seconds = 15660.084 FPS
78207 frames in 5.0 seconds = 15641.263 FPS

AMD64 3000+, Geforce 6800 GT

---

### Post by Cuppa-Chino on 2005-11-20
ATI drivers, oh ATI drivers do we not love you......

_P4 2.4 GHz FSB 800 1GB RAM DDR400 Radeon 9500 @ 9700 Core: 276.75 MHz Mem: 270MHz_
[B]
3542fps[/B]

_P4 2.4 GHz FSB 800 1GB RAM DDR400 Radeon 9500 @ 9700 Pro Core: 324 MHz Mem: 310.50MHz_

**4097fps**

_P4 2.4 GHz @ 3.0 GHz FSB 1000 1GB RAM DDR500 Radeon 9500 @ 9700 Core: 276.75 MHz Mem: 270MHz_

**3544fps**

_P4 2.4 GHz @ 3.0 GHz FSB 1000 1GB RAM DDR500 Radeon 9500 @ 9700 Pro Core: 324 MHz Mem: 310.50MHz_

**4100fps**

[COLOR="Red"]**don't you love the team in red from Canada**[/COLOR]

---

### Post by sciurus on 2005-11-21
Ati 8.16.20

Athlon XP 2600
1GB PC-2700
Radeon 9800 Pro

at the default windows size:
23229 frames in 5.0 seconds = 4645.795 FPS

maximized at 1600X1200
2054 frames in 5.0 seconds = 410.705 FPS

---

### Post by chronusdark on 2005-11-22
how the heck do you get benchmarks when i run glxgears it just goes forever and never does anything

---

### Post by berserker on 2005-11-22
[QUOTE=chronusdark]how the heck do you get benchmarks when i run glxgears it just goes forever and never does anything[/QUOTE]

```
glxgears -printfps
```

---

### Post by chronusdark on 2005-11-23
lhanners@gigabyte:~$ glxgears -printfps
37023 frames in 5.0 seconds = 7404.580 FPS
38955 frames in 5.0 seconds = 7790.839 FPS
39047 frames in 5.0 seconds = 7809.311 FPS
39034 frames in 5.0 seconds = 7806.667 FPS
39050 frames in 5.0 seconds = 7809.996 FPS
38961 frames in 5.0 seconds = 7792.166 FPS
38442 frames in 5.0 seconds = 7688.383 FPS


thats what i got my specs are 
AMD athlon 64 3000+
512 MB ram 
Geforce FX 5900 128DDR
Nforce 3 Motherboard by gigabyte

are my fps good for my specs?

---

### Post by lysis on 2005-12-04
normal

9682 frames in 5.0 seconds = 1936.349 FPS
9596 frames in 5.0 seconds = 1919.047 FPS
13746 frames in 5.0 seconds = 2749.076 FPS
11433 frames in 5.0 seconds = 2286.552 FPS
15149 frames in 5.0 seconds = 3029.657 FPS
14986 frames in 5.0 seconds = 2997.158 FPS
10388 frames in 5.0 seconds = 2077.407 FPS
9602 frames in 5.0 seconds = 1920.243 FPS
9529 frames in 5.0 seconds = 1905.660 FPS


if i make the window as small as it can be . . .

53647 frames in 5.0 seconds = 10729.371 FPS
56574 frames in 5.0 seconds = 11314.660 FPS
59808 frames in 5.0 seconds = 11961.523 FPS
57435 frames in 5.0 seconds = 11486.845 FPS
56201 frames in 5.0 seconds = 11240.168 FPS
56635 frames in 5.0 seconds = 11326.980 FPS
58051 frames in 5.0 seconds = 11610.107 FPS
57662 frames in 5.0 seconds = 11532.381 FPS




any way to get this to perform better?

---

### Post by WTF_Shelley on 2005-12-10
i only get 7475 with a sempron 754 and a gf6600gt is that good? ahhh f**k it it £250 comp upgrade:razz:

---

### Post by viscount on 2005-12-11
Is there some other way to find out my fps?
For some strange reason glxgears doesn't display
the fsp readout in the terminal, but otherwise it seems
to be working properly.

Im getting no ouput at all from glxgears in my terminal.

---

### Post by Cuppa-Chino on 2005-12-11
[QUOTE=WTF_Shelley]i only get 7475 with a sempron 754 and a gf6600gt is that good? ahhh f**k it it £250 comp upgrade:razz:[/QUOTE]

what are you upgrading to? and what is happening to your poor old gf6600gt? ;)

---

### Post by Pc_AdDiCt on 2005-12-11
:( something is VERY off here :???: 

21374 frames in 5.0 seconds = 4274.768 FPS

got 8300~ in gentoo

AMD64 3500+
1024MB PC3700
6600GT 128MB PCIE

any ideas? everything seems to be ok tried many drivers, the ones in repository seems to be working best 1.0.7667

edit: typo :p

edit2:

after trying 3 different ubuntu kernels and 3 different nvidia drivers and never getting above 4200~ fps i decided to try something different ;)

what i did was i copied my gentoo kernel over to my ubuntu install and reinstalled nvidia-kernel & nvidia-glx and ended up with this :p

37070 frames in 5.0 seconds = 7413.948 FPS

not the same as iv'e had earlier, but it should suffice for the moment ;)

---

### Post by berserker on 2005-12-11
[QUOTE=viscount]Im getting no ouput at all from glxgears in my terminal.[/QUOTE]

```
glxgears -printfps
```

---

### Post by ubu-for on 2005-12-11
Hello!

My hardware:
Abit KN8 SLI
AMD64 4000+
OCZ DIMM 1 GB DDR-400 Platinum EL
NVIDIA 6600 GT, PCIe, 256 MB
Samsung SP2504C, SATA II

My software:
Ubuntu 5.10, 32bit
nvidia-glx 1.07667
kernel 2.6.12-9-386

glxgears:
30007 frames in 5.0 seconds = 6001.321 FPS
30023 frames in 5.0 seconds = 6004.540 FPS
30025 frames in 5.0 seconds = 6004.876 FPS

After the installation of nvidia-glx, glxgears showed about 6.000 FPS. :( 

Because of tv-out, I've modified my xorg.conf. One restart later, glxgears showed about 11.000 FPS! :D

After another restart, I've the same low rate as before. 6.000 FPS! :confused:

Few days before, I had installed SUSE Linux 10.0 Evaluation. Started glxgears. And the tooth wheels turned very fast (don't remember FPS) compared to Ubuntu (can count every tooth of the wheels).

Does anybody have an idea how to modify Ubuntu for better (best) results? I don't want to run Win XP parallel!

THX for your help!

P.S. CSS via Wine 0.9.2 showes only DirectX 6 (hardware) and DirectX 9 (software).

---

### Post by erikpiper on 2005-12-11
around 270 with an Anthlon 64 3000-
And an nvidea 2 with 8 mb ram/synaptic upgrading things in the backround. :)

---

### Post by Mamay on 2005-12-17
Hello,

Here are my benchmarks for glxgears:p :

73751 frames in 5.0 seconds = 14750.200 FPS
73822 frames in 5.0 seconds = 14764.400 FPS
73802 frames in 5.0 seconds = 14760.400 FPS
73803 frames in 5.0 seconds = 14760.600 FPS
73752 frames in 5.0 seconds = 14750.400 FPS
73763 frames in 5.0 seconds = 14752.600 FPS


My specs:

Dual Opteron 248
2Gb Ram
GeForce 6800 Ultra/PCI-E/SSE2
Gentoo  Linux (2.6.14-gentoo-r2) 2005.1 (64bit, opteron optimised)

---

### Post by python on 2005-12-22
glxgears IS NOT a benchmark test. but...

29013 frames in 5.0 seconds = 5802.513 FPS

intel centrino 1.7 MHz
512Mb RAM
ati radeon 9600 mobility
etc

pleasing.

---

### Post by iceonnet on 2006-01-01
_GeForce 3 Ti 200_

Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

$ glxgears -printfps
11483 frames in 5.0 seconds = 2309.560 FPS

---

### Post by buellman on 2006-01-01
```

martin@cyclone:~$ glxgears -printfps
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
*********************************WARN_ONCE*********************************
File r300_render.c function r300_get_num_verts line 188
user error: Need more than 2 vertices to draw primitive QS !
***************************************************************************
7639 frames in 5.0 seconds = 1527.724 FPS
7572 frames in 5.0 seconds = 1511.817 FPS
7663 frames in 5.0 seconds = 1532.207 FPS
7770 frames in 5.0 seconds = 1553.886 FPS
7566 frames in 5.0 seconds = 1513.019 FPS
7833 frames in 5.0 seconds = 1566.445 FPS
7838 frames in 5.0 seconds = 1567.411 FPS
7800 frames in 5.0 seconds = 1559.990 FPS
7837 frames in 5.0 seconds = 1567.234 FPS
7836 frames in 5.0 seconds = 1567.146 FPS
7808 frames in 5.0 seconds = 1561.408 FPS
7835 frames in 5.0 seconds = 1566.949 FPS

```
Hardware:
Asus A7N8X-E Deluxe
AMD Athlon XP 2000+
2x MDT DD-Ram 256MB
Club3D ATI Radeon 9600 Pro 128MB
Western Digital WD400JB 40GB 8MB cache

Software:
Ubuntu 6.04 Dapper Drake, 32-bit
r300-driver
kernel 2.6.15-10-k7

Greets. Buellman

---

### Post by newuser111 on 2006-01-01
pentium 4 3.0 HT
512 ram
ATI x700 pro PCI-e

notice the big difference in fps using the different glxgears commands

**fgl_glxgears**
Using GLX_SGIX_pbuffer
6187 frames in 5.0 seconds = 1237.400 FPS
8607 frames in 5.0 seconds = 1721.400 FPS
8563 frames in 5.0 seconds = 1712.600 FPS
9060 frames in 5.0 seconds = 1812.000 FPS
9046 frames in 5.0 seconds = 1809.200 FPS
8519 frames in 5.0 seconds = 1703.800 FPS
8687 frames in 5.0 seconds = 1737.400 FPS
8997 frames in 5.0 seconds = 1799.400 FPS
9055 frames in 5.0 seconds = 1811.000 FPS
9004 frames in 5.0 seconds = 1800.800 FPS
8938 frames in 5.0 seconds = 1787.600 FPS
8698 frames in 5.0 seconds = 1739.600 FPS
8807 frames in 5.0 seconds = 1761.400 FPS
9088 frames in 5.0 seconds = 1817.600 FPS

**glxgears -printfps**
26689 frames in 5.0 seconds = 5337.634 FPS
26817 frames in 5.0 seconds = 5363.282 FPS
48521 frames in 5.0 seconds = 9704.124 FPS
49751 frames in 5.0 seconds = 9950.048 FPS
46970 frames in 5.0 seconds = 9393.953 FPS
49870 frames in 5.0 seconds = 9973.926 FPS
50148 frames in 5.0 seconds = 10029.583 FPS
50389 frames in 5.0 seconds = 10077.796 FPS
40215 frames in 5.0 seconds = 8042.940 FPS
46386 frames in 5.0 seconds = 9277.152 FPS
47310 frames in 5.0 seconds = 9461.984 FPS

---

### Post by newuser111 on 2006-01-01
i recommend installing the ati drives as shown here [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) if you used a different method before

but always use fglrxconfig to generate your xorg.conf file, rather than a different command, since it creates the best xorg.conf

---

### Post by richardjones on 2006-01-05
AMD64 3500+   (running the K8 kernel)
nvidia 7800GT    (PCI-X)
2GB RAM

53580 frames in 5.0 seconds = 10715.830 FPS
56472 frames in 5.0 seconds = 11294.271 FPS
56622 frames in 5.0 seconds = 11324.392 FPS
56535 frames in 5.0 seconds = 11306.978 FPS
55379 frames in 5.0 seconds = 11075.631 FPS

My old system (Athlon 2800+, nvidia 6800GT (AGP)) got very similar numbers, proving that glxgears is very much CPU-bound and has been for a while :)

---

### Post by richardjones on 2006-01-05
[QUOTE=richardjones]AMD64 3500+   (running the K8 kernel)
nvidia 7800GT    (PCI-X)
2GB RAM

53580 frames in 5.0 seconds = 10715.830 FPS
56472 frames in 5.0 seconds = 11294.271 FPS
56622 frames in 5.0 seconds = 11324.392 FPS
56535 frames in 5.0 seconds = 11306.978 FPS
55379 frames in 5.0 seconds = 11075.631 FPS

My old system (Athlon 2800+, nvidia 6800GT (AGP)) got very similar numbers, proving that glxgears is very much CPU-bound and has been for a while :)[/QUOTE]

Interesting. I just updated to the 8178 nvidia drivers and now get:

54745 frames in 5.0 seconds = 10948.941 FPS
66642 frames in 5.0 seconds = 13328.229 FPS
67047 frames in 5.0 seconds = 13409.381 FPS
67137 frames in 5.0 seconds = 13427.279 FPS
66431 frames in 5.0 seconds = 13286.188 FPS
67357 frames in 5.0 seconds = 13471.327 FPS

---

### Post by knubbe on 2006-01-07
Dell Inspiron 6000
1.40GHz Intel(R) Celeron(R) M processor
i915 mobile chipset (Intel)
2gb ram

5889 frames in 5.0 seconds = 1177.693 FPS
5705 frames in 5.0 seconds = 1140.925 FPS
5788 frames in 5.0 seconds = 1157.488 FPS
5909 frames in 5.0 seconds = 1181.626 FPS
5900 frames in 5.0 seconds = 1179.854 FPS

---

### Post by Navyblue on 2006-01-13
8979 frames in 5.0 seconds = 1795.660 FPS
8979 frames in 5.0 seconds = 1795.667 FPS
8979 frames in 5.0 seconds = 1795.679 FPS
8979 frames in 5.0 seconds = 1795.672 FPS
8979 frames in 5.0 seconds = 1795.634 FPS

Sapphire Radeon 9550 128 bit 128 MB
AMD Athlon 64 2800+
768 MB DDR 400 RAM
Kubuntu 32 bit with fglrx driver from official repository

[COLOR="Red"]**How do you guys get 3-4k fps with low end ATI cards? PLEASE TELL ME!!! :)**[/COLOR]

---

### Post by luka on 2006-01-22
31109 frames in 5.0 seconds = 6221.777 FPS
32650 frames in 5.0 seconds = 6529.962 FPS
32949 frames in 5.0 seconds = 6589.784 FPS
33440 frames in 5.0 seconds = 6687.949 FPS
32886 frames in 5.0 seconds = 6577.075 FPS
33039 frames in 5.0 seconds = 6607.757 FPS

HP Compaq nw8240 (2.13GHz, 1GB RAM)
ATI FireGL V5000 128MB

---

### Post by rippon on 2006-01-22
8500 AVG FPS in glxgears

AMD 3000+ Newcastle (2Ghz)
1GB DDR 400
ATI Radeon x800Pro (256MB AGP 8x)

I get 45-60 FPS in Americas Army on Normal - High settings.
...good 'nough for me.

---

### Post by dcstar on 2006-01-31
21559 frames in 5.0 seconds = 4311.745 FPS

AMD Athlon 2500+

Built in Via UNICHROME video on Gigabyte GA-7VM400M motherboard.

Hmm, because my video shares system RAM, the performance varies greatly depending on how much of the glxgears graphic is actually on the screen!

When it is fully visible, it drops to 2871 frames in 5.0 seconds = 574.170 FPS!!

Lowering my Refresh rate also increases my FPS..........

Still, it is nicer to have hardware acceleration on my Via chipset than not have it......

---

### Post by Tichondrius on 2006-01-31
Athlon 64 3800+, XFX 7800 GTX OC, 2GB RAM, 250GB HD

Glxgears score > 15000 FPS !!!

Quake 4 @1920x1200 High Quality w/4xAA > 100 FPS (avg)

btw, Quake 4 is DA BOMB

---

### Post by mxa055 on 2006-02-01
glxgears launches the program window but doesn't write anything back to the console... :-k 

How can I get fps values?

---

### Post by berserker on 2006-02-01
[QUOTE=mxa055]glxgears launches the program window but doesn't write anything back to the console... :-k 

How can I get fps values?[/QUOTE]

```
glxgears -printfps
```

---

### Post by Mangledbmx on 2006-02-01
im using ubuntu breezy 5.10 i believe and im wondering where i could get glxgears from... any info would be greatly appreciated

---

### Post by dcstar on 2006-02-01
[QUOTE=Mangledbmx]im using ubuntu breezy 5.10 i believe and im wondering where i could get glxgears from... any info would be greatly appreciated[/QUOTE]
It should be part of the xbase-clients transitional package.

---

### Post by dcstar on 2006-02-13
Just another little thing I have found, I could increase my glxgears rate by changing my colour depth (in /etc/Xorg/xorg.conf) from 24 to 16.

I get a ~40% increase, and my display doesn't look that different (to me).

Less data to write to the video card means less time to do it........

---

### Post by enkrypt3d on 2006-02-13
I have noticed something strange about glxgears... with kubuntu 5.04 it will report the FPS in the terminal.....Giving me around 9k-10k FPS  (This is after I get openGL acceleration working of course) and with 5.10 I am unable to get it to report the FPS!? Why is this?

I have a Dell Presicion M70 2.0Ghz Pentium M 2MB L2 and a Nvidia quadro go1400 256MB.... KDE 3.5 and Breezy Badger 5.10... Kernel revision 2.6.12-10-386. Any ideas on how I can get the FPS to show up? I've let it sit there indefinitely and it never shows anything :( :-k 

Games like tuxracer work great and all my OpenGL screensavers are working great....... just wanted to find out what the problem is here?

---

### Post by enkrypt3d on 2006-02-14
anyone? Come on guys I know you know whats up just tell me! :-D

---

### Post by WTF_Shelley on 2006-02-14
glxgears -iacknowledgethatthistoolisnotabenchmark

Im not joking, this will give you fps:D

---

### Post by enkrypt3d on 2006-02-14
LOL you've got to be joking!

Edit: omg i cant believe this actually works!

---

### Post by berserker on 2006-02-14
Or you could use this:

```
glxgears -printfps
```

---

### Post by aeiah on 2006-02-14
```
james@satsuma:~$ glxgears
94798 frames in 5.0 seconds = 18959.473 FPS
94854 frames in 5.0 seconds = 18970.652 FPS
94802 frames in 5.0 seconds = 18960.275 FPS
94806 frames in 5.0 seconds = 18961.109 FPS
94771 frames in 5.0 seconds = 18954.070 FPS
94818 frames in 5.0 seconds = 18963.488 FPS
```

smooth :mrgreen: 

AMD64 3800 X2
2GB ram
Nvidia 7800GT 256mb
ubuntu breezy with 2.6.12-10-k7-smp kernel

---

### Post by alfonz on 2006-02-14
[QUOTE=simonkitch]No mate I just had to reinstall my Nvidia driver now i'm getting :-

kitch@ubuntu:~$ glxgears
31656 frames in 5.0 seconds = 6331.200 FPS
33272 frames in 5.0 seconds = 6654.400 FPS
33279 frames in 5.0 seconds = 6655.800 FPS

No idea how I achieved that first score unfortunatly :([/QUOTE]

minimise fglrxgears window and watch them rise ;)

its probably what u did

---

### Post by mattisking on 2006-02-14
My glxgears score: 11,065 FPS

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Generic
OpenGL version string: 2.0.5582 (8.21.7)

$ glxgears -printfps
55327 frames in 5.0 seconds = 11065.308 FPS
54307 frames in 5.0 seconds = 10856.241 FPS
58915 frames in 5.0 seconds = 11782.895 FPS
57588 frames in 5.0 seconds = 11517.484 FPS
52598 frames in 5.0 seconds = 10519.568 FPS
55833 frames in 5.0 seconds = 11166.566 FPS

ATI X800 All in Wonder
P4 3.0 Gig (Hyperthreading)
1 Gig RAM
Ubuntu Dapper fglrx driver from official repository

---

### Post by Milamber_Cubed on 2006-02-18
Just thought I would toss this in here:

AMD Athlon64 3500+
6600GT 128MB DDR AGP
1GB Crucial Ballistix DDR RAM
Asus A8V Deluxe Mobo

Have been playing with Xgl in a fully updated Dapper (flight 3) install and have the followiing results - rounded down to nearest 100, somtimes more got almost 90fps more than stated result.

(CPU is alway 100% used, is this normal??)

Standard X.org - 7500fps
Xgl without compiz - 5500fps
Xgl and compiz - 12800fps :D

pretty damn sweet!

---

### Post by tlaloczint on 2006-02-21
896 frames in 5.0 seconds = 14179.043 FPS
70756 frames in 5.0 seconds = 14151.151 FPS
70751 frames in 5.0 seconds = 14150.187 FPS
70751 frames in 5.0 seconds = 14150.127 FPS
70732 frames in 5.0 seconds = 14146.292 FPS
70585 frames in 5.0 seconds = 14116.828 FPS
62064 frames in 5.0 seconds = 12412.750 FPS
71094 frames in 5.0 seconds = 14218.754 FPs

amd 64 3500+ newcastlecore
8700 gt nvidia 
2 gb ram 
on this
 glxgears -printfps

but if a do this 
glxgears -iacknowledgethatthistoolisnotabenchmark

I got this 
099 frames in 5.0 seconds = 14219.743 FPS
71535 frames in 5.0 seconds = 14306.929 FPS
71438 frames in 5.0 seconds = 14287.434 FPS
71498 frames in 5.0 seconds = 14299.540 FPS
71549 frames in 5.0 seconds = 14309.617 FPS
70283 frames in 5.0 seconds = 14055.613 FPS

---

### Post by billdoor on 2006-02-21
Athlon T-Bird 900Mhz
384MB PC100 RAM
Radeon 9700 Pro
ASUS KT133A VIA

$ glxgears -printfps
20652 frames in 5.0 seconds = 4130.394 FPS
20727 frames in 5.0 seconds = 4145.381 FPS
20657 frames in 5.0 seconds = 4131.331 FPS
20665 frames in 5.0 seconds = 4132.842 FPS
20144 frames in 5.0 seconds = 4028.679 FPS

edit: with 6xFSAA enabled (fglrx 8.22.5):

$ glxgears -printfps
11815 frames in 5.0 seconds = 2362.866 FPS
11813 frames in 5.0 seconds = 2362.441 FPS
11814 frames in 5.0 seconds = 2362.637 FPS
11814 frames in 5.0 seconds = 2362.741 FPS
11812 frames in 5.0 seconds = 2362.398 FPS

Kind of weird, because I figured the bottleneck was my CPU and memory... so I'm surprised enabling FSAA has such a large effect since I thought it was all done within the GPU :confused:

---

### Post by pdc303 on 2006-02-22
glxgears -printfps
58651 frames in 5.0 seconds = 11712.585 FPS
63874 frames in 5.0 seconds = 12762.286 FPS
64786 frames in 5.0 seconds = 12941.944 FPS
61162 frames in 5.0 seconds = 12232.400 FPS
58378 frames in 5.1 seconds = 11521.191 FPS

GeForce 6800 GS under Xgl & Compiz.

---

### Post by BeatBoxRocker on 2006-02-22
This is the first post of a new ubuntu user. Waves for all!

AMD Athlon XP 2600+
512Mb / 333Mhz
ATI Radeon 9000 Pro (ATI Propietary drivers)

10256 frames in 5.0 seconds = 2051.017 FPS
10228 frames in 5.0 seconds = 2045.439 FPS
10227 frames in 5.0 seconds = 2045.301 FPS
10203 frames in 5.0 seconds = 2040.588 FPS
10202 frames in 5.0 seconds = 2040.397 FPS

Saludos!

---

### Post by Xylene on 2006-02-22
25687 frames in 5.0 seconds = 5137.367 FPS
25685 frames in 5.0 seconds = 5136.873 FPS
25692 frames in 5.0 seconds = 5138.274 FPS
25693 frames in 5.0 seconds = 5138.545 FPS
25219 frames in 5.0 seconds = 5043.655 FPS
25509 frames in 5.0 seconds = 5101.708 FPS
25467 frames in 5.0 seconds = 5093.382 FPS

3200+ Athlon XP
1GB Memory
ATi 8.22.5 driver
9800 XT

---

### Post by Hobbes on 2006-02-22
34044 frames in 5.0 seconds = 6794.183 FPS
33989 frames in 5.0 seconds = 6793.143 FPS
33989 frames in 5.0 seconds = 6784.274 FPS
34103 frames in 5.0 seconds = 6805.622 FPS


OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5642 (8.22.5)

XGL w/ Compiz, gotta love it

---

### Post by gborzi on 2006-03-02
$ glxgears -printfps
4840 frames in 5.0 seconds = 967.936 FPS
4846 frames in 5.0 seconds = 969.069 FPS
4825 frames in 5.0 seconds = 964.974 FPS
4850 frames in 5.0 seconds = 969.984 FPS
4834 frames in 5.0 seconds = 966.756 FPS

System: AMD Athlon XP 2800+, 2G RAM, GeForce4 MX 440 AGP 8x, 128MB VRAM
both with the prepackaged 7667 nvidia drivers and the more up to date 8178 drivers.
Regardless of the tweaking in xorg.conf.

On a compaq evo N610c, with a Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz, 768 M RAM, ATI Radeon Mobility 7500 M, 32MB VRAM, using the open source drivers, after some tweaking of xorg.conf I improved glxgears fps from ~470 to
$ glxgears -printfps

sizeof(RADEONDRIRec) == 100, devPrivSize 100
6432 frames in 5.0 seconds = 1286.330 FPS
6360 frames in 5.0 seconds = 1271.925 FPS
6376 frames in 5.0 seconds = 1275.087 FPS
6355 frames in 5.0 seconds = 1270.967 FPS

However, with other programs (e.g. cube) the computer with nvidia has higher fps.

---

### Post by Micro Rotors on 2006-03-04
Got the new card and its working fine now.

AMD 64 Athlon 3500+
PNY Verto GeForce 6800 GS overclocked version

93244 frames in 5.0 seconds = 18648.781 FPS
94048 frames in 5.0 seconds = 18809.436 FPS
93192 frames in 5.0 seconds = 18638.355 FPS
94573 frames in 5.0 seconds = 18914.535 FPS
94557 frames in 5.0 seconds = 18911.215 FPS

---

### Post by R3linquish3r on 2006-03-17
ed@EAGLE:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
4148 frames in 5.0 seconds = 829.600 FPS
5149 frames in 5.0 seconds = 1029.800 FPS
5156 frames in 5.0 seconds = 1031.200 FPS
5150 frames in 5.0 seconds = 1030.000 FPS
5148 frames in 5.0 seconds = 1029.600 FPS
5144 frames in 5.0 seconds = 1028.800 FPS
5159 frames in 5.0 seconds = 1031.800 FPS
5161 frames in 5.0 seconds = 1032.200 FPS
5162 frames in 5.0 seconds = 1032.400 FPS
5161 frames in 5.0 seconds = 1032.200 FPS
5170 frames in 5.0 seconds = 1034.000 FPS
5080 frames in 5.0 seconds = 1016.000 FPS



MSI K8T Neo FISR2
AMD 3200+ Clocked to 2.2GHz
2 G's Kingston DDR400 RAM
ATI Radeon 9800XT (Flashed BIOS from a Pro)
Sound Blaster Audigy 2 ZA
120 G's SATA Drive; 80 G's IDE Drive



Now I'm conviced to go buy a 7600/7800.

---

### Post by BobRyan on 2006-03-23
I've run this test on all of my systems.. here are the results.
both desktop systems running a current gentoo install, xorg 6.8.2, and nvidia-8178. the laptop is running ubuntu dapper, xorg 7.0.0, ubuntu default ati driver. I'm surprised how big the gap between the desktops are, I mean.. the second one was built on the cheap but still... btw. both are using OCZ gold ddr500 memory running 1:1 (250mhz HTT).

Desktop1-
A64 3200+@2.5ghz, 1gb pc4000 OCZ, 128mb 6800 PCI-E@450/850
h36sa@bob ~ $ glxgears -display :0
55427 frames in 5.0 seconds = 11085.400 FPS
61030 frames in 5.0 seconds = 12206.000 FPS
60952 frames in 5.0 seconds = 12190.400 FPS
61044 frames in 5.0 seconds = 12208.800 FPS
61026 frames in 5.0 seconds = 12205.200 FPS
61028 frames in 5.0 seconds = 12205.600 FPS

Desktop2-
Sempron 2800+@2.0ghz, 1gb pc4000 OCZ, 128mb 6600GT AGP@536/974
h36sa@bowser ~ $ glxgears -display :0
29596 frames in 5.0 seconds = 5919.200 FPS
34894 frames in 5.0 seconds = 6978.800 FPS
34880 frames in 5.0 seconds = 6976.000 FPS
34889 frames in 5.0 seconds = 6977.800 FPS
34111 frames in 5.0 seconds = 6822.200 FPS
34844 frames in 5.0 seconds = 6968.800 FPS

Laptop-
P4 2.4ghz, 512mb pc2100, Radeon 7500 Mobile (work in progress)
h36sa@toad ~ $ glxgears -printfps
1093 frames in 5.0 seconds = 218.506 FPS
1084 frames in 5.0 seconds = 216.439 FPS
1087 frames in 5.0 seconds = 217.067 FPS
1090 frames in 5.0 seconds = 217.664 FPS
1088 frames in 5.0 seconds = 217.240 FPS
1083 frames in 5.0 seconds = 216.588 FPS

UPDATE: 
----------------------------------------
I have just gotten DRI properly installed on my laptop. I simply went to [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) and downloaded the most recent radeon package (it was built this morning). I untar'ed it, ran the install script, killed gdm, unloaded the radeon driver, and started gdm... Here are the results-
h36sa@toad ~ $ glxgears -printfps
9375 frames in 5.0 seconds = 1874.926 FPS
9372 frames in 5.0 seconds = 1874.362 FPS
9384 frames in 5.0 seconds = 1876.623 FPS
9382 frames in 5.0 seconds = 1876.204 FPS
9382 frames in 5.0 seconds = 1876.208 FPS
9382 frames in 5.0 seconds = 1876.265 FPS

As you can see, this is a huge improvement. I'm not really sure why the scores are so high (I havn't seen anyone break the 1500fps mark with similar hardware yet) but I'll take it...
  -Bob

---

### Post by proud2bcan8dn on 2006-03-24
40892 frames in 5.0 seconds = 8178.289 FPS
58043 frames in 5.0 seconds = 11608.514 FPS
66480 frames in 5.0 seconds = 13295.909 FPS
61125 frames in 5.0 seconds = 12224.941 FPS
58122 frames in 5.0 seconds = 11624.313 FPS
65514 frames in 5.0 seconds = 13102.656 FPS
68804 frames in 5.0 seconds = 13760.742 FPS
69340 frames in 5.0 seconds = 13867.899 FPS
64976 frames in 5.0 seconds = 12995.143 FPS
69690 frames in 5.0 seconds = 13937.841 FPS
70327 frames in 5.0 seconds = 14065.239 FPS
69861 frames in 5.0 seconds = 13972.035 FPS
67179 frames in 5.0 seconds = 13435.621 FPS
69645 frames in 5.0 seconds = 13928.910 FPS
69114 frames in 5.0 seconds = 13822.772 FPS
68734 frames in 5.0 seconds = 13746.756 FPS
56857 frames in 5.0 seconds = 11371.261 FPS
68219 frames in 5.0 seconds = 13643.768 FPS
69927 frames in 5.0 seconds = 13985.237 FPS
62242 frames in 5.0 seconds = 12448.400 FPS

 Min:   8178.289
Max: 14065.239
Med: 11121.764
 Avg: 12950.812

----------------------------
System Specs:
**************
AMD64 4000+
1GB DDR400
Sapphire Radeon X800XL 256MB PCI-E (Ubuntu Driver)
Ubuntu 5.10

---

### Post by pestypest on 2006-03-24
[QUOTE=electrosoccertux]Oh yeah well I beat all you all:

101050 frames in 5.0 seconds = 21177.800 FPS
99157 frames in 5.0 seconds = 19831.400 FPS
103554 frames in 5.0 seconds = 20710.800 FPS
105889 frames in 5.0 seconds = 21177.800 FPS

Barton 2500+ with water cooled 6800 Ultra clocked at 653/1384.[/QUOTE]

HAHAH cheater! ;) :P this is my OVERHEATED lol 
78208 frames in 5.0 seconds = 15641.478 FPS
91653 frames in 5.0 seconds = 18330.562 FPS
91302 frames in 5.0 seconds = 18260.324 FPS
89812 frames in 5.0 seconds = 17962.281 FPS
85293 frames in 5.0 seconds = 17054.244 FPS
check my sig

---

### Post by akeon on 2006-03-25
3713 frames in 5.0 seconds = 742.600 FPS
4263 frames in 5.0 seconds = 852.600 FPS
4270 frames in 5.0 seconds = 854.000 FPS
4277 frames in 5.0 seconds = 855.400 FPS
4269 frames in 5.0 seconds = 853.800 FPS
4268 frames in 5.0 seconds = 853.600 FPS
4277 frames in 5.0 seconds = 855.400 FPS
4268 frames in 5.0 seconds = 853.600 FPS
4270 frames in 5.0 seconds = 854.000 FPS
4277 frames in 5.0 seconds = 855.400 FPS

Pentium III 868MHz
385MB (DDR133)
nVIDIA GeForce FX5200 128MB

It's enough for me.

---

### Post by peRosine on 2006-03-31
AMD Athlon 3600+
Geforce 6800 GT.

```
pero@perosine:~$ glxgears -printfps
30081 frames in 5.0 seconds = 6007.178 FPS
71247 frames in 5.0 seconds = 14223.619 FPS
71289 frames in 5.0 seconds = 14249.618 FPS
71163 frames in 5.0 seconds = 14232.042 FPS
71164 frames in 5.0 seconds = 14231.872 FPS
71289 frames in 5.0 seconds = 14239.351 FPS
71291 frames in 5.0 seconds = 14245.214 FPS
71289 frames in 5.0 seconds = 14248.006 FPS
```

Non tweaked. Tweaking it next week when I get my new coolers.

---

### Post by Perfect Storm on 2006-03-31
[QUOTE=BobRyan]I've run this test on all of my systems.. here are the results.
both desktop systems running a current gentoo install, xorg 6.8.2, and nvidia-8178. the laptop is running ubuntu dapper, xorg 7.0.0, ubuntu default ati driver. I'm surprised how big the gap between the desktops are, I mean.. the second one was built on the cheap but still... btw. both are using OCZ gold ddr500 memory running 1:1 (250mhz HTT).

<snip>...
As you can see, this is a huge improvement. I'm not really sure why the scores are so high (I havn't seen anyone break the 1500fps mark with similar hardware yet) but I'll take it...
  -Bob[/QUOTE]

Don't worry glxgears isn't a benchmark. There are so many factors into the consideration, like screen resolution, depths, where you set the gears etc. etc.

If you want to benchmark try this: [http://ubuntuforums.org/showthread.php?t=145492](http://ubuntuforums.org/showthread.php?t=145492)

---

### Post by steveyeager on 2006-03-31
When I run glxgears, it does not show me framerates.  How can I get it to show framerates?

---

### Post by peRosine on 2006-04-01
```
glxgears -printfps
```

---

### Post by zisper on 2006-05-04
cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

Getting 2500 FPS

p4 1.7
1Gig Memory
nVidia GeForce3 Ti 500

Running Dapper - 2.6.15-21-686

---

### Post by enkrypt3d on 2006-05-04
[QUOTE=Artificial Intelligence]Don't worry glxgears isn't a benchmark. There are so many factors into the consideration, like screen resolution, depths, where you set the gears etc. etc.

If you want to benchmark try this: [http://ubuntuforums.org/showthread.php?t=145492](http://ubuntuforums.org/showthread.php?t=145492)[/QUOTE]

The one I like to use for fun is tuxracer! I get about 350FPS - 600 FPS with all the details and fog w/ 4 x FSAA & stencil buffer enabled.....so rad!! Now I just wish I could get SLi acceleration running..... In GLXgears I get 16,500 FPS or so....with its default size w/ a 1280x1024 screen @ 24 bit...... thoughts?

---

### Post by ciprianc on 2006-05-05
Celeron M 1.50GHz
1256 MB ram
Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller
Screen Resolution : 1280x800

5059 frames in 5.0 seconds = 1011.775 FPS
5057 frames in 5.0 seconds = 1011.211 FPS
5060 frames in 5.0 seconds = 1011.986 FPS
5059 frames in 5.0 seconds = 1011.677 FPS

---

### Post by zisper on 2006-05-05
I just thought I'd post this - after some issues with the 8756 driver and DVI connection on my card, I downgraded to the 7676 nvidia driver...  And picked my FPS up to 3000.  :D

---

### Post by lonegeek on 2006-06-11
Radeon 9500 non pro 64mb, amd xp 2200+, 1 gb ram...

Using fglrx drivers and dual monitors

zach@ubuntu:~$ glxgears -printfps
10524 frames in 5.0 seconds = 2104.758 FPS
10410 frames in 5.0 seconds = 2081.921 FPS
8831 frames in 5.0 seconds = 1766.034 FPS
10637 frames in 5.0 seconds = 2127.247 FPS
10643 frames in 5.0 seconds = 2128.446 FPS
10652 frames in 5.0 seconds = 2130.367 FPS
10350 frames in 5.0 seconds = 2069.837 FPS
9635 frames in 5.1 seconds = 1903.245 FPS
9585 frames in 5.0 seconds = 1916.874 FPS
10585 frames in 5.0 seconds = 2116.882 FPS
8845 frames in 5.0 seconds = 1768.846 FPS
7349 frames in 5.0 seconds = 1469.731 FPS
8063 frames in 5.0 seconds = 1612.479 FPS

---

### Post by fargoth on 2006-06-14
around 9300 with P4 3Ghz 2GB DDR4300 GeForce7600GT
running with compiz - i can change the opacity/brightness/saturation and drag the window around with the wobbly plugin - it doesn't affect the FPS as far as i can tell!

very cool.

---

### Post by Oblong_Cheese on 2006-06-14
AMD Athlon64 3400+; 1024Mb DDR; GeForce 6800GT

> 
64345 frames in 5.0 seconds = 12868.826 FPS
80593 frames in 5.0 seconds = 16118.500 FPS
99656 frames in 5.0 seconds = 19931.105 FPS
100196 frames in 5.0 seconds = 20039.082 FPS
99924 frames in 5.0 seconds = 19984.797 FPS
100000 frames in 5.0 seconds = 19999.885 FPS
89981 frames in 5.0 seconds = 17995.941 FPS


Hmmm yes... I am a gamer. :-P

By the way, this is running an amd64-k8 kernel and appropriate nvidia-glx modules. ;-)

---

### Post by popkid on 2006-06-15
Anyone fancy a laugh.....

937 frames in 5.0 seconds = 187.400 FPS
899 frames in 5.0 seconds = 179.655 FPS
938 frames in 5.0 seconds = 187.481 FPS
935 frames in 5.0 seconds = 186.939 FPS
938 frames in 5.0 seconds = 187.453 FPS

Dell Inspiron 7500, PIII 700MHz, ATI Mobility Mach64

and thats with dri!

you may have guessed I'm not a gamer :) 

pK

---

### Post by syxbit on 2006-06-15
i installed my ATI drivers, and type
glxgears
in the the terminal.
the thing loads up, and i can see it working, but nothing is printed on the terminal
any ideas ?

---

### Post by fargoth on 2006-06-16
try glxgears -info

---

### Post by shoffman11 on 2006-06-16
$ glxgears -printfps
73029 frames in 5.0 seconds = 14605.738 FPS
73038 frames in 5.0 seconds = 14607.478 FPS
73064 frames in 5.0 seconds = 14612.773 FPS
72099 frames in 5.0 seconds = 14419.726 FPS
72124 frames in 5.0 seconds = 14424.613 FPS

Athlon64x2 3800+ (2.16Ghz)
nvidia 7800GT (pci-e)
2gb corsair xms ram ddr400

---

### Post by fargoth on 2006-06-18
[QUOTE=shoffman11]$ glxgears -printfps
73029 frames in 5.0 seconds = 14605.738 FPS
73038 frames in 5.0 seconds = 14607.478 FPS
73064 frames in 5.0 seconds = 14612.773 FPS
72099 frames in 5.0 seconds = 14419.726 FPS
72124 frames in 5.0 seconds = 14424.613 FPS

Athlon64x2 3800+ (2.16Ghz)
nvidia 7800GT (pci-e)
2gb corsair xms ram ddr400[/QUOTE]

this is wierd, 3400+ and 6800GT got 19000 while you only get 14500??? seems like the drivers for the 7800GT aren't that optimised yet... are you running the amd64-k8 kernel and the latest nvidia-glx drivers?

---

### Post by dicecca112 on 2006-06-18
PIII 1GHZ
512MB of SDRam
Integrated graphics

> 2380 frames in 5.0 seconds = 475.984 FPS
6895 frames in 5.0 seconds = 1378.853 FPS
6814 frames in 5.0 seconds = 1362.684 FPS
5718 frames in 5.0 seconds = 1143.507 FPS
6129 frames in 5.0 seconds = 1225.734 FPS
6707 frames in 5.0 seconds = 1341.385 FPS
6367 frames in 5.0 seconds = 1273.264 FPS
7201 frames in 5.0 seconds = 1440.151 FPS
6402 frames in 5.0 seconds = 1280.322 FPS
6587 frames in 5.0 seconds = 1317.372 FPS
6200 frames in 5.0 seconds = 1233.458 FPS
2916 frames in 5.2 seconds = 564.533 FPS
5054 frames in 5.0 seconds = 1010.646 FPS
5668 frames in 5.0 seconds = 1133.474 FPS
6500 frames in 5.0 seconds = 1299.848 FPS
6373 frames in 5.0 seconds = 1272.528 FPS
6552 frames in 5.0 seconds = 1310.344 FPS
3905 frames in 5.0 seconds = 780.946 FPS


---

### Post by shoffman11 on 2006-06-21
[QUOTE=fargoth]this is wierd, 3400+ and 6800GT got 19000 while you only get 14500??? seems like the drivers for the 7800GT aren't that optimised yet... are you running the amd64-k8 kernel and the latest nvidia-glx drivers?[/QUOTE]

I'm running a customized 2.6.16-ck12 kernel and the nvidia drivers from nvidia (1.0-8762) > $ uname -a
Linux arthurdent 2.6.16-ck12 #1 SMP PREEMPT Sat Jun 17 19:26:55 EDT 2006 i686 GNU/Linux


My first post was with the default clock speeds.  After using the nvidia settings dialog auto detect timings, I get:> $ glxgears -printfps
78514 frames in 5.0 seconds = 15702.617 FPS
78548 frames in 5.0 seconds = 15709.462 FPS
78663 frames in 5.0 seconds = 15732.483 FPS
78580 frames in 5.0 seconds = 15715.896 FPS
78344 frames in 5.0 seconds = 15668.634 FPS
78531 frames in 5.0 seconds = 15706.089 FPS

That's with 490Mhz GPU and 1156Mhz memory.  I don't understand why the 6800GT is faster than the 7800GT.  Maybe he overclocked his more or the driver isn't optimized for 7800GT?

---

### Post by xelink on 2006-06-25
> 108741 frames in 5.0 seconds = 21748.047 FPS
107269 frames in 5.0 seconds = 21453.768 FPS
108078 frames in 5.0 seconds = 21615.506 FPS
108132 frames in 5.0 seconds = 21626.227 FPS
108665 frames in 5.0 seconds = 21732.861 FPS
108726 frames in 5.0 seconds = 21745.195 FPS
108756 frames in 5.0 seconds = 21751.033 FPS
108721 frames in 5.0 seconds = 21744.176 FPS
108234 frames in 5.0 seconds = 21646.721 FPS
108769 frames in 5.0 seconds = 21753.695 FPS
108730 frames in 5.0 seconds = 21745.996 FPS
88605 frames in 5.0 seconds = 17720.838 FPS
69878 frames in 5.0 seconds = 13975.453 FPS
69867 frames in 5.0 seconds = 13973.262 FPS
69861 frames in 5.0 seconds = 13972.116 FPS
69877 frames in 5.0 seconds = 13975.272 FPS
69882 frames in 5.0 seconds = 13976.390 FPS

everything done full 24/32 bit color
13.9k was with it off screen

opteron 165@2.61GHz 1.264V(1.30/1.35Vnormal)
RAM 2GB DDR500@261mhz 3-4-4-8 (or is it 7 don't remember too tired, doesn't amtter really though) 2.7V
7800GT core 470, ram 1.1GHz(stock factory overclock)

---

### Post by liquidtenmillion on 2006-06-26
[QUOTE=shoffman11]I'm running a customized 2.6.16-ck12 kernel and the nvidia drivers from nvidia (1.0-8762) 

My first post was with the default clock speeds.  After using the nvidia settings dialog auto detect timings, I get:That's with 490Mhz GPU and 1156Mhz memory.  I don't understand why the 6800GT is faster than the 7800GT.  Maybe he overclocked his more or the driver isn't optimized for 7800GT?[/QUOTE]

glxgears is not a benchmark!  It's true.  One system can score FAR higher than another, but yet can be much slower in reality.  The only true benchmark would be playing a game on full settings and watching FPS from that.  Glxgears is meant ONLY to test if you have 3d accelleration working at all, not to test how fast a card is.


That should hopefully be good news for you.

---

### Post by RESmonkey on 2006-06-27
Avg (by looking at the numbers, no real math): 6600-6650+(first try) 7000-7100+ second try

Pentium 4 1.6Ghz (NOT HT)
512MB RAm, 1@PC2100, 1@PC2700
ATi Radeon 9600 RV350 256MB (DOWNclocked)

^I've downclocked the card to 200mhz (default driver), but it's safely capable of 400Mhz, and experimental 500Mhz...0.O

Anyone else with a similar setup?

EDIT= OMG second try....7100's....and over!!!!!

---

### Post by hard_i on 2006-06-27
20199 frames in 5.0 seconds = 4039.642 FPS
20196 frames in 5.0 seconds = 4039.051 FPS
20181 frames in 5.0 seconds = 4036.042 FPS
20189 frames in 5.0 seconds = 4037.795 FPS
20203 frames in 5.0 seconds = 4040.564 FPS

Celeron 2.4GHz ( northwood - 128kb L2 powwa )
1GB PC3200 2.5-3-3-7
Radeon 9600pro 128MB

---

### Post by Tylo on 2006-06-27
3642.337 FPS

ATi RADEON 9600 AIW
2.8 ghz, I think? Pentium 4.
512 RAM

---

### Post by hypnoticstate on 2006-07-01
69182 frames in 5.0 seconds = 13819.917 FPS
68850 frames in 5.0 seconds = 13769.975 FPS
67092 frames in 5.0 seconds = 13400.014 FPS
67620 frames in 5.0 seconds = 13511.734 FPS
68055 frames in 5.0 seconds = 13608.336 FPS
64261 frames in 5.0 seconds = 12849.012 FPS
64261 frames in 5.0 seconds = 12847.193 FPS
64638 frames in 5.0 seconds = 12905.519 FPS
64512 frames in 5.0 seconds = 12891.259 FPS
68726 frames in 5.0 seconds = 13743.381 FPS
70959 frames in 5.0 seconds = 14189.659 FPS
70685 frames in 5.0 seconds = 14129.252 FPS
69141 frames in 5.0 seconds = 13814.532 FPS
67929 frames in 5.0 seconds = 13581.106 FPS
68253 frames in 5.0 seconds = 13650.582 FPS
64633 frames in 5.0 seconds = 12909.310 FPS
64936 frames in 5.0 seconds = 12977.732 FPS
69346 frames in 5.0 seconds = 13856.101 FPS
69726 frames in 5.0 seconds = 13925.982 FPS
64707 frames in 5.0 seconds = 12934.308 FPS
69314 frames in 5.0 seconds = 13856.793 FPS
70384 frames in 5.0 seconds = 14056.007 FPS
70467 frames in 5.0 seconds = 14075.684 FPS
67673 frames in 5.0 seconds = 13516.018 FPS
67691 frames in 5.0 seconds = 13528.720 FPS
64387 frames in 5.0 seconds = 12861.070 FPS
65265 frames in 5.0 seconds = 13047.669 FPS

X2-4400, 2gigs Ram, 7800gt

---

### Post by johnwlittle on 2006-07-02
[IMG]http://www.blogsofwar.com/gallery/wp-content/uploads/2006/07/pc.jpg[/IMG]

63689 frames in 5.0 seconds = 12737.690 FPS
84148 frames in 5.0 seconds = 16829.510 FPS
86075 frames in 5.0 seconds = 17214.957 FPS
83976 frames in 5.0 seconds = 16795.182 FPS
87929 frames in 5.0 seconds = 17585.611 FPS
89133 frames in 5.0 seconds = 17826.453 FPS

CPU
AMD Athlon 64 X2 3800+ - 1GHz FSB 2 x 512KB L2 Cache Socket 939 Dual Core Processor 

Motherboard
nForce4-A939 - nVRAID, K8HT2000, Gigabit Ethernet LAN, nVidia Firewall, PCI Express, Dual-Channel DDR 400, SATA, ATA133, onboard 6-channel audio and USB 2.0.

Video
BFG nVidia GeForce 7600gt OC

Ram
1GB Dual-Channel DDR 400

Storage
Dual Seagate Barracuda 160GB SATA drives
120GB external firewire drive
Memorex Dual Layer DVD±RW Writer

Case
LL Warrior - (Lian Li PC-61 modded w/ 6 fans & 500w power supply)

OS
Ubuntu 6.06 (of course) w/ K7-SMP Kernel

---

### Post by vem0m on 2006-07-06
3267.138
ATi All-In-Wonder X800 XL 256 DDR
Intel Celeron 2.7 GHz
1.3 GB DDR RAM

---

### Post by walkerx on 2006-07-07
Well this is my results

60823 frames in 5.0 seconds = 12164.451 FPS
64639 frames in 5.0 seconds = 12927.763 FPS
64805 frames in 5.0 seconds = 12960.910 FPS
64695 frames in 5.0 seconds = 12938.958 FPS
64623 frames in 5.0 seconds = 12924.595 FPS
64812 frames in 5.0 seconds = 12962.397 FPS
64252 frames in 5.0 seconds = 12850.277 FPS
62569 frames in 5.0 seconds = 12513.625 FPS
64637 frames in 5.0 seconds = 12927.299 FPS
62683 frames in 5.0 seconds = 12536.449 FPS
7372 frames in 5.0 seconds = 1474.241 FPS
6815 frames in 5.0 seconds = 1362.877 FPS
6801 frames in 5.0 seconds = 1360.177 FPS
62013 frames in 5.0 seconds = 12402.596 FPS
64853 frames in 5.0 seconds = 12970.474 FPS
64184 frames in 5.0 seconds = 12836.636 FPS
62570 frames in 5.0 seconds = 12513.909 FPS
6803 frames in 5.0 seconds = 1360.544 FPS
6813 frames in 5.0 seconds = 1362.576 FPS
6796 frames in 5.0 seconds = 1359.033 FPS
11375 frames in 5.0 seconds = 2274.720 FPS

The high frame rates are when it runs the default tiny window, and from looking at everyone else's post this is what I think they have posted on, if I'm wrong please can someone tell me how to get them framerates when running maximised.

The lower framerates are when I run glxgears in maximised mode

---

### Post by Roger Mudd on 2006-07-07
Minimized

```
41078 frames in 5.0 seconds = 8215.512 FPS
65282 frames in 5.0 seconds = 13056.271 FPS
64498 frames in 5.0 seconds = 12899.541 FPS
64981 frames in 5.0 seconds = 12996.141 FPS
63593 frames in 5.0 seconds = 12718.510 FPS
58114 frames in 5.0 seconds = 11622.771 FPS
64802 frames in 5.0 seconds = 12960.211 FPS
44388 frames in 5.0 seconds = 8863.949 FPS
```

Maximized

```
41078 frames in 5.0 seconds = 8215.512 FPS
65282 frames in 5.0 seconds = 13056.271 FPS
64498 frames in 5.0 seconds = 12899.541 FPS
64981 frames in 5.0 seconds = 12996.141 FPS
63593 frames in 5.0 seconds = 12718.510 FPS
58114 frames in 5.0 seconds = 11622.771 FPS
64802 frames in 5.0 seconds = 12960.211 FPS
44388 frames in 5.0 seconds = 8863.949 FPS

```

Motherboard:  ABIT IC7-G
Video Card:  Sapphire ATI Radeon 9800 Pro
Drivers:  Installed via [this]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#video-acceleration-introduction") method
RAM: 2GB
Monitor:  Dell 2005FPW (1680x1050 resolution)

---

### Post by afterxleep on 2006-07-12
> **verbalshadow said:**
> verbalshadow@darkspiral:~$ glxgears
841 frames in 5.0 seconds = 168.200 FPS
914 frames in 5.0 seconds = 182.800 FPS
908 frames in 5.0 seconds = 181.600 FPS
988 frames in 5.0 seconds = 197.600 FPS
912 frames in 5.0 seconds = 182.400 FPS
908 frames in 5.0 seconds = 181.600 FPS
816 frames in 5.0 seconds = 163.200 FPS


amd XP-m 2800+
768mb ddr ram
ATI Radeon Mobility U1

Drivers that came with hoary.


1255 frames in 5.0 seconds = 250.791 FPS
1229 frames in 5.0 seconds = 245.785 FPS
1227 frames in 5.0 seconds = 245.188 FPS
1232 frames in 5.0 seconds = 246.188 FPS
1229 frames in 5.0 seconds = 245.584 FPS
1230 frames in 5.0 seconds = 245.979 FPS

amd XP-m 2200+
Radeon Mobility U1

Just set Dapper to use the radeon driver instead ATI
Window size is default

Does anyone has better FPS with this card?

---

### Post by joshchernoff on 2006-07-18
inetl p4 3gig 64bit 800fsb 
1gig DDR2-667 
512 sapphire ati radeon x1600
:(  ecs motherboard (I know, I know)


out in front
20649 frames in 5.0 seconds = 4129.739 FPS
20124 frames in 5.0 seconds = 4024.765 FPS
19692 frames in 5.0 seconds = 3938.300 FPS
20190 frames in 5.0 seconds = 4037.839 FPS
20130 frames in 5.0 seconds = 4025.833 FPS
20175 frames in 5.0 seconds = 4034.835 FPS
20191 frames in 5.0 seconds = 4038.004 FPS
20079 frames in 5.0 seconds = 4015.605 FPS

behind window
61788 frames in 5.0 seconds = 12357.431 FPS
61853 frames in 5.0 seconds = 12370.546 FPS
61880 frames in 5.0 seconds = 12375.998 FPS
61823 frames in 5.0 seconds = 12364.586 FPS
61817 frames in 5.0 seconds = 12363.265 FPS
61661 frames in 5.0 seconds = 12332.066 FPS
61606 frames in 5.0 seconds = 12321.031 FPS
61738 frames in 5.0 seconds = 12347.456 FPS
61949 frames in 5.0 seconds = 12389.733 FPS

---

### Post by qqwasder on 2006-07-25
Scores for asus A8N-SLI Deluxe, AMD 3500+, nvidia 7800GT, generic memory:

60262 frames in 5.0 seconds = 10052.400 FPS
61217 frames in 5.0 seconds = 12243.400 FPS
61364 frames in 5.0 seconds = 12272.800 FPS
62069 frames in 5.0 seconds = 12413.800 FPS
62471 frames in 5.0 seconds = 12494.200 FPS
62308 frames in 5.0 seconds = 12461.600 FPS
61809 frames in 5.0 seconds = 12361.800 FPS
62222 frames in 5.0 seconds = 12444.400 FPS
61887 frames in 5.0 seconds = 12377.400 FPS
56440 frames in 5.0 seconds = 11288.000 FPS

Note: Just a data point for SuSE 10.0

---

### Post by pickarooney on 2006-07-27
glxgears doesn't give me any output to the console window, just plays the little box of gears (pretty slowly). Is there some argument needed for it to print out the fps scores?

---

### Post by 5-HT on 2006-07-28
> **pickarooney said:**
> glxgears doesn't give me any output to the console window, just plays the little box of gears (pretty slowly). Is there some argument needed for it to print out the fps scores?
```
 glxgears -printfps
```

---

### Post by fireedo on 2006-07-28
edo@ubuntu:~$ glxgears -printfps
20592 frames in 5.0 seconds = 4118.298 FPS
20670 frames in 5.0 seconds = 4133.821 FPS
20670 frames in 5.0 seconds = 4133.954 FPS

edo@ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
2637 frames in 5.0 seconds = 527.400 FPS
3116 frames in 5.0 seconds = 623.200 FPS
3083 frames in 5.0 seconds = 616.600 FPS


AMD sempron64 2500
DDR 512mb Kingston value RAM
Creative ATI Radeon 9600 pro 128Mb
Ubuntu Dapper

---

### Post by XneoX on 2006-07-31
20023 frames in 5.0 seconds = 4004.520 FPS
20295 frames in 5.0 seconds = 4058.997 FPS
20331 frames in 5.0 seconds = 4066.010 FPS
20333 frames in 5.0 seconds = 4066.573 FPS
20312 frames in 5.0 seconds = 4062.292 FPS
20295 frames in 5.0 seconds = 4058.997 FPS

Fujitsu Siemens Amilo 1425 Laptop
128Mb Ati Radeon 9700
512 RAM
1.8G Intel Centrino

:-(

---

### Post by rippon on 2006-08-01
772 frames in 5.0 seconds = 154.352 FPS

I dont know if these ATI drivers are working for me or not. I also found that if I cover up the gears with the terminal, I get around 14000fps, but I guess that is cheating.

---

### Post by devnulljp on 2006-08-11
> **steveyeager said:**
> When I run glxgears, it does not show me framerates.  How can I get it to show framerates?

```
glxgears -iacknowledgetthatthistoolisnotabenchmark
```

---

### Post by Hitman_Forhire on 2006-08-13
3.2 Ghz P4 HT - [ Laptop ]
1GB DDR 400
Dapper, XGL+Compiz

27985 frames in 5.0 seconds = 5578.570 FPS

That's all I got.

---

### Post by GhostDawg on 2006-08-13
I recently installed Dapper 6.0.6.1 using and Athlon XP 1700 1.4ghz system and running glxgears, it runs very slow.

I did install the linux-images-k7 and didn't make a big difference. Running other linux distros glxgears flies much faster than with Ubuntu. It was slow when I had Breezy installed also.

Any suggestions?

Thnx.

---

### Post by zxee on 2006-08-13
What the hey...Homebuilt sempron 1.8Mhz, 512MB Ram, G-force 5500 128MB video with nvidia-glx apt installed. In Dapper 6.0.6.1 (I don't think the fps is any different in my edgy install-but I'd have to check to be sure)

glxgears -printfps
6669 frames in 5.0 seconds = 1333.634 FPS
6681 frames in 5.0 seconds = 1336.079 FPS
6678 frames in 5.0 seconds = 1335.474 FPS
6678 frames in 5.0 seconds = 1335.415 FPS

with glxgears gui covered by terminal
39520 frames in 5.0 seconds = 7903.889 FPS
39522 frames in 5.0 seconds = 7904.272 FPS
39509 frames in 5.0 seconds = 7901.618 FPS
39467 frames in 5.0 seconds = 7893.257 FPS
39575 frames in 5.0 seconds = 7914.878 FPS
39656 frames in 5.0 seconds = 7901.586 FPS
39503 frames in 5.0 seconds = 7900.537 FPS

---

### Post by jworr on 2006-08-13
64bit ubuntu 6.06.1
nvidia 6800gt
amd 64 3000+

glxgears -printfps
64403 frames in 5.0 seconds = 12880.440 FPS
64344 frames in 5.0 seconds = 12868.617 FPS
64199 frames in 5.0 seconds = 12839.644 FPS
64784 frames in 5.0 seconds = 12956.654 FPS
64796 frames in 5.0 seconds = 12959.155 FPS
64731 frames in 5.0 seconds = 12946.074 FPS
64795 frames in 5.0 seconds = 12958.842 FPS

---

### Post by JamesTheBard on 2006-08-13
Okay, here's what I've got:

Regular:
--------------------------------------------
62730 frames in 5.0 seconds = 12527.883 FPS
62354 frames in 5.0 seconds = 12457.127 FPS
63754 frames in 5.0 seconds = 12747.658 FPS
64644 frames in 5.0 seconds = 12928.798 FPS

Full-Screen (1920x1200)
--------------------------------------------
8998 frames in 5.1 seconds = 1758.310 FPS
8892 frames in 5.0 seconds = 1766.764 FPS
8745 frames in 5.0 seconds = 1739.795 FPS
8698 frames in 5.1 seconds = 1718.644 FPS

DISTRO: "Dapper Drake" i386 (SMP i686 kernel)
XORG: 7.0 w/ GLX and Compiz
CPU: Athlon 64 X2 4200+
RAM: 2 GB
GRAPHICS: XFX nVidia GeForce 6800 GT

---

### Post by jpowell on 2006-08-16
AMD Athlon 64 3000
1Gb Ram
Geforce 7900GT AGP
Dapper

jpowell@icarus:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
70078 frames in 5.0 seconds = 14015.413 FPS
70462 frames in 5.0 seconds = 14092.293 FPS
70387 frames in 5.0 seconds = 14077.257 FPS

---

### Post by KlausU on 2006-08-17
78356 frames in 5.0 seconds = 15671.172 FPS

Core 2 Duo 6600 @ 2.4 GHz
Nvidia GeForce 7900 GT 256 MB
2*1 GB Corsair VS @ 667

---

### Post by _fr33man_ on 2006-08-19
10154 frames in 5.0 seconds = 2030.767 FPS
10393 frames in 5.0 seconds = 2078.260 FPS
10444 frames in 5.0 seconds = 2088.782 FPS
10444 frames in 5.0 seconds = 2088.781 FPS
10447 frames in 5.0 seconds = 2089.365 FPS

AMD Duron 1.1Ghz
256MB SDRAM PC133
GeForce 4 MX440-SE 64MB 128bit

---

### Post by argie on 2006-08-19
Damn video drivers.

615 frames in 5.3 seconds = 115.725 FPS
1140 frames in 5.1 seconds = 221.364 FPS
1368 frames in 5.1 seconds = 268.421 FPS

---

### Post by jrjr on 2006-08-19
wow not many people running ATI so it seems...

Does this look right to you guys?? Seems like low numbers but the machine works ok....

Gears running in open
14605 frames in 5.0 seconds = 2920.922 FPS
14600 frames in 5.0 seconds = 2919.958 FPS
14551 frames in 5.0 seconds = 2910.135 FPS
14384 frames in 5.0 seconds = 2876.800 FPS

gears covered up
26650 frames in 5.0 seconds = 5329.886 FPS
26837 frames in 5.0 seconds = 5367.290 FPS
26887 frames in 5.0 seconds = 5377.204 FPS
26806 frames in 5.0 seconds = 5361.127 FPS


Intel 2.8
512 ram
ATI X1600
FGLRX driver
Big Desktop mode (2 screens)

Edit:
Sorry just realized this is Hoary forum
I'm using Dapper if it makes a difference

---

### Post by ubu_dynamite on 2006-08-24
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 TX Generic
OpenGL version string: 2.0.5814 8.25.18
pentium 4, 2.6Ghz, 1gb Ram

"Dapper Drake"
"linux-686"

xserver-xorg-driver-ati
glxgears-printfps
6044 frames in 5.0 seconds = 1208.780 FPS
5760 frames in 5.0 seconds = 1151.965 FPS
5767 frames in 5.0 seconds = 1153.268 FPS
5913 frames in 5.0 seconds = 1182.463 FPS
6041 frames in 5.0 seconds = 1207.877 FPS
5842 frames in 5.0 seconds = 1168.258 FPS
############################################

xorg-driver-fglrx "ubuntu 8.25.18"
glxgears -printfps
15806 frames in 5.0 seconds = 3161.006 FPS
15772 frames in 5.0 seconds = 3154.384 FPS
15552 frames in 5.0 seconds = 3110.239 FPS
15774 frames in 5.0 seconds = 3154.632 FPS
15776 frames in 5.0 seconds = 3155.145 FPS
15774 frames in 5.0 seconds = 3154.720 FPS
15775 frames in 5.0 seconds = 3154.903 FPS

fgl_glxgears
Using GLX_SGIX_pbuffer
2256 frames in 5.0 seconds = 451.200 FPS
2610 frames in 5.0 seconds = 522.000 FPS
2631 frames in 5.0 seconds = 526.200 FPS
2610 frames in 5.0 seconds = 522.000 FPS
2619 frames in 5.0 seconds = 523.800 FPS
2617 frames in 5.0 seconds = 523.400 FPS
2606 frames in 5.0 seconds = 521.200 FPS

---

### Post by Josh_b on 2006-08-25
84798 frames in 5.0 seconds = 16959.504 FPS
82696 frames in 5.0 seconds = 16539.174 FPS
85002 frames in 5.0 seconds = 17000.299 FPS
83336 frames in 5.0 seconds = 16667.016 FPS
72152 frames in 5.0 seconds = 14356.036 FPS
67468 frames in 5.0 seconds = 13493.587 FPS
81009 frames in 5.0 seconds = 16201.680 FPS
83177 frames in 5.0 seconds = 16635.242 FPS
80071 frames in 5.0 seconds = 16014.136 FPS

hehe. Do I win?

I'm running:
AMD 4200+ 64 Bit X2 (only running 32-bit Ubuntu though)
Dual LeadTek 7900GT's
ASUS brand AGEIA PhysX (no drivers :( )
1Gb ram (needs an upgrade)

---

### Post by Malac on 2006-08-25
```
$ glxgears
4459 frames in 5.0 seconds = 891.755 FPS
4411 frames in 5.0 seconds = 882.162 FPS
4411 frames in 5.0 seconds = 882.182 FPS
4412 frames in 5.0 seconds = 882.199 FPS
4411 frames in 5.0 seconds = 882.192 FPS
4412 frames in 5.0 seconds = 882.222 FPS
``` 
ATI 9200SE 128MB
P4 2.8GHz
768MB RAM
ATI 8.28.8 driver compiled to Ubuntu/dapper

---

### Post by catanzag on 2006-08-25
2581 frames in 5.0 seconds = 516.127 FPS
2642 frames in 5.0 seconds = 528.100 FPS
2812 frames in 5.0 seconds = 562.345 FPS
2507 frames in 5.0 seconds = 501.011 FPS
2705 frames in 5.0 seconds = 540.939 FPS
2271 frames in 5.0 seconds = 454.018 FPS

Pentium 4 M 1.7 GHz
GeForce4 420 Go
768MB RAM

---

### Post by edemark on 2006-08-25
5524 frames in 5.0 seconds = 1104.667 FPS
5529 frames in 5.0 seconds = 1105.671 FPS
5530 frames in 5.0 seconds = 1105.956 FPS
5523 frames in 5.0 seconds = 1104.413 FPS
5488 frames in 5.0 seconds = 1097.544 FPS
5411 frames in 5.0 seconds = 1082.136 FPS
5518 frames in 5.0 seconds = 1103.494 FPS

pIV 3.06
ati igp 345 128 mb ram shared
640 MB ram (768 would be but 128 goes to the graphics)

---

### Post by viciouslime on 2006-08-26
> **Josh_b said:**
> 84798 frames in 5.0 seconds = 16959.504 FPS
82696 frames in 5.0 seconds = 16539.174 FPS
85002 frames in 5.0 seconds = 17000.299 FPS
83336 frames in 5.0 seconds = 16667.016 FPS
72152 frames in 5.0 seconds = 14356.036 FPS
67468 frames in 5.0 seconds = 13493.587 FPS
81009 frames in 5.0 seconds = 16201.680 FPS
83177 frames in 5.0 seconds = 16635.242 FPS
80071 frames in 5.0 seconds = 16014.136 FPS

hehe. Do I win?

I'm running:
AMD 4200+ 64 Bit X2 (only running 32-bit Ubuntu though)
Dual LeadTek 7900GT's
ASUS brand AGEIA PhysX (no drivers :( )
1Gb ram (needs an upgrade)


Only just, I get 12500 FPS, from a single 7800GT so I would expect a LOT more from two 7900GTs! Especially given how much that must have cost you!

---

### Post by schoene on 2006-08-27
My fps always stay 125, even if I set glxgears in full screen. Also when I play tuxracer, the fps is exactly 125. Does the newest ATI driver limit the frame-rate? Or can I disable that?

---

### Post by Malac on 2006-08-27
Could people go back through and put which driver and version they are using as this may help other people get an idea of what is possible.

---

### Post by Josh_b on 2006-08-28
> **viciouslime said:**
> Only just, I get 12500 FPS, from a single 7800GT so I would expect a LOT more from two 7900GTs! Especially given how much that must have cost you!

I paid AU$450 for each (Don't how much they're worth in America, and it's not just the exchange rate either). Don't forget also, glxgears doesn't require the same specs as games (ie, no intensive CPU calculations, etc), which my PC would probably further out do your machine (what are your specs?), especially if there was a linux version of the PhysX drivers.:cry: 

[QUOTE=Malac]Could people go back through and put which driver and version they are using as this may help other people get an idea of what is possible.[/QUOTE]

The driver I'm using is version 1.0.8762+2.6.15.11-3 of nvidia-glx (I think that's the info you were looking for)

---

### Post by maka on 2006-08-29
> **Josh_b said:**
> I paid AU$450 for each (Don't how much they're worth in America, and it's not just the exchange rate either). Don't forget also, glxgears doesn't require the same specs as games (ie, no intensive CPU calculations, etc), which my PC would probably further out do your machine (what are your specs?), especially if there was a linux version of the PhysX drivers.:cry: 



The driver I'm using is version 1.0.8762+2.6.15.11-3 of nvidia-glx (I think that's the info you were looking for)

where can i see what version of nvidia i am using? ](*,)  thx

---

### Post by Josh_b on 2006-08-30
I went through Synaptic and searched for nvidia-glx and it has the current version installed there.

---

### Post by Hemmer on 2006-08-30
35720 frames in 5.0 seconds = 7143.852 FPS

AMD 64 3000+
Nvidia Geforce 6600
1.5 GB RAM

---

### Post by matthew on 2006-08-30
I originally contributed to this thread on June 10, 2005 ([Post #42]("http://ubuntuforums.org/showpost.php?p=206745&postcount=42")) while using Ubuntu 5.04 (Hoary Hedgehog) and ATI driver version 8.16.20> **matthew said:**
> 7030 frames in 5.0 seconds = 1406.000 FPS
7029 frames in 5.0 seconds = 1405.800 FPS
7032 frames in 5.0 seconds = 1406.400 FPS
7030 frames in 5.0 seconds = 1406.000 FPS
7031 frames in 5.0 seconds = 1406.200 FPS
7024 frames in 5.0 seconds = 1404.800 FPS

Pentium M 745
1 Gb ram
ATI Mobility Radeon 9700I am now running 6.04 (Dapper Drake) and have made no hardware changes. Take a look:

matt@telecaster:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5814 (8.25.18)

matt@telecaster:~$ glxgears  -printfps
10863 frames in 5.0 seconds = 2172.470 FPS
10875 frames in 5.0 seconds = 2174.814 FPS
10875 frames in 5.0 seconds = 2174.809 FPS
10875 frames in 5.0 seconds = 2174.837 FPS
10874 frames in 5.0 seconds = 2174.765 FPS
10752 frames in 5.0 seconds = 2150.384 FPS
10874 frames in 5.0 seconds = 2174.645 FPS
10784 frames in 5.0 seconds = 2152.051 FPS

The new ATI drivers and whatever optimizations the developers have made from Hoary->Breezy->Dapper have caused a 50% increase in my frame rate. Yes, I'm pleased.

---

### Post by neo8750 on 2006-09-11
I win!!!

zepski@zeptop:~$ glxgears -printfps
372 frames in 5.1 seconds = 72.873 FPS
342 frames in 5.3 seconds = 64.993 FPS
342 frames in 5.4 seconds = 63.269 FPS
342 frames in 5.3 seconds = 64.847 FPS
342 frames in 5.6 seconds = 60.555 FPS
342 frames in 5.2 seconds = 65.432 FPS
342 frames in 5.2 seconds = 65.175 FPS
342 frames in 5.4 seconds = 63.364 FPS

---

### Post by brucevangeorge on 2006-09-19
4800 average.

Athlon 1800+
Ti4600. No fastwrites, No SBA. << It doesn't make any difference for me... have no idea why.

---

### Post by Josh_b on 2006-09-21
> **neo8750 said:**
> I win!!!

zepski@zeptop:~$ glxgears -printfps
372 frames in 5.1 seconds = 72.873 FPS
342 frames in 5.3 seconds = 64.993 FPS
342 frames in 5.4 seconds = 63.269 FPS
342 frames in 5.3 seconds = 64.847 FPS
342 frames in 5.6 seconds = 60.555 FPS
342 frames in 5.2 seconds = 65.432 FPS
342 frames in 5.2 seconds = 65.175 FPS
342 frames in 5.4 seconds = 63.364 FPS

....ouch....Why is your CPU underclocked?

---

### Post by enopepsoo on 2006-09-21
[PHP]6923 frames in 5.0 seconds = 1384.436 FPS
6913 frames in 5.0 seconds = 1382.497 FPS
6899 frames in 5.0 seconds = 1379.778 FPS
6924 frames in 5.0 seconds = 1384.767 FPS
6923 frames in 5.0 seconds = 1384.493 FPS
6958 frames in 5.0 seconds = 1391.532 FPS
[/PHP]

Mine is an AMD x2 3800+, w/ 2gb ddr2, and a 256mb (shared :( ) nvidia 6500.  I also have an sata hd, but I doubt it makes any difference in a test like this.:-({|=

---

### Post by enopepsoo on 2006-09-21
> **Hemmer said:**
> 35720 frames in 5.0 seconds = 7143.852 FPS

AMD 64 3000+
Nvidia Geforce 6600
1.5 GB RAM

how can someone with a system with lower specs kill my performance like that?  I must have done something wrong at some point.

---

### Post by fig_jam_uk on 2006-09-22
I tried with the orriginal Kernal then decided to upgrade just to see if there was any if much difference...

before Kernel upgrade from -- Ubuntu kernel 2.6.15-26-386

22817 frames in 5.0 seconds = 4563.310 FPS
26805 frames in 5.0 seconds = 5360.908 FPS
26940 frames in 5.0 seconds = 5387.890 FPS
26366 frames in 5.0 seconds = 5273.078 FPS
26742 frames in 5.0 seconds = 5348.305 FPS
26810 frames in 5.0 seconds = 5361.889 FPS
26876 frames in 5.0 seconds = 5375.092 FPS
26823 frames in 5.0 seconds = 5363.312 FPS
26343 frames in 5.0 seconds = 5268.505 FPS
26693 frames in 5.0 seconds = 5338.468 FPS
26813 frames in 5.0 seconds = 5362.524 FPS
26788 frames in 5.0 seconds = 5357.452 FPS
26079 frames in 5.0 seconds = 5215.731 FPS
26779 frames in 5.0 seconds = 5355.669 FPS
26859 frames in 5.0 seconds = 5371.729 FPS
26856 frames in 5.0 seconds = 5371.052 FPS

After Kernel upgrade to -- Ubuntu kernel 2.6.15-27-686


34367 frames in 5.0 seconds = 6873.297 FPS
36343 frames in 5.0 seconds = 7268.397 FPS
35821 frames in 5.0 seconds = 7164.097 FPS
12367 frames in 5.0 seconds = 2473.364 FPS
35640 frames in 5.0 seconds = 7127.833 FPS
36504 frames in 5.0 seconds = 7300.643 FPS
36560 frames in 5.0 seconds = 7311.862 FPS
36571 frames in 5.0 seconds = 7314.077 FPS
36553 frames in 5.0 seconds = 7310.488 FPS
36563 frames in 5.0 seconds = 7312.600 FPS
36571 frames in 5.0 seconds = 7314.120 FPS
36581 frames in 5.0 seconds = 7316.090 FPS
36528 frames in 5.0 seconds = 7305.454 FPS
36558 frames in 5.0 seconds = 7311.472 FPS

Nice difference!!!

AMD64 3000+
NVIDIA Gforce 6800XT
1Gb Dual channel corsair twinX
nforce MOBO

---

### Post by fig_jam_uk on 2006-09-22
> **enopepsoo said:**
> [PHP]6923 frames in 5.0 seconds = 1384.436 FPS
6913 frames in 5.0 seconds = 1382.497 FPS
6899 frames in 5.0 seconds = 1379.778 FPS
6924 frames in 5.0 seconds = 1384.767 FPS
6923 frames in 5.0 seconds = 1384.493 FPS
6958 frames in 5.0 seconds = 1391.532 FPS
[/PHP]

Mine is an AMD x2 3800+, w/ 2gb ddr2, and a 256mb (shared :( ) nvidia 6500.  I also have an sata hd, but I doubt it makes any difference in a test like this.:-({|=

Thatll probably be your problem im afraid..

---

### Post by erikpiper on 2006-09-29
77351 frames in 5.0 seconds = 15470.152 FPS
84233 frames in 5.0 seconds = 16846.418 FPS
84214 frames in 5.0 seconds = 16842.688 FPS
84235 frames in 5.0 seconds = 16846.896 FPS
84309 frames in 5.0 seconds = 16861.742 FPS


On a fairly fresh instillation... Gotta be a way to boost these scores..

(Nvidia 7900Gt 256)

---

### Post by Joh_ on 2006-09-29
```
$ glxgears -printfps
1211 frames in 5.0 seconds = 242.168 FPS
1219 frames in 5.0 seconds = 243.588 FPS
1215 frames in 5.0 seconds = 242.833 FPS
1203 frames in 5.0 seconds = 240.535 FPS
1068 frames in 5.0 seconds = 213.576 FPS
```

AMD Duron 1.6 GHz
768 MB DDR400 (aka PC3200)
ATI Radeon 9600 (with latest fglrx, correctly configured)
Edgy Beta 1

I absolutely loathe ATI's linux drivers... Next graphics card I'm buying will be an nVidia. ](*,)

**Edit:** I just saw this is in the Hoary forum. Got here from a search. :p

---

### Post by KamakazieX on 2006-10-12
$ glxgears -printfps
53799 frames in 5.0 seconds = 10759.699 FPS
53780 frames in 5.0 seconds = 10755.898 FPS
53752 frames in 5.0 seconds = 10750.277 FPS
53735 frames in 5.0 seconds = 10746.953 FPS

My sweet new Pentium D 3.4Ghz with my 2.6.18 kernel I built optimized for P4 SMP XEON. The latest nvidia drivers built from source. :-D

---

### Post by KamakazieX on 2006-10-12
> **KamakazieX said:**
> $ glxgears -printfps
53799 frames in 5.0 seconds = 10759.699 FPS
53780 frames in 5.0 seconds = 10755.898 FPS
53752 frames in 5.0 seconds = 10750.277 FPS
53735 frames in 5.0 seconds = 10746.953 FPS

My sweet new Pentium D 3.4Ghz with my 2.6.18 kernel I built optimized for P4 SMP XEON. The latest nvidia drivers built from source. :-D

Ah forgot specs..

newegg BFGTech 7600, only 512 pc4300 right now, going for 2gb
blows away windows gaming!

---

### Post by KamakazieX on 2006-10-12
Fullscreen @ 1280x1024 @ 24bit

$ glxgears -fullscreen -printfps
8446 frames in 5.0 seconds = 1689.086 FPS

---

### Post by AllFather on 2006-10-14
88703 frames in 5.0 seconds = 17740.420 FPS

---

### Post by russianpirate on 2006-10-15
Athlon64 3500+ ~2.49GHZ
GeForce 6800 128MB
1GB Rosewill Value
Nvidia Driver 9625 Beta

```
42947 frames in 5.0 seconds = 8565.169 FPS
```

I used to get 10000+ fps on my archlinux setup, but I had the 16pipes/6vertex unlocked and it was overclocked. I just use ubuntu for fun, and windows for gaming ;)

---

### Post by FarmerGiles on 2006-10-15
ATI Radeon X1900XT

glgears = 18406

92032 frames in 5.0 seconds = 18406.334 FPS

Fullscreen: (1280*1024)

20163 frames in 5.0 seconds = 4032.432 FPS

---

### Post by jdunn on 2006-10-15
glxgears is not a good benchmark.  *sigh*....Nevertheless, my score is

22852 frames in 5.0 seconds = 4570.205 FPS

That's with a standard sized glxgears window (not hidden).  My system specs are:

Intel Pentium (Northwood) 2.8 GHz
1 GB DDR (not sure what type)
GeForce 5600 Ultra 128MB
GLX Driver 8762

---

### Post by OffHand on 2006-10-16
15900 frames in 5.0 seconds = 3180 FPS

AMD Athlon 3500+ Venice @ 2350Mhz
Aopen Aeolus PCX6600-DV256 Nvidia
1024 MB Dual Channel  (cheap memory)
160GB 7200 RPM 8MB Hard Disk

Thought I would do better than this with my setup.

---

### Post by Juzz on 2006-10-16
$ glxgears -printfps
6393 frames in 5.0 seconds = 1278.535 FPS
6851 frames in 5.0 seconds = 1370.110 FPS
6851 frames in 5.0 seconds = 1370.084 FPS
6860 frames in 5.0 seconds = 1371.827 FPS
6863 frames in 5.0 seconds = 1372.538 FPS
6864 frames in 5.0 seconds = 1372.747 FPS
6843 frames in 5.0 seconds = 1368.404 FPS

I achieved this on my notebook with ATi X200 integrated graphics - using the 8.24.8 drivers.
I have 1GB of DDR400 Ram in the machine of which the 128 are set aside to the gfx, and my CPU is and AMD Turion 1.6GHz.

Cheers
Juzz

---

### Post by Carrots171 on 2006-10-17
Around 9,780 FPS 

1 GB RAM
AMD Athlon XP 2500+
Nvidia GeForce 6800XT (with all 16 pipelines and 6 vertex units unlocked with Nvclock)

---

### Post by jhenager on 2006-10-17
This is about what I am getting.
5167 frames in 5.0 seconds = 1033.400 FPS
5509 frames in 5.0 seconds = 1101.800 FPS
5509 frames in 5.0 seconds = 1101.800 FPS
5509 frames in 5.0 seconds = 1101.800 FPS

Must be my el-cheapo PC Chips P23G motherboard.

---

### Post by voided3 on 2006-10-17
10473 frames in 5.0 seconds = 2094.485 FPS

....which was yeilded by:

AMD Athlon XP-M 1800+ @ 1363 MHz
1.0 gig SDRAM 
ATI Radeon 9250 w/ 256mb DDR
15" HP f50 LCD @ 1024x768

---

### Post by binks on 2006-10-18
binks@binks-desktop:~$ glxgears -printfps
22024 frames in 5.0 seconds = 4404.634 FPS
22029 frames in 5.0 seconds = 4405.621 FPS
22012 frames in 5.0 seconds = 4402.292 FPS
22030 frames in 5.0 seconds = 4405.892 FPS
22028 frames in 5.0 seconds = 4405.410 FPS


p4 3.0 ghz on a asus p4p800 mobo 1 gig corsair xms paired ram and a asus 9600 xt dvi graphics card (none of which is overclocked atm but will play sat to see if i can kill the card as  now have a nvidia spare
lol just watch me

---

### Post by BatteryCell on 2006-10-19
```
joe@kubuntu:~# glxgears -printfps
92839 frames in 5.0 seconds = 18567.785 FPS
107448 frames in 5.0 seconds = 21489.531 FPS
107385 frames in 5.0 seconds = 21476.934 FPS
107386 frames in 5.0 seconds = 21477.168 FPS
104836 frames in 5.0 seconds = 20967.154 FPS
107236 frames in 5.0 seconds = 21447.105 FPS
107252 frames in 5.0 seconds = 21450.330 FPS
107313 frames in 5.0 seconds = 21462.502 FPS
106921 frames in 5.0 seconds = 21384.061 FPS
107329 frames in 5.0 seconds = 21465.645 FPS
105755 frames in 5.0 seconds = 21150.963 FPS
105574 frames in 5.0 seconds = 21114.678 FPS
106123 frames in 5.0 seconds = 21224.545 FPS
105645 frames in 5.0 seconds = 21128.951 FPS
107170 frames in 5.0 seconds = 21433.963 FPS

```
AMD 3800+
Asus A8N-SLI Deluxe
1 gig corsair ram
Geforce 7900 gt
Running at 1280x1024

---

### Post by hstokholm on 2006-10-21
heine@ubuntu:~$ glxgears -printfps
64553 frames in 5.0 seconds = 12910.593 FPS
64583 frames in 5.0 seconds = 12916.523 FPS
64583 frames in 5.0 seconds = 12916.588 FPS
64579 frames in 5.0 seconds = 12915.635 FPS
64617 frames in 5.0 seconds = 12923.360 FPS
64598 frames in 5.0 seconds = 12919.566 FPS
64599 frames in 5.0 seconds = 12919.603 FPS
64593 frames in 5.0 seconds = 12918.475 FPS
64628 frames in 5.0 seconds = 12925.494 FPS
64602 frames in 5.0 seconds = 12920.247 FPS

amd x2 4200+
asus A8 sli
ati x1800xt 512 mb ddr3
1 gig corsair ram
and running at 1440 * 900

I really should have bought a nvidia :P

---

### Post by nothreat33 on 2006-10-21
62025 frames in 5.0 seconds = 12404.918 FPS
61119 frames in 5.0 seconds = 12223.753 FPS
82633 frames in 5.0 seconds = 16526.455 FPS
61209 frames in 5.0 seconds = 12241.639 FPS
61807 frames in 5.0 seconds = 12361.312 FPS

running ubuntu 6.06  @ 32-bit SMP

[http://image28.webshots.com/28/3/98/56/2499398560085076651FLEtWq_fs.jpg](http://image28.webshots.com/28/3/98/56/2499398560085076651FLEtWq_fs.jpg)

---

### Post by 311Sam on 2006-10-21
825fps

1ghz p3m
768mb
geforce2go

:p

---

### Post by ~LoKe on 2006-10-21
I must be doing something wrong...
> loke@x04d:~$ glxgears -printfps
329 frames in 5.0 seconds = 65.703 FPS
342 frames in 5.0 seconds = 68.267 FPS
349 frames in 5.0 seconds = 69.641 FPS
354 frames in 5.0 seconds = 70.610 FPS
368 frames in 5.0 seconds = 73.444 FPS
365 frames in 5.0 seconds = 72.974 FPS
362 frames in 5.0 seconds = 72.213 FPS
364 frames in 5.0 seconds = 72.673 FPS
361 frames in 5.0 seconds = 72.003 FPS
356 frames in 5.0 seconds = 71.087 FPS

E6300 Core 2 Duo @ 2.17GHz
1GB (2x512) Corsair DDR2 RAM
XFX nVidia 7300GT /w Beta Drivers

Are there any optimal settings to raise my FPS?

---

### Post by JamesTheBard on 2006-10-22
Just got done "upgrading" the computer due to a motherboard failure. 
Before:
```

62730 frames in 5.0 seconds = 12527.883 FPS
62354 frames in 5.0 seconds = 12457.127 FPS
63754 frames in 5.0 seconds = 12747.658 FPS
64644 frames in 5.0 seconds = 12928.798 FPS

```
After:
```

jamesthebard@phoenix:~$ glxgears -printfps
55149 frames in 5.0 seconds = 11029.691 FPS
54928 frames in 5.0 seconds = 10985.548 FPS
55226 frames in 5.0 seconds = 11045.162 FPS
55158 frames in 5.0 seconds = 11031.594 FPS

```
Maybe not really an upgrade.](*,)

---

### Post by DraeLee on 2006-10-22
9554 frames in 5.0 seconds = 1910.720 FPS
9938 frames in 5.0 seconds = 1987.461 FPS
9923 frames in 5.0 seconds = 1984.576 FPS
10696 frames in 5.0 seconds = 2137.221 FPS
10675 frames in 5.0 seconds = 2134.970 FPS
10728 frames in 5.0 seconds = 2145.483 FPS
10718 frames in 5.0 seconds = 2143.594 FPS
10745 frames in 5.0 seconds = 2148.949 FPS
10670 frames in 5.0 seconds = 2133.515 FPS
10719 frames in 5.0 seconds = 2143.710 FPS
10706 frames in 5.0 seconds = 2141.182 FPS
10692 frames in 5.0 seconds = 2138.287 FPS
10747 frames in 5.0 seconds = 2149.364 FPS
10647 frames in 5.0 seconds = 2129.398 FPS
10705 frames in 5.0 seconds = 2140.844 FPS
10730 frames in 5.0 seconds = 2145.842 FPS
10657 frames in 5.0 seconds = 2131.311 FPS
10734 frames in 5.0 seconds = 2141.163 FPS
10560 frames in 5.0 seconds = 2111.834 FPS



heres mine amd64 3200+ 
Nvidia 5200 128mb
1gig ram

---

### Post by Cuppa-Chino on 2006-10-25
finally got a card that works:

~$ glxgears -printfps
37271 frames in 5.0 seconds = 7454.186 FPS
37008 frames in 5.0 seconds = 7401.580 FPS
31822 frames in 5.0 seconds = 6364.385 FPS
37000 frames in 5.0 seconds = 7399.726 FPS
37032 frames in 5.0 seconds = 7406.321 FPS
36672 frames in 5.0 seconds = 7334.386 FPS
37882 frames in 5.0 seconds = 7576.246 FPS
38079 frames in 5.0 seconds = 7615.640 FPS
37923 frames in 5.0 seconds = 7584.465 FPS
37937 frames in 5.0 seconds = 7587.335 FPS
37889 frames in 5.0 seconds = 7577.771 FPS
36821 frames in 5.0 seconds = 7364.062 FPS

nvidia 7900gto
1gig ram
p4C 2.4Ghz

---

### Post by dresnu on 2006-10-27
```
5831 frames in 5.0 seconds = 1166.113 FPS
6488 frames in 5.0 seconds = 1297.556 FPS
6822 frames in 5.0 seconds = 1363.261 FPS
6879 frames in 5.0 seconds = 1375.675 FPS
6789 frames in 5.0 seconds = 1357.634 FPS
6655 frames in 5.0 seconds = 1331.000 FPS
6818 frames in 5.0 seconds = 1363.506 FPS
6593 frames in 5.0 seconds = 1318.437 FPS
6881 frames in 5.0 seconds = 1376.136 FPS
6959 frames in 5.0 seconds = 1391.629 FPS
6758 frames in 5.0 seconds = 1351.530 FPS

```

Not much I know, but taking into account that I get these results on a 4-year old P4-mobile laptop with a 32MB mobility radeon 7500 while running beryl composite manager... well I reckon these results to be pretty acceptable.

Thanks Edgy! :-D

---

### Post by Juzz on 2006-10-28
glxgears -printfps
33985 frames in 5.0 seconds = 6796.902 FPS
34009 frames in 5.0 seconds = 6801.769 FPS
34017 frames in 5.0 seconds = 6803.308 FPS
34004 frames in 5.0 seconds = 6800.692 FPS
34018 frames in 5.0 seconds = 6803.570 FPS

On my stationary:

PIV 2.8GHz
2GB RAM
Geforce 6600GT

---

### Post by loko on 2006-10-28
glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x5b
3895 frames in 5.0 seconds = 778.864 FPS
4011 frames in 5.0 seconds = 802.074 FPS
4014 frames in 5.0 seconds = 802.603 FPS
4006 frames in 5.0 seconds = 801.153 FPS
4015 frames in 5.0 seconds = 802.858 FPS
4013 frames in 5.0 seconds = 802.527 FPS
3883 frames in 5.0 seconds = 776.540 FPS


Edgy Eft
T2300 Core Duo
512MB DDR2@533Mhz
Intel 945GM

---

### Post by reidbold on 2006-10-29
~10600

amd 3200+
nvidia 7600gt

---

### Post by electricshoes on 2006-10-29
$ glxgears -printfps
92727 frames in 5.0 seconds = 18545.285 FPS
98125 frames in 5.0 seconds = 19624.930 FPS
98868 frames in 5.0 seconds = 19773.529 FPS
94991 frames in 5.0 seconds = 18998.105 FPS
100571 frames in 5.0 seconds = 20114.010 FPS
91950 frames in 5.0 seconds = 18389.912 FPS
52464 frames in 5.0 seconds = 10492.746 FPS
89669 frames in 5.0 seconds = 17933.734 FPS
91302 frames in 5.0 seconds = 18260.316 FPS

---

### Post by mbirkis on 2006-10-30
$ glxgears -printfps
44027 frames in 5.0 seconds = 8805.256 FPS
46540 frames in 5.0 seconds = 9307.944 FPS
67068 frames in 5.0 seconds = 13413.570 FPS
77334 frames in 5.0 seconds = 15466.648 FPS
78195 frames in 5.0 seconds = 15638.848 FPS
75312 frames in 5.0 seconds = 15062.370 FPS
78094 frames in 5.0 seconds = 15618.624 FPS
73958 frames in 5.0 seconds = 14791.506 FPS
71507 frames in 5.3 seconds = 13453.748 FPS
76699 frames in 5.0 seconds = 15339.615 FPS
68549 frames in 5.0 seconds = 13709.772 FPS
77561 frames in 5.0 seconds = 15512.031 FPS

nvidia 6800 card

---

### Post by jc87 on 2006-10-30
```
 glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
11521 frames in 5.0 seconds = 2304.127 FPS
11522 frames in 5.0 seconds = 2304.266 FPS
11522 frames in 5.0 seconds = 2304.250 FPS
11527 frames in 5.0 seconds = 2305.393 FPS
```

[B]
Ubuntu 6.10[/B]
[B]
Ati Radeon 9250[/B] @ open source radeon driver [tutorial](https://help.ubuntu.com/community/RadeonDriver)

**Pentium 4 1700 hz**

**512 DDR 400**

My [xorg.conf](http://clientes.netvisao.pt/xw166644/xorg.conf)

---

### Post by RTB-UK on 2006-10-30
tom@tom-ubuntu:~$ glxgears -printfps
54900 frames in 5.0 seconds = 10975.813 FPS
58341 frames in 5.0 seconds = 11668.108 FPS
58147 frames in 5.0 seconds = 11629.328 FPS
72035 frames in 5.0 seconds = 14406.865 FPS
84882 frames in 5.0 seconds = 16976.365 FPS
84775 frames in 5.0 seconds = 16954.852 FPS
80589 frames in 5.0 seconds = 16117.745 FPS
82146 frames in 5.0 seconds = 16429.191 FPS


6800GT 400/1100
3700 san diego 2.2ghz
1gb OcZ rev 2 plat 200mhz 2,2,2,5

---

### Post by sloggerkhan on 2006-11-01
with stuff in the backround and at near full screen, I get 

[COLOR="Blue"]1038 frames in 5.0 seconds = 207.419 FPS[/COLOR]

(full screen res would be 1680x1050, so full width - ~60 pixels height for window bars, panels, so say maybe 1680x990)

Something interesting: if glx gears is running, and I mouse over the other open windows on the taskbar/dock panel, it freezes for a moment when my mouse switches which app-box it is over.

and with flg_glxgears I get

[COLOR="Blue"]746 frames in 5.0 seconds = 149.200 FPS[/COLOR]

at the same near-full screen resolution.

err.. ooops, mean fgl_gears...

oh, my hardware:

turion 64 2ghz, x700 mobility 128

---

### Post by ~LoKe on 2006-11-01
```
loke@x04d:~$ glxgears
21198 frames in 5.0 seconds = 4231.228 FPS
21760 frames in 5.0 seconds = 4351.891 FPS
19121 frames in 5.0 seconds = 3815.068 FPS
23285 frames in 5.0 seconds = 4645.215 FPS
23484 frames in 5.0 seconds = 4696.785 FPS
24108 frames in 5.0 seconds = 4821.523 FPS

```

---

### Post by RizSilverthorn on 2006-11-01
**Default size**
GLXGears visible:
fred@dangermouse:~$ glxgears -printfps
75474 frames in 5.0 seconds = 15094.777 FPS
88813 frames in 5.0 seconds = 17762.568 FPS
88841 frames in 5.0 seconds = 17768.074 FPS
88842 frames in 5.0 seconds = 17768.240 FPS
88837 frames in 5.0 seconds = 17767.225 FPS

GLXGears hidden behind console:
fred@dangermouse:~$ glxgears -printfps
87066 frames in 5.0 seconds = 17413.121 FPS
110705 frames in 5.0 seconds = 22140.898 FPS
110805 frames in 5.0 seconds = 22160.826 FPS
110782 frames in 5.0 seconds = 22156.223 FPS
110961 frames in 5.0 seconds = 22192.080 FPS
111169 frames in 5.0 seconds = 22233.742 FPS
111205 frames in 5.0 seconds = 22240.951 FPS
111280 frames in 5.0 seconds = 22255.895 FPS
111119 frames in 5.0 seconds = 22223.752 FPS

Maximised (1280x1024)
fred@dangermouse:~$ glxgears -printfps
17242 frames in 5.0 seconds = 3448.093 FPS
9407 frames in 5.0 seconds = 1881.354 FPS
9457 frames in 5.0 seconds = 1891.204 FPS
9564 frames in 5.0 seconds = 1912.745 FPS
15156 frames in 5.0 seconds = 3031.050 FPS
19952 frames in 5.0 seconds = 3990.302 FPS
(scores 2-4 full screen on top, 5-6 full screen minimised)

AMD Athlon64 4800+ X2, MSI 7950GT ViVo, Asus A8N32-SLI Deluxe, 2GB DDR400. Fresh install of Edgy and latest stable nvidia drivers. And still get the same crappy performance (@29-32fps D3D or OpenGL)in WoW under Cedega as I was getting with a A64 3200+, 1GB & no-name 6600

---

### Post by sloggerkhan on 2006-11-01
Do you know if mobility radeons have hardware limiting? I know that back on windows I played a lot of ET and the frame rate was always EXACTLY 90fps, pretty much no matter what the settings....

---

### Post by sp4rd on 2006-11-02
linuxinfo
Linux stevesbox9 2.6.17-2-k7 #1 SMP Wed Sep 13 17:18:46 UTC 2006
One AMD Unknown 1601MHz processor, 3208.26 total bogomips, 256M RAM

---
matrox G400+MILN/16/IB2 with SGRAM IBM FRU 01N2197 008
lspci -n
01:00.0 0300: 102b:0525 (rev 04)

grep -i -a1 "Module class: X.Org Video Driver" /var/log/Xorg.0.log         
	compiled for 7.1.1, module version = 1.4.4
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.0

.drirc
<driconf>
    <device screen="0" driver="mga">
        <application name="Default">
            <option name="no_rast" value="false" />
            <option name="texture_depth" value="1" />
            <option name="nv_vertex_program" value="true" />
            <option name="arb_vertex_program" value="true" />
            <option name="color_reduction" value="0" />
            <option name="vblank_mode" value="1" />
        </application>
    </device>
</driconf>

matrox G400+MILN/16/IB2 xorg7.1/aiglx/compiz @1024x768-60 depth 16bit with compiz
steve@stevesbox9:~$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
4004 frames in 5.0 seconds = 800.664 FPS
3996 frames in 5.0 seconds = 799.159 FPS
3999 frames in 5.0 seconds = 799.694 FPS
3993 frames in 5.0 seconds = 798.484 FPS
3996 frames in 5.0 seconds = 799.076 FPS

---
nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)

lspci -n
01:00.0 0300: 10de:0110 (rev a1)

grep -i -a1 "Module class: X.Org Video Driver" /var/log/Xorg.0.log
        compiled for 4.0.2, module version = 1.0.9625
        Module class: X.Org Video Driver

GeForce2 MX/MX 400 xorg7.1/nvidia(aiglx)/compiz @1024x768-60 depth 16bit no compiz
steve@stevesbox9:~$ glxgears -printfps
6812 frames in 5.0 seconds = 1362.280 FPS
6818 frames in 5.0 seconds = 1363.533 FPS
6815 frames in 5.0 seconds = 1362.891 FPS
6820 frames in 5.0 seconds = 1363.814 FPS
6817 frames in 5.0 seconds = 1363.351 FPS

GeForce2 MX/MX 400 xorg7.1/nvidia(aiglx)/compiz @1024x768-60 depth 24bit no compiz
steve@stevesbox9:~$ glxgears -printfps
3793 frames in 5.0 seconds = 758.531 FPS
3797 frames in 5.0 seconds = 759.272 FPS
3794 frames in 5.0 seconds = 758.786 FPS
3797 frames in 5.0 seconds = 759.387 FPS
3796 frames in 5.0 seconds = 759.014 FPS

GeForce2 MX/MX 400 xorg7.1/nvidia(aiglx)/compiz @1024x768-60 depth 24bit with compiz
steve@stevesbox9:~$ glxgears -printfps
2765 frames in 5.0 seconds = 552.544 FPS
2765 frames in 5.0 seconds = 552.499 FPS
2767 frames in 5.0 seconds = 553.279 FPS
2759 frames in 5.0 seconds = 551.459 FPS
2763 frames in 5.0 seconds = 552.587 FPS

can't run compiz in 16bit with nvidia's beta driver :(
steve@stevesbox9:~$ compiz --replace
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz.real: No GLXFBConfig for depth 32

---

### Post by brj on 2006-11-03
Linux: Edgy
Card: ATI Radeon 9200 
Driver: radeon
CPU: AMD Athlon XP 2700

jakob@oahu:~$ glxgears -printfps
8250 frames in 5.0 seconds = 1649.915 FPS
8250 frames in 5.0 seconds = 1649.887 FPS
8251 frames in 5.0 seconds = 1650.156 FPS
8250 frames in 5.0 seconds = 1649.883 FPS
8248 frames in 5.0 seconds = 1649.451 FPS

---

### Post by jimrz on 2006-11-05
> **chronusdark said:**
> how the heck do you get benchmarks when i run glxgears it just goes forever and never does anything

```
glxgears -printfps
```

this will show the scores in your terminal window

---

### Post by jimrz on 2006-11-05
GF4 MX 440 - 64 Mb / P3 1 Ghz / 512 Mb ram

dapper / driver from the repositories

with Firefox + Evolution running in background and gears window active

```
5284 frames in 5.0 seconds = 1056.679 FPS
5282 frames in 5.0 seconds = 1056.359 FPS
5268 frames in 5.0 seconds = 1053.442 FPS
5280 frames in 5.0 seconds = 1055.958 FPS
5276 frames in 5.0 seconds = 1055.023 FPS
5276 frames in 5.0 seconds = 1055.188 FPS
5288 frames in 5.0 seconds = 1057.496 FPS
5284 frames in 5.0 seconds = 1056.618 FPS
5271 frames in 5.0 seconds = 1054.059 FPS
5291 frames in 5.0 seconds = 1058.020 FPS
5286 frames in 5.0 seconds = 1057.116 FPS
5282 frames in 5.0 seconds = 1056.341 FPS
5273 frames in 5.0 seconds = 1054.570 FPS

```

not too bad for an old rig

---

### Post by Marsan on 2006-11-05
p4 2.8 ghz HT
1gb RAM
Fx 5700 256mb

```
marsan@marsan-desktop:~$ glxgears -printfps
14334 frames in 5.0 seconds = 2866.727 FPS
14812 frames in 5.0 seconds = 2962.323 FPS
14698 frames in 5.0 seconds = 2939.404 FPS
14700 frames in 5.0 seconds = 2939.984 FPS
14705 frames in 5.0 seconds = 2940.870 FPS
14744 frames in 5.0 seconds = 2948.607 FPS

```

---

### Post by mithras86 on 2006-11-05
Amd64 3200+ venice (running 32bits)
1GB ram
Nvidia 6600GT
```
jurian@karlijn:~$ glxgears -printfps
20937 frames in 5.0 seconds = 4186.151 FPS
23489 frames in 5.0 seconds = 4697.670 FPS
24611 frames in 5.0 seconds = 4921.425 FPS
24605 frames in 5.0 seconds = 4920.894 FPS
```Not really bad :p

This is just with glxgears visible with default window size (and running Beryl)

---

### Post by drphilngood on 2006-11-05
**[COLOR="Sienna"]_nVidia  7800GTX clocked @ 500/1295_[/COLOR]**
[SIZE="2"]111098 frames in 5.0 seconds = 22219.422 FPS
111889 frames in 5.0 seconds = 22377.670 FPS
111918 frames in 5.0 seconds = 22383.527 FPS
111945 frames in 5.0 seconds = 22388.955 FPS
112044 frames in 5.0 seconds = 22408.701 FPS
111918 frames in 5.0 seconds = 22383.451 FPS
111277 frames in 5.0 seconds = 22255.293 FPS
111539 frames in 5.0 seconds = 22307.625 FPS
111458 frames in 5.0 seconds = 22291.537 FPS
[/SIZE]

[SIZE="1"][I]Asus A8N-SLI Premium | AMD x2 4800+ (939) |  eVga 7800 GTX (8776 driver)
2 gig Patriot | Audigy 2 Platinum | Lian-Li V-1000 Plus | Leadtek TV2000 XP
20.1¨ Symaster 204T @ 1600x1200 |*home built rig in June 2005*[/I][/SIZE]

---

### Post by Buickman on 2006-11-05
P4 630 3.0 (oc'd to 3.6)
2 Gig DDR
Asus P5P800 SE
ATI X850 XT AGP

Dapper
49111 frames in 5.0 seconds = 9822.161 FPS
48595 frames in 5.0 seconds = 9718.939 FPS
49069 frames in 5.0 seconds = 9813.745 FPS
49073 frames in 5.0 seconds = 9814.502 FPS
49068 frames in 5.0 seconds = 9813.469 FPS
47811 frames in 5.0 seconds = 9562.072 FPS


Edgy
2512 frames in 5.0 seconds = 502.064 FPS
2502 frames in 5.0 seconds = 500.373 FPS
2500 frames in 5.0 seconds = 499.973 FPS
2500 frames in 5.0 seconds = 499.973 FPS
2503 frames in 5.0 seconds = 500.573 FPS
2503 frames in 5.0 seconds = 500.573 FPS
2509 frames in 5.0 seconds = 501.773 FPS

All I can say is...Wow. I've got some work to do. I've followed all the instructions for installing the ATI driver for edgy. Back to the drawing board.

---

### Post by Dual Cortex on 2006-11-05
felipe@LinuxDesktop:~$ glxgears -printfps
13670 frames in 5.0 seconds = 2733.888 FPS
13661 frames in 5.0 seconds = 2732.028 FPS
13678 frames in 5.0 seconds = 2735.480 FPS
13659 frames in 5.0 seconds = 2731.760 FPS
13664 frames in 5.0 seconds = 2732.723 FPS


Dell 4700
P4 530 3GHz HT
2*256MB DDR2-400
7300LE @ 530/873

---

### Post by mr.Data on 2006-11-05
33720 frames in 5.0 seconds = 6743.829 FPS
33920 frames in 5.0 seconds = 6783.832 FPS
33843 frames in 5.0 seconds = 6768.518 FPS
33794 frames in 5.0 seconds = 6758.665 FPS


Athlon 2500XP+, GF-6600GT 1.2Gig Ram.

How do i Enable fast Write?

---

### Post by dhsafe on 2006-11-05
[/code]
akiro@akiro-desktop:~$ glxgears
7308 frames in 5.0 seconds = 1461.531 FPS
7315 frames in 5.0 seconds = 1462.891 FPS
7113 frames in 5.0 seconds = 1422.407 FPS
akiro@akiro-desktop:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled
akiro@akiro-desktop:~$ sudo lspci -v
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp.: Unknown device a341
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 193
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at feae0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 3.0

akiro@akiro-desktop:~$ glxinfo | grep rendering
direct rendering: Yes
[code/]

My rig:
ASRock 775v88+
Celeron D 326
756MB DDR
EVGA 6200 256MB

I'm a little disappointed...
I expected better from this card..
Are there any tweak guides to enable better performance..

---

### Post by ThomasA76 on 2006-11-05
Dont think youre gonna get more than that, since your gfx-card sucks...and so do my card, i have a GMA950 integrated and get about 950p ;) Neither my card or your card is a gamingcard...Sorry to say that ;)

---

### Post by phoqueyoo on 2006-11-05
15146 frames in 5.0 seconds = 3029.194 FPS
15113 frames in 5.0 seconds = 3022.578 FPS
15118 frames in 5.0 seconds = 3023.597 FPS

w/ ati 7500 aiw and athlon xp 3000 (after lots of tweaking)

---

### Post by jjandrj6679 on 2006-11-07
Hi all here are my scores for my 1st attempt.

Not Overclocked 2244Mhz
================
Max
11710.098 FPS

Average in front
11602.305 FPS

Behind The Terminal
17396.070 FPS

Is there a score board so that we can see the results anywhere?

Is there any benchmarking software avalible I used 3DMark05 and ATI Rm Clock foe O?C my GPU. Does anyone know where I can find then, I am completely new to linux into my 3rd week now of no XP
 
LFTHFUS
Josh

---

### Post by jjandrj6679 on 2006-11-07
Ive just had a look at the results of the last few pages, some of them are truely awful like "mithras86" his system closely matches mine:-
```

mithras86                      mine  
Amd64 3200+ 90nm         Amd64 3500+ 90nm
1GB ram                        1GB XMS Matchedram
Nvidia 6600GT                 Nvidia 6800GT 256
(running 32bits)              (running 64bits)

4920.894 FPS           11710.098 FPS

```

---

### Post by jjandrj6679 on 2006-11-07
Oops pressed the wrong button.

So to me either there is something wrong with mithras86 system, or maybe its not setup right, Surly a 6600gt can't be that useless? can it.

So may I make a suggestion to the moderators, as there has been so much interest in this little prog & what fun its created, for the benefit of others and just for fun, would it be possible to set up some kind of system that could be used to keep track of the scores and also hold details of the system, say CPU, GPU, Ram, M/B Overclocked or not. A: to have fun & B: check if you system is as good as others or simular specs.

I have no idea if it is possible here but I have seen it on other sites that keeps score

mithras86 feel free to PM me as I am interested as to why your score is so low.
Yours
Josh

---

### Post by CowzRule on 2006-11-11
```
[COLOR="Red"]6031.287 FPS[/COLOR]
```ATI X800 Pro
Athlon XP 3200+
1GB ram
With the **ATI** driver from a fresh install of Ubuntu Edgy
My xorg.config settings
```
Section "Device"
	Identifier	"ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Driver		"radeon"
	Option          "AGPMode" "8"
	Option          "ColorTiling" "on"	
	Option          "AccelMethod" "XAA"
	Option          "EnablePageFlip" "on"
	Option		"XAANoOffScreenPixMaps"
	Option		"RenderAccel" "true"
	Option 		"MergedFB" "true"
	Option		"MonitorLayout" "LCD, CRT"
	Option		"CRT2Hsync" "30-70"
	Option		"CRT2VRefresh" "50-150"
	Option		"CRT2Position" "RightOf"
	Option		"MetaModes" "1024x768-1024x768"
	BusID		"PCI:1:0:0"
EndSection
```

---

### Post by ilkerka on 2006-11-12
Average, excluding the first one
FPS: 11100
Edit: I realised that i was just looking at terminal sometime while benchmarking which increased the fps increadibly. If glxgears is always in focus it is reduced to around 4000
System:
AMD Athlon XP 2500+
ATI 9600XT Sapphire 256MB
1.5gb ram
Dapper Gnome desktop

---

### Post by OceanSoul on 2006-11-25
Greetings.

AMD Athlon(tm) 64 Processor 3400+
ATI Radeon 9600XT
1024 DDR
(With 32bits Ubuntu installed, because of lots of errors installing the drivers and other incompatibilities)

1324 frames in 5.0 seconds = 264.794 FPS
1132 frames in 5.0 seconds = 226.392 FPS
1124 frames in 5.0 seconds = 224.792 FPS
1266 frames in 5.0 seconds = 253.191 FPS
1309 frames in 5.0 seconds = 261.790 FPS
1313 frames in 5.0 seconds = 262.591 FPS
1319 frames in 5.0 seconds = 263.790 FPS
1317 frames in 5.0 seconds = 263.390 FPS
1308 frames in 5.0 seconds = 261.591 FPS
1317 frames in 5.0 seconds = 263.390 FPS

It never gets better than this, and the image of glxgears is not very fast, as it should be.

I installed the Ubuntu drivers yesterday (the Method 1 from the wiki*, with apt-get), and:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

I'm sure there is something wrong. It's true I can use tuxkart with some stability and even Enemy Territory... But I have a great graphics card. It was expensive, and it was supposed to be great. ATI. Bah.

I have a question: Is it possible this slowness is due to the repository's drivers? Sometimes the repositories only have stable versions. It is like Widelands. They stopped the creation of stable versions, and I could only get the latest stable version. When I got the one from the site, it was a much more advanced version, but not a stable one. Maybe I should try Method 2? I tried all this methods when I had the 64 bit version of Ubuntu, but nothing worked. Now the first method worked just fine. Lets see. I will try it.

What should I do?

Thanks in advance.

*(this is the wiki: 
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide))

---

### Post by OceanSoul on 2006-11-25
I followed the Method 2.

1343 frames in 5.0 seconds = 268.590 FPS
1359 frames in 5.0 seconds = 271.790 FPS
1297 frames in 5.0 seconds = 259.390 FPS
1313 frames in 5.0 seconds = 262.590 FPS
1313 frames in 5.0 seconds = 262.591 FPS
1333 frames in 5.0 seconds = 266.590 FPS
1318 frames in 5.0 seconds = 263.590 FPS

The same. So they must be doing the same. 

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6174 (8.31.5)

```

```
$ glxinfo | grep render
direct rendering: Yes

```

I am now going to try to find here in Ubuntuforums other ways to install the drivers.

Anything you think I should do?

Thanks in advance.

---

### Post by burwaco on 2006-11-25
well, whe I run glxgears I get an error...
glsgears runs fine but I bon't get FPS...
this is the error:

```

root@box:/# glxgears 
libGL warning: 3D driver claims to not support visual 0x4b

```

---

### Post by xenoalien on 2006-11-25
> **ruben_b said:**
> does anybody use an intel 915GM 128mb shared memory?
i only get 800fps and i can´t believe thats all!?

my old geforce 420 go had allready 1500fps.
It is slow because your memory is being shared and your video and sound are most likely integrated which means your processor is being robbed of its recourse causing your PC to be slow and get low fps. If you want a fast computer make sure you have the least amount of integrated parts. My motherboard came with integrated sound. I turned it off in the bios and put in a pci soundcard and it makes games especially, run a lot faster.

---

### Post by Pathfinder_ on 2006-11-25
> **burwaco said:**
> well, whe I run glxgears I get an error...
glsgears runs fine but I bon't get FPS...
this is the error:

```

root@box:/# glxgears 
libGL warning: 3D driver claims to not support visual 0x4b

```

this just means that you are using the driver that comes with edgy. i get the same thing. to get fps type: glxgears -printfps

---

### Post by slimdog360 on 2006-11-25
nick@ubuntu:~$ glxgears -printfps
21128 frames in 5.0 seconds = 4225.334 FPS
24836 frames in 5.0 seconds = 4967.071 FPS
24856 frames in 5.0 seconds = 4971.002 FPS
24801 frames in 5.0 seconds = 4960.161 FPS
24850 frames in 5.0 seconds = 4969.954 FPS

Althon XP 2800 @ ~ 2.1GHz
1GB DDR400 RAM
Nvidia 7600GS 512MB

---

### Post by burwaco on 2006-11-26
root@box:/# glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
9084 frames in 5.0 seconds = 1816.743 FPS
9127 frames in 5.0 seconds = 1825.229 FPS
9126 frames in 5.0 seconds = 1825.199 FPS
9121 frames in 5.0 seconds = 1824.176 FPS
9127 frames in 5.0 seconds = 1825.391 FPS
9122 frames in 5.0 seconds = 1824.294 FPS
8740 frames in 5.0 seconds = 1747.921 FPS


Medion 95400 laptop
Pentium M 1,7 Ghz
512 Mb Ram
ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

What can I do to make this go faster ?

---

### Post by maxjivi05 on 2006-11-26
11135 frames in 5.0 seconds = 2226.944 FPS
15102 frames in 5.0 seconds = 3020.345 FPS
15074 frames in 5.0 seconds = 3014.663 FPS
15017 frames in 5.0 seconds = 3002.820 FPS
15064 frames in 5.0 seconds = 3012.649 FPS
15060 frames in 5.0 seconds = 3011.930 FPS

AMD XP 3200+ 2.6GHz
NVidia GeForce FX 5500 OC ( GPU: 310.500 / Mem: 472.500 ) 256MB Ram
1 Gig of Ram

Even with this junk score I still play Quake 4 no lag at smallest res but I have shadows and stuff to still make it look pretty :)

---

### Post by Bezmotivnik on 2006-11-27
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE/3DNOW!
OpenGL version string: 2.0.2 NVIDIA 87.62

19063 frames in 5.0 seconds = 3812.499 FPS
19070 frames in 5.0 seconds = 3813.885 FPS
19068 frames in 5.0 seconds = 3813.325 FPS

---

### Post by d351GuJu on 2006-11-29
65365 frames in 5.0 seconds = 13072.908 FPS
65849 frames in 5.0 seconds = 13169.771 FPS
65694 frames in 5.0 seconds = 13138.689 FPS
65742 frames in 5.0 seconds = 13148.400 FPS
65703 frames in 5.0 seconds = 13140.492 FPS
65519 frames in 5.0 seconds = 13103.660 FPS

;)

---

### Post by RavenThorn on 2006-12-02
102167 frames in 5.0 seconds = 20433.310 FPS
103103 frames in 5.0 seconds = 20620.546 FPS
103267 frames in 5.0 seconds = 20653.388 FPS
103125 frames in 5.0 seconds = 20624.942 FPS

---

### Post by zvezdogled on 2006-12-02
26009 frames in 5.0 seconds = 5184.582 FPS
27132 frames in 5.0 seconds = 5422.690 FPS
26237 frames in 5.0 seconds = 5232.771 FPS
25439 frames in 5.0 seconds = 5079.443 FPS
24527 frames in 5.0 seconds = 4898.363 FPS

centrino 1.7GHz
ATI Radeon mobility 9700

---

### Post by SingLee on 2006-12-03
The best I can do is 5317.254 FPS
It goes down when I use Beryl. I just install the 9626 driver.
Nice Logo :KS 

AMD Sempron 2800+
Nvidia 6600 AGP 128
1GB RAM

---

### Post by whatintheworldisthat on 2006-12-04
AMD64 3200+ Venice 2.2
512MB x 2 Corsair VS
Nvidia 6800GS

70532 frames in 5.0 seconds = 14106.374 FPS
85895 frames in 5.0 seconds = 17178.561 FPS
81936 frames in 5.0 seconds = 16387.158 FPS
83102 frames in 5.0 seconds = 16618.664 FPS
83649 frames in 5.0 seconds = 16729.385 FPS
83434 frames in 5.0 seconds = 16686.715 FPS
72108 frames in 5.0 seconds = 14420.238 FPS

---

### Post by Pathfinder_ on 2006-12-04
```
13705 frames in 5.0 seconds = 2740.883 FPS
13690 frames in 5.0 seconds = 2737.939 FPS
13703 frames in 5.0 seconds = 2740.409 FPS

```
celeron D 2.93@3.12GHz
1gig pc3200
Radeon 9000pro 64mb 

this is my fps with the default ati driver that comes with edgy + some xorg.conf tweaks. with the proprietary ati's driver i got 2400. for some reason i get more with the opesource driver. ;)

---

### Post by slicky on 2006-12-05
Radeon 9600 XT 256 mb
AMD64 @ 2009mhz
1024 ram

(using XGL)

~$ fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6011 (8.28.8)


~$ glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No


glxgears -iacknowledgethatthistoolisnotabenchmark 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
10392 frames in 5.0 seconds = 2074.553 FPS
17328 frames in 5.0 seconds = 3447.253 FPS
17821 frames in 5.0 seconds = 3563.918 FPS
16986 frames in 5.0 seconds = 3393.244 FPS
17345 frames in 5.0 seconds = 3463.689 FPS
17801 frames in 5.0 seconds = 3557.289 FPS


(using DRI)

~$ DISPLAY=:0 fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6011 (8.28.8)


~$ DISPLAY=:0 glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes


DISPLAY=:0 glxgears -iacknowledgethatthistoolisnotabenchmark 
1217 frames in 5.0 seconds = 243.245 FPS
1227 frames in 5.0 seconds = 245.380 FPS
1231 frames in 5.0 seconds = 246.178 FPS
1225 frames in 5.0 seconds = 244.977 FPS
1218 frames in 5.0 seconds = 243.583 FPS

---

### Post by testbenchdude on 2006-12-09
Here's something interesting.. glxgears on top with beryl running:

95257 frames in 5.0 seconds = 19051.396 FPS
90247 frames in 5.0 seconds = 18037.572 FPS
88743 frames in 5.0 seconds = 17728.541 FPS
88726 frames in 5.0 seconds = 17729.225 FPS
88971 frames in 5.0 seconds = 17773.426 FPS

glxgears minimized in beryl:

615842 frames in 5.0 seconds = **123165.461 FPS**
868138 frames in 5.0 seconds = **173627.562 FPS**
868590 frames in 5.0 seconds = **173718.000 FPS**
868383 frames in 5.0 seconds = **173673.578 FPS**
868614 frames in 5.0 seconds = **173720.672 FPS**


with Gnome Window Manager (beryl off):

27892 frames in 5.0 seconds = 5560.958 FPS
27949 frames in 5.0 seconds = 5587.767 FPS
27947 frames in 5.0 seconds = 5587.314 FPS
27947 frames in 5.0 seconds = 5583.875 FPS
27947 frames in 5.0 seconds = 5583.940 FPS

glxgears minimized (beryl off):

604290 frames in 5.0 seconds = **120858.000 FPS**
869690 frames in 5.0 seconds = **173937.969 FPS**
869328 frames in 5.0 seconds = **173863.641 FPS**
869408 frames in 5.0 seconds = **173874.234 FPS**
869633 frames in 5.0 seconds = **173926.594 FPS**


Would someone care to explain to me why this is so? **Six-digit FPS** seems sort of impossible...My apologies if it's already mentioned somewhere in this thread, I was too lazy to read all of it. :) Oh, and I'm running 2 7900GT's in SLI, C2D6600, 2gb 800MHz DDR2. Oh, and do I win? haha seriously, someone please explain this to me, I'm a noob with only about a week's worth of Ubuntu under my belt :)

---

### Post by kesman on 2006-12-11
> **Khannie said:**
> I averaged 4601 (excluding the first set)

System:
Athlon 2800+ @ 3200+
9800 pro (8.12.10 drivers)
768MB ram

Whoa! Are you using the official fglrx-driver or open source radeon?
I only get something around ~500fps with my x700, using fglrx :F

---

### Post by pickarooney on 2006-12-16
2571 frames in 5.0 seconds = 514.094 FPS
2858 frames in 5.0 seconds = 571.588 FPS
2784 frames in 5.0 seconds = 556.734 FPS

Athlon 64 3400+
GeForce 6200 TurboCache PCI-E
1GB RAM

Surely a contender for the worst performance possible for an nvidia config?

---

### Post by Dropbear on 2006-12-18
With beryl running...........

darren@Dropbear:~$ glxgears -printfps
32479 frames in 5.0 seconds = 6495.681 FPS
33365 frames in 5.0 seconds = 6672.866 FPS
33117 frames in 5.0 seconds = 6623.245 FPS
33426 frames in 5.0 seconds = 6685.107 FPS
33098 frames in 5.0 seconds = 6619.527 FPS
33189 frames in 5.0 seconds = 6637.363 FPS
33202 frames in 5.0 seconds = 6640.321 FPS
33211 frames in 5.0 seconds = 6642.159 FPS

Without beryl running...........

darren@Dropbear:~$ glxgears -printfps
50771 frames in 5.0 seconds = 10154.101 FPS
51905 frames in 5.0 seconds = 10380.888 FPS
51900 frames in 5.0 seconds = 10379.811 FPS
52006 frames in 5.0 seconds = 10401.069 FPS
51891 frames in 5.0 seconds = 10378.121 FPS
51980 frames in 5.0 seconds = 10395.853 FPS
51997 frames in 5.0 seconds = 10399.292 FPS
51916 frames in 5.0 seconds = 10383.129 FPS

You can see the performance hit from beryl (AIGLX)

Athlon 3800+ am2
1GB ddr2 ram 667mhz
Geforce 7600gt 256mb pcie 
200GB sata2 hd
1024x768 70hz 32bit colour

---

### Post by Dropbear on 2006-12-18
> **testbenchdude said:**
> Here's something interesting.. glxgears on top with beryl running:

95257 frames in 5.0 seconds = 19051.396 FPS
90247 frames in 5.0 seconds = 18037.572 FPS
88743 frames in 5.0 seconds = 17728.541 FPS
88726 frames in 5.0 seconds = 17729.225 FPS
88971 frames in 5.0 seconds = 17773.426 FPS

glxgears minimized in beryl:

615842 frames in 5.0 seconds = **123165.461 FPS**
868138 frames in 5.0 seconds = **173627.562 FPS**
868590 frames in 5.0 seconds = **173718.000 FPS**
868383 frames in 5.0 seconds = **173673.578 FPS**
868614 frames in 5.0 seconds = **173720.672 FPS**


with Gnome Window Manager (beryl off):

27892 frames in 5.0 seconds = 5560.958 FPS
27949 frames in 5.0 seconds = 5587.767 FPS
27947 frames in 5.0 seconds = 5587.314 FPS
27947 frames in 5.0 seconds = 5583.875 FPS
27947 frames in 5.0 seconds = 5583.940 FPS

glxgears minimized (beryl off):

604290 frames in 5.0 seconds = **120858.000 FPS**
869690 frames in 5.0 seconds = **173937.969 FPS**
869328 frames in 5.0 seconds = **173863.641 FPS**
869408 frames in 5.0 seconds = **173874.234 FPS**
869633 frames in 5.0 seconds = **173926.594 FPS**


Would someone care to explain to me why this is so? **Six-digit FPS** seems sort of impossible...My apologies if it's already mentioned somewhere in this thread, I was too lazy to read all of it. :) Oh, and I'm running 2 7900GT's in SLI, C2D6600, 2gb 800MHz DDR2. Oh, and do I win? haha seriously, someone please explain this to me, I'm a noob with only about a week's worth of Ubuntu under my belt :)

With those system specs it's very possible ;)

---

### Post by Takre on 2006-12-21
HP NX6110 laptop and Kubuntu 6.10..

3441 frames in 5.0 seconds = 688.157 FPS :o

Intel celeron m 1.4Ghz
512mb ram
intel GM915
1024x768
120Gb western-digital

---

### Post by jhenager on 2006-12-21
jeff@jeff-desktop:~$ glxgears -printfps
6916 frames in 5.0 seconds = 1382.224 FPS
6115 frames in 5.0 seconds = 1222.879 FPS
6187 frames in 5.0 seconds = 1237.213 FPS
6186 frames in 5.0 seconds = 1237.124 FPS
6186 frames in 5.0 seconds = 1237.094 FPS
6185 frames in 5.0 seconds = 1236.898 FPS
6187 frames in 5.0 seconds = 1237.247 FPS
6186 frames in 5.0 seconds = 1237.060 FPS
6185 frames in 5.0 seconds = 1236.985 FPS

---

### Post by blitzer on 2006-12-25
glxgears -printfps
5688 frames in 5.0 seconds = 1137.598 FPS
5702 frames in 5.0 seconds = 1140.240 FPS
5703 frames in 5.0 seconds = 1140.484 FPS
5702 frames in 5.0 seconds = 1140.285 FPS
5618 frames in 5.0 seconds = 1123.549 FPS
5223 frames in 5.0 seconds = 1044.528 FPS

fgl_glxgears
Using GLX_SGIX_pbuffer
598 frames in 5.0 seconds = 119.600 FPS
769 frames in 5.0 seconds = 153.800 FPS
786 frames in 5.0 seconds = 157.200 FPS
769 frames in 5.0 seconds = 153.800 FPS
794 frames in 5.0 seconds = 158.800 FPS
766 frames in 5.0 seconds = 153.200 FPS
770 frames in 5.0 seconds = 154.000 FPS

:mrgreen: 
 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

---

### Post by Lystrodom on 2006-12-25
4680 frames in 5.0 seconds = 935.623 FPS
4517 frames in 5.0 seconds = 903.363 FPS
4537 frames in 5.0 seconds = 907.372 FPS
4634 frames in 5.0 seconds = 926.765 FPS
4815 frames in 5.0 seconds = 962.962 FPS


I must be doing something wrong... I've got an AMD 64 X2 4200+, Geforce 7950GX2, 1 gig of Corsair RAM, and a 250 gig SATA drive...

---

### Post by patrick295767 on 2006-12-25
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes


I beat you guys with my high-tech     ATI   ALL IN WONDER Rage 128   double core !! 

```
MESA_window_pos GL_NV_texgen_reflection GL_SGI_color_matrix GL_SGI_color_table
1790 frames in 5.0 seconds = 358.000 FPS
2008 frames in 5.0 seconds = 401.600 FPS
2289 frames in 5.0 seconds = 457.800 FPS
2289 frames in 5.0 seconds = 457.800 FPS
2288 frames in 5.0 seconds = 457.600 FPS
2289 frames in 5.0 seconds = 457.800 FPS
2288 frames in 5.0 seconds = 457.600 FPS
2289 frames in 5.0 seconds = 457.800 FPS
```



debian, xorg 
~$ glxgears -printfps
1858 frames in 5.0 seconds = 371.490 FPS
1856 frames in 5.0 seconds = 371.130 FPS
1855 frames in 5.0 seconds = 370.870 FPS
1858 frames in 5.0 seconds = 371.458 FPS
1855 frames in 5.0 seconds = 370.920 FPS
1855 frames in 5.0 seconds = 370.956 FPS
1857 frames in 5.0 seconds = 371.218 FPS
1860 frames in 5.0 seconds = 371.950 FPS
1843 frames in 5.0 seconds = 368.412 FPS




lol   :D :D

---

### Post by Slammer64 on 2006-12-25
Here's my addition to this merry band of lunatics :p 

user@HAL-9000:~$ glxgears -printfps
59527 frames in 5.0 seconds = 11905.325 FPS
72827 frames in 5.0 seconds = 14565.359 FPS
72733 frames in 5.0 seconds = 14546.460 FPS
72811 frames in 5.0 seconds = 14562.128 FPS
72819 frames in 5.0 seconds = 14563.741 FPS
72828 frames in 5.0 seconds = 14565.530 FPS

System: Athlon X2 3800+
nVidia 6800 Ultra/256 meg RAM
MSI K9NU-Neo V Mobo
Patriot Ram:2 Gig DDR2 800
200 Gig Sata 2

---

### Post by tmrafi on 2006-12-25
One more benchmark for the lunatics :cool: 
Without Beryl
~$ glxgears -printfps
78954 frames in 5.0 seconds = 15790.756 FPS
78930 frames in 5.0 seconds = 15785.851 FPS
78954 frames in 5.0 seconds = 15790.624 FPS
78926 frames in 5.0 seconds = 15785.020 FPS
78929 frames in 5.0 seconds = 15785.624 FPS

System : Intel Core2Duo 6600
nVidia 7900 GS / 256MB DDR3 RAM
ASUS P5B Mobo
Corsair XMS2 1GB RAM (PC6400)
250 GB SATA2 3Gbps HDD

---

### Post by Vord on 2006-12-26
Damn you!

vord@vord-desktop:~$ glxgears -printfps
64188 frames in 5.0 seconds = 12837.595 FPS
71213 frames in 5.0 seconds = 14242.499 FPS
71837 frames in 5.0 seconds = 14367.235 FPS
70804 frames in 5.0 seconds = 14160.710 FPS

I was hoping I'd have the high score :P

---

### Post by Lystrodom on 2006-12-26
So, without Beryl running I wasn't breaking 1k FPS.

With beryl running: 
20436 frames in 5.0 seconds = 4087.160 FPS
19430 frames in 5.0 seconds = 3885.962 FPS
15749 frames in 5.0 seconds = 3149.581 FPS
19151 frames in 5.0 seconds = 3830.055 FPS
19119 frames in 5.0 seconds = 3823.666 FPS


And then minimized with Beryl running:
80924 frames in 5.0 seconds = 16184.797 FPS
82930 frames in 5.0 seconds = 16586.000 FPS
83711 frames in 5.0 seconds = 16742.082 FPS
83886 frames in 5.0 seconds = 16777.119 FPS
82696 frames in 5.0 seconds = 16528.326 FPS


So beryl makes my system run faster? I've got an AMD 64 X2 4200+, Nvidia Geforce 7950GX2,  1 GB Corsair RAM, 250 GB SATA 3.0Gbps HDD.

---

### Post by kEinstein on 2007-01-04
Let's continue the funny thread that reminds of my childhood! Whether it was size, thickness, money or something else, I never won... and I wont win this time :rolleyes:  simply due to the fact that glxgears is not a benchmark tool. Therefore its results are not comparable... ](*,) however, 

I'm running Edgy on a Dual-Head System:
T43 @ 1866 MHz, 1024 MB RAM, 60GB 7200rpm, ATi X300
3D support is enabled on both monitors, internal SXGA+ (1400x1050), external WSXGA+ (1680x1050) using fglrx v.8.28

```
swank@myThinkPad:~$ glxgears **-iacknowledgethatthistoolisnotabenchmark**
1253 frames in 5.0 seconds = 250.453 FPS
1249 frames in 5.0 seconds = 249.784 FPS
1249 frames in 5.0 seconds = 249.786 FPS
1250 frames in 5.0 seconds = 249.985 FPS
1249 frames in 5.0 seconds = 249.785 FPS
1222 frames in 5.0 seconds = 244.384 FPS
1249 frames in 5.0 seconds = 249.784 FPS
1249 frames in 5.0 seconds = 249.785 FPS
```

---

### Post by EdThaSlayer on 2007-01-04
I have a:
 P4 3.0 GHZ with 2 mb l2 cache
1024 mb ddr2 ram
ATI Radeon 9600(128 mb of vram, I think that the clockspeed of my graphics card is 400 mhz)

I'm running Edgy Eft(the reason its so slow) with the version of fgrlx that you can get via apt-get
```

1251 frames in 5.0 seconds = 250.029 FPS
1251 frames in 5.0 seconds = 250.185 FPS
1249 frames in 5.0 seconds = 249.783 FPS
1250 frames in 5.0 seconds = 249.986 FPS
1249 frames in 5.0 seconds = 249.785 FPS
1250 frames in 5.0 seconds = 249.984 FPS
1249 frames in 5.0 seconds = 249.784 FPS
1250 frames in 5.0 seconds = 249.981 FPS
1248 frames in 5.0 seconds = 249.588 FPS

```

---

### Post by kEinstein on 2007-01-04
Interestingly EdThaSlayer and I achieve comparable results:
Is it the fact that both graphic cards build on the same chip?
X300 and 9600 - didn't expect identical values in FPS on two different machines...

---

### Post by mpeixoto on 2007-01-08
1200 fps

intel p4 2.8Ghz
1GbRAM
ati9200se
Ubuntu Edgy

---

### Post by RoLanRok on 2007-01-08
This is run in Gnome with the latest Nvidia drivers (Geforce 1.0-9746 AMD64) with no performance tweaks.

```
xxx@xxx-desktop:~$ glxgears -printfps
52471 frames in 5.0 seconds = 10494.034 FPS
54346 frames in 5.0 seconds = 10869.148 FPS
54336 frames in 5.0 seconds = 10867.129 FPS
54329 frames in 5.0 seconds = 10865.646 FPS
54348 frames in 5.0 seconds = 10869.435 FPS
54353 frames in 5.0 seconds = 10870.590 FPS
54346 frames in 5.0 seconds = 10869.121 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

```

Comp Specs:
1024x768 32
AMD Sempron 3200+
768MB PC-3200 RAM
BFG Geforce 7600 GT
Regular IDE HDD

Before I upgraded to the latest driver, my FPS was about half that.

---

### Post by pross on 2007-01-08
> **tmrafi said:**
> 
System : Intel Core2Duo 6600
nVidia 7900 GS / 256MB DDR3 RAM
ASUS P5B Mobo
Corsair XMS2 1GB RAM (PC6400)
250 GB SATA2 3Gbps HDD

Same GFX card ;) 
Same RAM !
Athlon 64 X2 3800

Beryl..
pross@pross-desktop:~$ glxgears -printfps
46923 frames in 5.0 seconds = 9384.554 FPS
47455 frames in 5.0 seconds = 9490.863 FPS
46897 frames in 5.0 seconds = 9379.285 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
No Beryl..
pross@pross-desktop:~$ glxgears -printfps
72078 frames in 5.0 seconds = 14415.562 FPS
75635 frames in 5.0 seconds = 15126.897 FPS
75748 frames in 5.0 seconds = 15149.467 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

---

### Post by Muppeteer on 2007-01-09
```
68384 frames in 5.0 seconds = 13676.651 FPS
73788 frames in 5.0 seconds = 14757.524 FPS
73841 frames in 5.0 seconds = 14768.031 FPS
72168 frames in 5.0 seconds = 14433.450 FPS
73744 frames in 5.0 seconds = 14748.649 FPS
73789 frames in 5.0 seconds = 14757.800 FPS
73190 frames in 5.0 seconds = 14637.965 FPS

```

My hardware 
AMD 64 3700+
Leadtek 7800 GTX
Corsair XMS 2x 512MB @ 2-3-6-6
Asus A8N SLi Premium
Audigy 2 ZS

Funny enough i was getting 12000+ with my ATI X800 XT, but it was soo crap when trying to play WoW...:(

---

### Post by 2Loose on 2007-01-11
Got the new ATI 8.33.6 drivers working with my X1950PRO now

AMD64 3000 Venice (1.8GHz)
1Gb RAM
ASrock DUAL SATAII 939 Mobo

57546 frames in 5.0 seconds = 11509.131 FPS
57630 frames in 5.0 seconds = 11525.874 FPS

---

### Post by Enverex on 2007-01-11
~19,000 Fps

---

### Post by Cimmerian on 2007-01-13
Specs:

8800 GTX
Core 2 6700
2GB ram
nForce 680i mobo

Result:

106886 frames in 5.0 seconds = 21377.152 FPS
107013 frames in 5.0 seconds = 21402.588 FPS
106843 frames in 5.0 seconds = 21368.441 FPS
106866 frames in 5.0 seconds = 21373.068 FPS

---

### Post by EdThaSlayer on 2007-01-13
I have a:
P4 3.0 GHZ with 2 mb l2 cache
1024 mb ddr2 ram
ATI Radeon 9600(128 mb of vram, I think that the clockspeed of my graphics card is 400 mhz)

Ever since I changed back to Dapper Drake things have gone faster...but not as fast as I expected it to be...(my small 4 year olds brothers "hand me down" 1.5 ghz pentium 4 with 256 mb of ram and a old dusty geforce 2 card can do up to 1000 fps)
> 
7134 frames in 5.0 seconds = 1426.348 FPS
6983 frames in 5.0 seconds = 1396.593 FPS
7129 frames in 5.0 seconds = 1425.651 FPS
6967 frames in 5.0 seconds = 1393.241 FPS
6973 frames in 5.0 seconds = 1394.559 FPS
7041 frames in 5.0 seconds = 1408.192 FPS


---

### Post by sitheris on 2007-01-14
72510 frames in 5.0 seconds = 14501.978 FPS
72526 frames in 5.0 seconds = 14505.081 FPS
72588 frames in 5.0 seconds = 14517.464 FPS
72196 frames in 5.0 seconds = 14439.016 FPS
92149 frames in 5.0 seconds = 18429.656 FPS

AMD X2 4400
2gb DDR400
XFX 7800gt

:-D

---

### Post by M_the_C on 2007-01-14
Around 1552.092 FPS.

AMD Athlon 2800XP
512MB RAM
nVidia 6200 AGP

Why when I switch to another Virtual Desktop does it reach 3000 FPS.
It still has to work it out doesn't it?

---

### Post by myname on 2007-01-14
I must have something configured incorrectly, and any help would be greatly appreciated.

my specs: 
AMD 64 3700+
2 ghz memory
ATI X1600 w/512 megs Ram

And the results of my glxgears -printfps is the following:

~$ glxgears -printfps
1870 frames in 5.0 seconds = 373.708 FPS
2653 frames in 5.0 seconds = 530.580 FPS
2424 frames in 5.0 seconds = 484.782 FPS
2008 frames in 5.0 seconds = 401.585 FPS
1966 frames in 5.0 seconds = 393.185 FPS
1930 frames in 5.0 seconds = 385.986 FPS
1979 frames in 5.0 seconds = 395.785 FPS
2014 frames in 5.0 seconds = 402.785 FPS
2000 frames in 5.0 seconds = 399.985 FPS
1991 frames in 5.0 seconds = 398.185 FPS
1985 frames in 5.0 seconds = 396.985 FPS
1984 frames in 5.0 seconds = 396.784 FPS

Any idea why other people with ATI cards are getting over 1000 FPS with glxgears?

Here is the output from fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6119 (8.30.3)

I also notice that when I go to Digg ([www.digg.com)](www.digg.com)), and use my mouse scrollwheel to scroll down the page, I can see the page redrawn as it's scrolling.  this does not happen on my work machine, or a friends machine that have nvidia cards.  Anyway to get  my ATI card to have similar performance?

--kevin

---

### Post by kcakalinuxnub on 2007-01-14
> 26885 frames in 5.0 seconds = 5376.755 FPS
15002 frames in 5.0 seconds = 3000.204 FPS
12992 frames in 5.0 seconds = 2598.290 FPS
12957 frames in 5.0 seconds = 2591.330 FPS
12973 frames in 5.0 seconds = 2594.439 FPS
13010 frames in 5.0 seconds = 2601.923 FPS
12965 frames in 5.0 seconds = 2592.923 FPS


P4 2.6 Ghz 1GB SDDR RAM
Nvidia Geforce FX5200

---

### Post by M_the_C on 2007-01-14
> **myname said:**
> I must have something configured incorrectly, and any help would be greatly appreciated.

I also notice that when I go to Digg ([www.digg.com)](www.digg.com)), and use my mouse scrollwheel to scroll down the page, I can see the page redrawn as it's scrolling.  this does not happen on my work machine, or a friends machine that have nvidia cards.  Anyway to get  my ATI card to have similar performance?

--kevin
Do you have the official ATI drivers installed?
Are you running Compiz or Beryl.

I have heard any of these slows graphics capabilities.

---

### Post by myname on 2007-01-14
I do have the official ATI drivers installed, and as far as I know, I don't have beryl or compiz running.  I am running Edgy.

is there a proper way to install the latest ATI drivers?  I tried to uninstall the drivers and install the latest release, and now my system locks when booting up.  I don't get to the login screen.

zoinks, and I haven't backed up in a while.

--Kevin

---

### Post by lagtastic on 2007-01-14
> **Cimmerian said:**
> Specs:

8800 GTX
Core 2 6700
2GB ram
nForce 680i mobo

Result:

106886 frames in 5.0 seconds = 21377.152 FPS
107013 frames in 5.0 seconds = 21402.588 FPS
106843 frames in 5.0 seconds = 21368.441 FPS
106866 frames in 5.0 seconds = 21373.068 FPS

wow, that new 8800 does shine, comes pretty close to my 3d workstation with a quadro 4500 ...

120928 frames in 5.0 seconds = 24185.557 FPS
121811 frames in 5.0 seconds = 24362.049 FPS
115137 frames in 5.0 seconds = 23027.281 FPS
115500 frames in 5.0 seconds = 23099.885 FPS
115373 frames in 5.0 seconds = 23074.582 FPS
115152 frames in 5.0 seconds = 23030.264 FPS
115404 frames in 5.0 seconds = 23080.656 FPS
115417 frames in 5.0 seconds = 23083.354 FPS
115334 frames in 5.0 seconds = 23066.777 FPS
115181 frames in 5.0 seconds = 23036.002 FPS

cheerios

---

### Post by mkw87 on 2007-01-14
53218 frames in 5.0 seconds = 10643.503 FPS
54782 frames in 5.0 seconds = 10956.276 FPS
54674 frames in 5.0 seconds = 10934.627 FPS
54547 frames in 5.0 seconds = 10909.364 FPS
50531 frames in 5.0 seconds = 10106.065 FPS

eVGA 7600gt with my Opty 165

---

### Post by emarkay on 2007-01-19
Dell Optiplex GX110
Intel Pentium III 733 MHz
384Mb RAM
Onboard Intel(r) 82810E Graphics Controller:

998 frames in 8.4 seconds = 118.283 FPS
1311 frames in 9.8 seconds = 134.396 FPS
1312 frames in 9.4 seconds = 139.105 FPS
656 frames in 5.1 seconds = 127.389 FPS
1312 frames in 20.5 seconds = 63.972 FPS
656 frames in 19.7 seconds = 33.274 FPS
656 frames in 5.4 seconds = 120.652 FPS
656 frames in 6.6 seconds = 99.224 FPS
656 frames in 15.5 seconds = 42.246 FPS
656 frames in 8.2 seconds = 80.213 FPS
656 frames in 8.8 seconds = 74.186 FPS

---

### Post by Cimmerian on 2007-01-20
Here's what happened after a bios update:

Running @1600x1200

crom@cimmeria:~$ glxgears -printfps
142542 frames in 5.0 seconds = 28508.264 FPS
142685 frames in 5.0 seconds = 28536.924 FPS
142585 frames in 5.0 seconds = 28516.963 FPS
142800 frames in 5.0 seconds = 28559.863 FPS
142812 frames in 5.0 seconds = 28562.236 FPS
142710 frames in 5.0 seconds = 28541.938 FPS
crom@cimmeria:~$ 

I think I will have to do some overclocking and see if I can't hit 30k =)

Some compositing settings are enabled which may also affect performance...

---

### Post by rolando2424 on 2007-01-20
I even feel ashamed...

> rolando@rolando-desktop:~$ glxgears -printfps
1252 frames in 5.0 seconds = 250.267 FPS
1254 frames in 5.0 seconds = 250.784 FPS
1256 frames in 5.0 seconds = 251.180 FPS
1251 frames in 5.0 seconds = 250.190 FPS


Intel Pentium 4 2.8 Ghz
512 Mb Ram
and a Nvidia GeForce MX 400 :(

](*,)

EDIT: Ubuntu Edgy Eft, in 1024x768

---

### Post by xxrealmsxx on 2007-01-22
Hp pavillion zv6000
AMD64 3200+ w/ 512mb of ram
ati Radeon 128mb dedicated video ram

realms@realms-laptop:~$ glxgears -printfps
7852 frames in 5.0 seconds = 1568.134 FPS
8937 frames in 5.0 seconds = 1787.385 FPS
10481 frames in 5.0 seconds = 2096.187 FPS
10206 frames in 5.0 seconds = 2041.186 FPS
10514 frames in 5.0 seconds = 2102.664 FPS
10128 frames in 5.0 seconds = 2025.432 FPS
10581 frames in 5.0 seconds = 2116.087 FPS
10830 frames in 5.0 seconds = 2165.829 FPS
10634 frames in 5.0 seconds = 2126.766 FPS
10339 frames in 5.0 seconds = 2067.632 FPS
10624 frames in 5.0 seconds = 2124.674 FPS
10389 frames in 5.0 seconds = 2077.712 FPS
10453 frames in 5.0 seconds = 2090.479 FPS
10933 frames in 5.0 seconds = 2186.541 FPS
10753 frames in 5.0 seconds = 2150.576 FPS
10873 frames in 5.0 seconds = 2174.501 FPS
10572 frames in 5.0 seconds = 2114.354 FPS
10386 frames in 5.0 seconds = 2077.114 FPS
10461 frames in 5.0 seconds = 2092.110 FPS
10278 frames in 5.0 seconds = 2055.457 FPS
10630 frames in 5.0 seconds = 2125.974 FPS
10338 frames in 5.0 seconds = 2067.464 FPS
10533 frames in 5.0 seconds = 2106.532 FPS
10762 frames in 5.0 seconds = 2152.238 FPS
10412 frames in 5.0 seconds = 2082.247 FPS
11985 frames in 5.0 seconds = 2396.913 FPS
15085 frames in 5.0 seconds = 3016.906 FPS
14917 frames in 5.0 seconds = 2983.238 FPS
14616 frames in 5.0 seconds = 2923.055 FPS
14707 frames in 5.0 seconds = 2941.388 FPS
14356 frames in 5.0 seconds = 2871.138 FPS
14166 frames in 5.0 seconds = 2833.152 FPS
14536 frames in 5.0 seconds = 2907.108 FPS
15225 frames in 5.0 seconds = 3044.914 FPS

and i still can't play unreal :(.

---

### Post by bluehue on 2007-01-26
Intel 3.2c
1GB Ram
Evga 6800 Ultra

```

spiral@spiral-desktop:~$ glxgears -printfps
71683 frames in 5.0 seconds = 14336.598 FPS
71485 frames in 5.0 seconds = 14296.914 FPS
71914 frames in 5.0 seconds = 14382.800 FPS
71912 frames in 5.0 seconds = 14382.308 FPS
71925 frames in 5.0 seconds = 14384.845 FPS
71901 frames in 5.0 seconds = 14380.019 FPS

```

---

### Post by wesley_of_course on 2007-02-17
Wesley here ;


wesley@Ratdog:~$ glxgears -printfps

82903 frames in 5.0 seconds = 16580.588 FPS
92148 frames in 5.0 seconds = 18429.506 FPS
92135 frames in 5.0 seconds = 18426.975 FPS
92159 frames in 5.0 seconds = 18431.775 FPS
92138 frames in 5.0 seconds = 18427.406 FPS
92177 frames in 5.0 seconds = 18435.301 FPS
92160 frames in 5.0 seconds = 18431.824 FPS
92169 frames in 5.0 seconds = 18433.701 FPS
92154 frames in 5.0 seconds = 18430.627 FPS
92168 frames in 5.0 seconds = 18433.549 FPS
92140 frames in 5.0 seconds = 18427.975 FPS
92172 frames in 5.0 seconds = 18434.248 FPS

  Windows minimized  EVGA  eGeForce 7600 GT 256MB
   INTEL Core 2 Duo E6600
 ASUS  P5N-E SLI
Corsair DDR800 TWIN 2X 512 MATCHED

   A fresh install probably helped more than I'll ever know at this point in time.

:popcorn:

---

### Post by duaneb on 2007-02-17
I'm only gettin ~2000 with my 7300 GS... what's wrong? :?

---

