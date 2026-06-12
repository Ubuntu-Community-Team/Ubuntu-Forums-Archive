---
title: "CPU benchmark - how many GFLOPs does your multicore machine do?"
date: 2008-12-07
forum: Gaming &amp; Leisure
---

### Post by graysky on 2008-12-07
The primary goal of the Linpack benchmark is to measure Gigaflops of PCs or PC clusters.  It has been used for Super-Computers, but also desktop machines.  The software solves mathematical problem - arbitrary large set of linear equations, and displays the rate of solving, measured in Gigaflops (Floating Point Operations per Second).

It is very efficient at using multi-core processors.  Here is a screen-shot of my conky during the test run:

[img]http://img243.imageshack.us/img243/117/15978852cs4.gif[/img]

You can download it from Intel's page: [Linpack download link](http://www.intel.com/cd/software/products/asmo-na/eng/363184.htm).  

Installation is trivial:
```
$ cd Downloads
$ tar zxvf l_lpk_p_10.1.0.002.tgz
```

Before you run it, you need to know how much physical memory you have and enter the appropriate values into the software for it's problem sizes and leading dimensions variables.  These tell it how much memory to use.

Here is a rough guide:

[b]1 gig of physical memory = 7000
2 gig of physical memory = 13700
4 gig of physical memory = 20000
8 gig of physical memory = 30000[/b]

If you're running the amd64 LINUX, use the 'xlinpack_xeon64' executable.  If you're running the standard i686 or below LINUX, use the 'xlinpack_xeon32' executable.

```
$ cd linpack_10.1.0/benchmarks/linpack/
$ ./xlinpack_xeon64
```

Now you'll see:

```
Input data or print help ? Type [data]/help :
```

Simply hit the <ENTER> key and enter the value you found from the table above.  My system has 4 gigs, so I'll use '20000' for the first two questions, and '4' for the last two questions.

```
Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 20000
Leading dimension of array: 20000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Sun Dec 14 19:00:27 2008

CPU frequency:    3.400 GHz
Number of CPUs: 4
Number of threads: 4

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      111.673    47.7658  4.546476e-10 4.024627e-02
20000  20000  4      111.306    47.9233  4.546476e-10 4.024627e-02
20000  20000  4      111.339    47.9091  4.546476e-10 4.024627e-02
20000  20000  4      111.733    47.7400  4.546476e-10 4.024627e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       47.8345  47.9233 

End of tests
```

My CPU is an X3360 @ 8.5x400=3.40 GHz by the way.

Please post your results!

---

### Post by eragon100 on 2008-12-07
My intel core 2 duo e6300 @ 1.86 GHZ:

ichigo-soul-reaper@soul-society:~/Desktop/linpack_10.1.0/benchmarks/linpack$ ./xlinpack_xeon64
Input data or print help ? Type [data]/help :
data
Number of equations to solve (problem size): 18500
Leading dimension of array: 18500
Number of trials to run: 1
Data alignment value (in Kbytes): 4
Current date/time: Sun Dec  7 14:00:58 2008

CPU frequency:    1.862 GHz
Number of CPUs: 2
Number of threads: 2

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 18500
Leading dimension of array                  : 18500
Number of trials to run                     : 1    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 2738374096, at the size = 18500

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
18500  18500  4      475.641    8.8760   3.158189e-10 3.270656e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
18500  18500  4       8.8760   8.8760  

End of tests


Well, ubuntu runs *extremely* fast on this PC, so I'
m happy :popcorn:

---

### Post by Funnnny on 2008-12-07
Mine is T8300 2x2.4G
> CPU frequency:    2.394 GHz
Number of CPUs: 2
Number of threads: 2

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 13700
Leading dimension of array                  : 13700
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 1501798096, at the size = 13700

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
13700  13700  4      167.233    10.2528  1.865160e-10 3.518248e-02
13700  13700  4      124.721    13.7475  1.865160e-10 3.518248e-02
13700  13700  4      126.239    13.5823  1.865160e-10 3.518248e-02
13700  13700  4      119.224    14.3814  1.865160e-10 3.518248e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
13700  13700  4       12.9910  14.3814 

End of tests


---

### Post by Mr.Carramba on 2009-02-18
This was so much fun :)
Thank you for posting link and info!


> 
CPU frequency:    2.327 GHz
Number of CPUs: 8
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 30000
Leading dimension of array                  : 30000
Number of trials to run                     : 4
Data alignment value (in Kbytes)            : 4

Maximum memory requested that can be used = 7200604096, at the size = 30000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
30000  30000  4      303.953    59.2257  7.597450e-10 2.994923e-02
30000  30000  4      303.596    59.2952  7.597450e-10 2.994923e-02
30000  30000  4      303.480    59.3179  7.597450e-10 2.994923e-02
30000  30000  4      303.716    59.2718  7.597450e-10 2.994923e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
30000  30000  4       59.2776  59.3179

End of tests


---

### Post by VladTepes on 2009-06-17
Do we have similar test suites for AMD x86_64 machines too? The software package I found on Netlib takes ages to 'make' on my machine, and then hangs it.

-Vlad

---

### Post by wapko on 2009-07-09
i looked everywhere for a gigaflops benchmark. then i found this thread.. was fooling with hpl and stuff..

intel q9550 goodness :D

```
CPU frequency:    3.604 GHz
Number of CPUs: 4
Number of threads: 4

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      106.650    50.0153  3.498382e-10 3.096834e-02
20000  20000  4      106.519    50.0769  3.498382e-10 3.096834e-02
20000  20000  4      106.199    50.2279  3.498382e-10 3.096834e-02
20000  20000  4      106.996    49.8535  3.498382e-10 3.096834e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       50.0434  50.2279 

End of tests
```


would like to see an OC i7 do this test..

---

### Post by Waly_Br on 2009-10-16
xlinpack_xeon32Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 20000    
Leading dimension of array: 20000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Fri Oct 16 18:35:18 2009

CPU frequency:    2.261 GHz
Number of CPUs: 2
Number of threads: 2

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      343.637    15.5226  3.560856e-10 3.152138e-02
20000  20000  4      355.292    15.0134  3.560856e-10 3.152138e-02
20000  20000  4      342.751    15.5627  3.560856e-10 3.152138e-02
20000  20000  4      344.322    15.4917  3.560856e-10 3.152138e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       15.3976  15.5627 

End of tests
My laptop =)

---

### Post by Sealbhach on 2009-10-16
Memory 2GB
2 x Intel Core2 Duo T7250 @2.00 GHz

```
Number of equations to solve (problem size): 13700
Leading dimension of array: 13700
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Sat Oct 17 01:08:55 2009

CPU frequency:    1.995 GHz
Number of CPUs: 2
Number of threads: 2

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 13700
Leading dimension of array                  : 13700
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 1501798096, at the size = 13700

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
13700  13700  4      176.729    9.7019   1.865160e-10 3.518248e-02
13700  13700  4      184.014    9.3178   1.865160e-10 3.518248e-02
13700  13700  4      192.283    8.9171   1.865160e-10 3.518248e-02
13700  13700  4      198.220    8.6500   1.865160e-10 3.518248e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
13700  13700  4       9.1467   9.7019  

End of tests
```

---

### Post by dalesd on 2009-10-18
34.2 GFlops!  Woo!
Intel Q9300 Quad Core @ 2.5 GHz.

```

CPU frequency:    2.505 GHz
Number of CPUs: 4
Number of threads: 4

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20016  4      156.735    34.0329  3.625560e-10 3.209415e-02
20000  20016  4      156.792    34.0205  3.625560e-10 3.209415e-02
20000  20016  4      155.871    34.2214  3.625560e-10 3.209415e-02
20000  20016  4      155.858    34.2243  3.625560e-10 3.209415e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20016  4       34.1248  34.2243
```

---

### Post by calc on 2009-10-20
> **Mr.Carramba said:**
> This was so much fun :)
Thank you for posting link and info!

What kind of cpu do you have? It appears to be extremely fast, is it a Core i7 Bloomfield?

---

### Post by calc on 2009-10-20
System specs:

Intel Core i7 860 2.80 GHz (Lynnfield) oc to 169x21 3.549GHz
8GB DDR3 memory running at 1690 MHz cas 7

```
Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 30000
Leading dimension of array: 30000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Tue Oct 20 20:08:14 2009

CPU frequency:    3.549 GHz
Number of CPUs: 8
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 30000
Leading dimension of array                  : 30000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 7200604096, at the size = 30000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
30000  30000  4      341.007    52.7902  8.446834e-10 3.329751e-02
30000  30000  4      340.978    52.7946  8.446834e-10 3.329751e-02
30000  30000  4      340.978    52.7945  8.446834e-10 3.329751e-02
30000  30000  4      340.987    52.7932  8.446834e-10 3.329751e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
30000  30000  4       52.7931  52.7946

End of tests
```

Note that linpack gives much higher GFlops numbers under Linux than under Windows 7. The highest I got under Windows 7 was 46.74 which was ~ 13% slower than under Linux. Also I noticed that when stability testing under Windows 7 I found the voltage needed for it, which was stable for over 10 hours of linpack, but since it apparently wasn't stressing the CPU nearly as much the same voltage under Linux caused the system to immediately reboot when I ran linpack. I upped the Vtt core voltage another 0.020 and it became stable under Linux as well.

Also note that for Lynnfield the maximum safe Vtt voltage is 1.21 so that is why I limited my overclock to only 3.549 GHz as that was the highest I could go keeping the Vtt voltage within the guidelines in the chip documentation. The socket 1156 motherboards, at least my Gigabyte GA-P55-UD5, apparently still only show the limits based on Bloomfield which was 1.35 volts so be careful if you overclock a Lynnfield processor.

---

### Post by Bachstelze on 2009-10-20
Bow before my Celeron 220!

```

firas@iori linpack % ./xlinpack_xeon64
Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 13700
Leading dimension of array: 13700
Number of trials to run: 2
Data alignment value (in Kbytes): 2
Current date/time: Wed Oct 21 04:51:38 2009

CPU frequency:    1.200 GHz
Number of CPUs: 1
Number of threads: 1

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 13700
Leading dimension of array                  : 13700
Number of trials to run                     : 2
Data alignment value (in Kbytes)            : 2

Maximum memory requested that can be used = 1501796048, at the size = 13700

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
13700  13700  2      764.291    2.2434   1.921471e-10 3.624467e-02
13700  13700  2      883.600    1.9405   1.921471e-10 3.624467e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
13700  13700  2       2.0919   2.2434

End of tests
```

---

### Post by canduc17 on 2009-10-22
Great tool!
Do you know another one to obtain the bandwidth between CPU and main memory in Byte/seconds? I'm going crazy serching for it!
Thank you.

---

### Post by wapko on 2009-11-06
So i got a dualcore atom 330 board, the intel D945GCLF2D

this i my results. will be a nice little nas box when im done setting it up.
```

Number of equations to solve (problem size): 7000
Leading dimension of array: 7000
Number of trials to run: 2
Data alignment value (in Kbytes): 2
Current date/time: Fri Nov  6 09:02:00 2009

CPU frequency:    1.596 GHz
Number of CPUs: 4
Number of threads: 4

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 7000
Leading dimension of array                  : 7000
Number of trials to run                     : 2
Data alignment value (in Kbytes)            : 2

Maximum memory requested that can be used = 392142048, at the size = 7000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
7000   7000   2      310.644    0.7364   5.086720e-11 3.650045e-02
7000   7000   2      310.633    0.7364   5.086720e-11 3.650045e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
7000   7000   2       0.7364   0.7364

End of tests 

```

disabling HT gives an avg. of 0.771

---

### Post by drphilngood on 2009-11-18
i7 Lynnfield 870 on 64-bit Jaunty [Average 58.6443, Maximal 58.6537
[ATTACH]142856[/ATTACH]

---

### Post by Uppsala9496 on 2009-12-04
Any way of getting Linpack to work on an AMD cpu?  Version 10.2 from intel won't allow it to run on an AMD chip.

---

### Post by w0mbatharcos on 2010-02-24
Specs:
2 x Xeon X5365
16 GB FB-Dimm DDR2 RAM

```
w0mbatharcos@w0mbatharcos-desktop:~/Letöltések/linpack_10.2.3/benchmarks/linpack
$ ./xlinpack_xeon64
Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 40000
Leading dimension of array: 40000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Wed Feb 24 17:43:18 2010

CPU frequency:    2.992 GHz
Number of CPUs: 8
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 40000
Leading dimension of array                  : 40000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 12800804096, at the size = 40000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
40000  40000  4      729.120    58.5224  1.435151e-09 3.191825e-02
40000  40000  4      721.039    59.1783  1.435151e-09 3.191825e-02
40000  40000  4      724.087    58.9292  1.435151e-09 3.191825e-02
40000  40000  4      726.529    58.7311  1.435151e-09 3.191825e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
40000  40000  4       58.8402  59.1783 

End of tests

```

---

### Post by calc on 2010-04-17
> **drphilngood said:**
> i7 Lynnfield 870 on 64-bit Jaunty [Average 58.6443, Maximal 58.6537
[ATTACH]142856[/ATTACH]

Sorry I didn't see this earlier, I don't know if you care or not but your system isn't stable. The Residual(norm) numbers should all match if your system is working properly. When overclocking my machine I let the test run for about 24 hours (few hundred times) and made sure all the numbers matched before doing anything critical on the system.

---

### Post by drphilngood on 2010-04-18
> **calc said:**
> Sorry I didn't see this earlier, I don't know if you care or not but your system isn't stable. The Residual(norm) numbers should all match if your system is working properly. When overclocking my machine I let the test run for about 24 hours (few hundred times) and made sure all the numbers matched before doing anything critical on the system.

That's strange; my rig has ran eight instances of Prime95 for 19 hours, along with various other stability testing apps, without any errors.  In addition, I have not had ANY problems with data corruption nor seen any other behavior that would indicate instability.  I suppose that Linpack could be a more strenuous test but it didn't seem to be and my rig didn't get as hot running it as it did when running Prime95. *scratches head*  However, as consequence of your notification, I will now do further testing and let you know if I get any errors.
Thanks for the 411, as well as your concern, my friend.
Have a good one!! (^_^)

addendum:
I have no explanation for this.  Attached are two more tests that were ran at higher overclocks - both with and without hyper-threading - and the Residual(norm) numbers do, indeed, match; albeit, at somewhat lower scores.  Thus, I suppose I should do further runs and see if I can duplicate the errors found in the aforementioned flawed run.
Thanks again. =)
[ATTACH]153625[/ATTACH]

---

### Post by calc on 2010-04-18
> **drphilngood said:**
> That's strange; my rig has ran eight instances of Prime95 for 19 hours, along with various other stability testing apps, without any errors.  In addition, I have not had ANY problems with data corruption nor seen any other behavior that would indicate instability.  I suppose that Linpack could be a more strenuous test but it didn't seem to be and my rig didn't get as hot running it as it did when running Prime95. *scratches head*  However, as consequence of your notification, I will now do further testing and let you know if I get any errors.
Thanks for the 411, as well as your concern, my friend.
Have a good one!! (^_^)

addendum:
I have no explanation for this.  Attached are two more tests that were ran at higher overclocks - both with and without hyper-threading - and the Residual(norm) numbers do, indeed, match; albeit, at somewhat lower scores.  Thus, I suppose I should do further runs and see if I can duplicate the errors found in the aforementioned flawed run.
Thanks again. =)
[ATTACH]153625[/ATTACH]

The highest GFlops you can get it to do combined with a stable set of residual numbers should determine a stable system. If you aren't reaching your highest GFlops number then you aren't stressing the CPU as much and so you are more likely to get a stable residual number. As I mentioned back when I first posted my numbers when I was running under Windows it tested stable (over many hours of linpack) but the GFlops were lower than under Linux and so when I ran Linpack on Linux with the same bios settings the GFlops were higher and caused a near immediate reboot of my system. I think this was due to other processes stealing time on the CPU and keeping the system from reaching peak load. So when I did my testing under Linux I booted into single user mode so that I could be sure nothing else (or very little) would be stealing CPU time and keeping the system from reaching peak load. Linpack does stress the CPU a huge amount more than Prime95 does, I don't remember the exact numbers at the moment but I had a Kill A Watt meter hooked up to my pc when I was doing burn in testing and from what I recall my system with the dinky Radeon 4350 and a 80Plus power supply was pulling over 230 Watts when under load. I used Prime95 to do initial testing to find a close range of what was stable and used Linpack to finish dialing it in. Also for long term stability you may want to keep your Vtt below 1.21 as I mentioned in my previous post. I was able to overclock higher than 3.55GHz with my CPU but it was pushing Vtt over the maximum safe limits from the Intel spec sheet. The Bloomfield LGA 1366 i7 CPUs didn't have the lower Vtt limit in their spec sheet so probably can run safe at higher Vtt voltage and thus higher overclocks. I tend to err on the safe side since I use my system for work and want it to last at least 6 years, 3 for myself and then 3 for general home use.

---

### Post by drphilngood on 2010-04-20
> **calc said:**
> The highest GFlops......general home use.
Yes, that is my point; the residual numbers of all my other runs matched, even those at higher OCs.  I guess I'll just tag it as an anomaly but do further testing and keep an eye out for any instability.
Yes, it is important to keep one's uncore voltage within spec; we all want our rigs to last as long as possible, I suppose.  However, it was my low budget, as apposed to low vtt voltage, that lowered my OCs.  I cheaped out and bought four sticks of ram - albeit, very good ram -, instead of the customary two, and that dashed my hopes for an outstanding OC.  Oh well, live and learn.
Have a good one.

---

### Post by thegreenblob on 2010-04-20
Here's the results from my Intel Core 2 Quad Q8200.

```
[joe@desktop linpack]$ ./xlinpack_xeon64 
Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 20000
Leading dimension of array: 20000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Tue Apr 20 12:31:48 2010

CPU frequency:    2.333 GHz
Number of CPUs: 4
Number of threads: 4

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      227.169    23.4809  3.625560e-10 3.209415e-02
20000  20000  4      231.208    23.0707  3.625560e-10 3.209415e-02
20000  20000  4      231.567    23.0350  3.625560e-10 3.209415e-02
20000  20000  4      227.335    23.4637  3.625560e-10 3.209415e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       23.2626  23.4809 

End of tests
```

---

### Post by decalguy on 2010-04-21
Stock HP Pavilion Elite m9250f running Linux mint 8 Helena x64

Number of equations to solve (problem size): 20000
Leading dimension of array: 20000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Wed Apr 21 09:50:50 2010

CPU frequency:    2.667 GHz
Number of CPUs: 4
Number of threads: 4

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      149.624    35.6502  3.625560e-10 3.209415e-02
20000  20000  4      149.579    35.6611  3.625560e-10 3.209415e-02
20000  20000  4      149.269    35.7351  3.625560e-10 3.209415e-02
20000  20000  4      148.725    35.8657  3.625560e-10 3.209415e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       35.7280  35.8657

---

### Post by drphilngood on 2010-04-30
i7 Lynnfield 870 on 64-bit Lucid [Average 54.2831, Maximal 54.2994]
[ATTACH]154858[/ATTACH]

---

### Post by s990we on 2010-05-03
Why wont it use all 8 threads?
Its a i7 930. (4 cores, 2 threads each)
It uses 4, then it switch to 4 others.

---

### Post by Sepiraph on 2010-05-08
```
Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 20000
Leading dimension of array: 20000
Number of trials to run: 1
Data alignment value (in Kbytes): 4
Current date/time: Sat May  8 23:13:19 2010

CPU frequency:    3.862 GHz
Number of CPUs: 8
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 1    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      93.185     57.2425  3.625560e-10 3.209415e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       57.2425  57.2425 

End of tests

```

---

### Post by MartinsBalodis on 2010-05-13
Number of equations to solve (problem size): 20000
Leading dimension of array: 20000
Number of trials to run: 1
Data alignment value (in Kbytes): 4
Current date/time: Thu May 13 23:11:35 2010

CPU frequency:    3.325 GHz
Number of CPUs: 24
Number of threads: 24

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 1    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      68.156     78.2635  3.679233e-10 3.256927e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       78.2635  78.2635 

End of tests

---

### Post by jap1968 on 2010-05-28
Atom pineview here: Intel D510MO
Dual core, HT enabled
Ubuntu 10.04 64 bits

```

Number of equations to solve (problem size): 7000
Leading dimension of array: 7000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Fri May 28 22:19:41 2010

CPU frequency:    1.667 GHz
Number of CPUs: 4
Number of threads: 4

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 7000 
Leading dimension of array                  : 7000 
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 392144096, at the size = 7000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
7000   7000   4      293.491    0.7795   5.352613e-11 3.840840e-02
7000   7000   4      292.439    0.7823   5.352613e-11 3.840840e-02
7000   7000   4      292.865    0.7811   5.352613e-11 3.840840e-02
7000   7000   4      292.753    0.7814   5.352613e-11 3.840840e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
7000   7000   4       0.7811   0.7823  

End of tests

```

---

### Post by Cavsfan on 2010-05-28
Core 2 Quad Q9550 @ 2.83GHz (unclocked)

```
CPU frequency:    2.843 GHz
Number of CPUs: 4
Number of threads: 4

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      134.952    39.5262  3.625560e-10 3.209415e-02
20000  20000  4      134.281    39.7236  3.625560e-10 3.209415e-02
20000  20000  4      134.891    39.5439  3.625560e-10 3.209415e-02
20000  20000  4      134.068    39.7868  3.625560e-10 3.209415e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       39.6451  39.7868
```GFlops = 39.6451 average. I'm happy. :)

---

### Post by jap1968 on 2010-06-03
More stats in another machine:
Intel(R) Core(TM)2 CPU 6600 @2.40GHz
Ubuntu 10.04 i686

```

Number of equations to solve (problem size): 7000
Leading dimension of array: 7000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Thu Jun  3 10:27:22 2010

CPU frequency:    2.400 GHz
Number of CPUs: 2
Number of threads: 2

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 7000 
Leading dimension of array                  : 7000 
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 392144096, at the size = 7000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
7000   7000   4      18.266     12.5240  5.316206e-11 3.814716e-02
7000   7000   4      18.179     12.5840  5.316206e-11 3.814716e-02
7000   7000   4      18.229     12.5497  5.316206e-11 3.814716e-02
7000   7000   4      18.180     12.5832  5.316206e-11 3.814716e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
7000   7000   4       12.5602  12.5840 

```

---

### Post by Milos_SD on 2010-06-03
This is strange, I have 8GB of RAM, and I can't use 30000. It says I don't have enough memory. :S

Edit: Intel Core2Duo E6550 2.33 Ghz
Here is with 20000:


```
./xlinpack_xeon64 
Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 20000
Leading dimension of array: 20000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Thu Jun  3 12:22:24 2010

CPU frequency:    2.333 GHz
Number of CPUs: 2
Number of threads: 2

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      366.192    14.5665  4.214754e-10 3.730981e-02
20000  20000  4      381.412    13.9852  4.214754e-10 3.730981e-02
20000  20000  4      378.536    14.0915  4.214754e-10 3.730981e-02
20000  20000  4      355.066    15.0229  4.214754e-10 3.730981e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       14.4165  15.0229 

End of tests

```

---

### Post by calc on 2010-06-03
> **Milos_SD said:**
> This is strange, I have 8GB of RAM, and I can't use 30000. It says I don't have enough memory. :S


Boot into single user mode and it will probably work.

---

### Post by jap1968 on 2010-10-21
More tests:
MB: Gigabyte GA-8I945GZME-RH
CPU: P4 3GHz, HT enabled
RAM: 512MB
OS: Ubuntu 10.04.1 32 bits

```

Number of equations to solve (problem size): 7000
Leading dimension of array: 7000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Thu Oct 21 16:05:13 2010

CPU frequency:    2.993 GHz
Number of CPUs: 2
Number of threads: 2

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 7000 
Leading dimension of array                  : 7000 
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 392144096, at the size = 7000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
7000   7000   4      49.903     4.5842   5.128918e-11 3.680325e-02
7000   7000   4      49.750     4.5983   5.128918e-11 3.680325e-02
7000   7000   4      49.742     4.5990   5.128918e-11 3.680325e-02
7000   7000   4      49.975     4.5776   5.128918e-11 3.680325e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
7000   7000   4       4.5898   4.5990  

End of tests

```

---

### Post by Mr.Carramba on 2010-10-22
> **calc said:**
> What kind of cpu do you have? It appears to be extremely fast, is it a Core i7 Bloomfield?

sorry for late ansver :)
I have dual quad core Intel Xeon E5410  @ 2.33GHz and 8 gig of ram :D

---

### Post by pyrosrockthisworld on 2010-11-12
heres mine it will be faster once i rebuild my com i have 2 SATAIII caviar blacks to run in raid but havent had the time to rebuild it
its a i7 860

> 
```
Current date/time: Sat Nov 13 09:48:26 2010

CPU frequency:    3.150 GHz
Number of CPUs: 8
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      111.952    47.6466  3.625560e-10 3.209415e-02
20000  20000  4      110.872    48.1106  3.625560e-10 3.209415e-02
20000  20000  4      115.331    46.2508  3.625560e-10 3.209415e-02
20000  20000  4      115.604    46.1412  3.625560e-10 3.209415e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       47.0373  48.1106 

End of tests

```


---

### Post by Cavsfan on 2010-11-14
> **pyrosrockthisworld said:**
> heres mine it will be faster once i rebuild my com i have 2 SATAIII caviar blacks to run in raid but havent had the time to rebuild it
its a i7 860

That is pretty sweet with 8 cores and all, but you should edit the post and wrap the text with CODE (highlight all of the text and then 
click the # button at the top right and it will wrap CODE and /CODE around it and it will display aligned.

It will just make it easier for us to read it. :)

---

### Post by lorenzoneri on 2010-12-23
My result on dual xeon E5410 @ 2.33GHz

Number of equations to solve (problem size): 30000
Leading dimension of array: 30000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Thu Dec 23 21:51:16 2010

CPU frequency:    2.327 GHz
Number of CPUs: 2
Number of cores: 8
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 30000
Leading dimension of array                  : 30000
Number of trials to run                     : 4
Data alignment value (in Kbytes)            : 4

Maximum memory requested that can be used = 7200604096, at the size = 30000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
30000  30000  4      291.218    61.8156  8.439482e-10 3.326853e-02
30000  30000  4      284.224    63.3367  8.439482e-10 3.326853e-02
30000  30000  4      284.810    63.2063  8.439482e-10 3.326853e-02
30000  30000  4      284.095    63.3653  8.439482e-10 3.326853e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
30000  30000  4       62.9310  63.3653

End of tests

---

### Post by pioppa84 on 2011-01-01
Number of equations to solve (problem size): 20000
Leading dimension of array: 20000
Number of trials to run: 4
Data alignment value (in Kbytes): 4   
Current date/time: Sun Jan  2 00:09:55 2011

CPU frequency:    2.400 GHz
Number of CPUs: 2
Number of cores: 8
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      73.217     72.8541  3.461960e-10 3.064593e-02
20000  20000  4      73.186     72.8844  3.461960e-10 3.064593e-02
20000  20000  4      73.356     72.7156  3.461960e-10 3.064593e-02
20000  20000  4      73.051     73.0189  3.461960e-10 3.064593e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       72.8683  73.0189 

End of tests

):P

---

### Post by jkastrup on 2011-03-25
I tested my ThinkStation D20 with 2 intel xeon x5570 processors.
I got 24Gb ram but tested it on a smaller problem to make it comparable with the memory on my GPU.
I then tested it on a larger problem (10GB size) and got similar results. 

```

:~/bin/linpack_10.3.2/benchmarks/linpack$ ./xlinpack_xeon64 
Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 20000
Leading dimension of array: 20000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Thu Mar 24 12:51:43 2011

CPU frequency:    2.934 GHz
Number of CPUs: 2
Number of cores: 8
Number of threads: 16

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      62.311     85.6049  3.461960e-10 3.064593e-02
20000  20000  4      64.963     82.1102  3.461960e-10 3.064593e-02
20000  20000  4      62.947     84.7396  3.461960e-10 3.064593e-02
20000  20000  4      62.957     84.7266  3.461960e-10 3.064593e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       84.2953  85.6049 

End of tests

```

---

### Post by handy on 2011-03-25
Why do you care who's got the most numbers?

---

### Post by drphilngood on 2011-03-25
Great score and a nice rig, jkastrup; congrats and welcome to the forums! \\:D/

---

### Post by jkastrup on 2011-03-31
> **handy said:**
> Why do you care who's got the most numbers?

I am using this as a benchmark for a Computational Fluid Dynamic code that shall be ported to a GPU. And it is nice to see what CPU performance we actually got at the moment compared to other CPUs in the case we need to upgrade our hardware.

> **drphilngood said:**
> Great score and a nice rig, jkastrup; congrats and welcome to the forums! \\:D/

Thx :D This tool convinced our department to run our own server instead of using the IT departments cluster (which is slower).

We might set to or three of these machines together (MPI) and test it again.

---

### Post by raymondlo84 on 2011-04-08
CPU: Intel i7 - 920 @ 3.3Ghz 

x] I think my results is as good as the X3360 x]

CPU frequency:    3.316 GHz
Number of CPUs: 1
Number of cores: 4
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      112.858    47.2643  3.625560e-10 3.209415e-02
20000  20000  4      117.887    45.2479  3.625560e-10 3.209415e-02
20000  20000  4      110.856    48.1175  3.625560e-10 3.209415e-02
20000  20000  4      111.003    48.0540  3.625560e-10 3.209415e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       47.1709  48.1175 

End of tests

---

### Post by normcf on 2011-04-16
Intel core i7 (sandy bridge) 8G ram
Linux transition 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux


Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 30000
Leading dimension of array: 30000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Sat Apr 16 16:31:04 2011

CPU frequency:    3.790 GHz
Number of CPUs: 1
Number of cores: 4
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 30000
Leading dimension of array                  : 30000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 7200604096, at the size = 30000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
30000  30000  4      180.324    99.8304  7.953263e-10 3.135185e-02
30000  30000  4      181.435    99.2192  7.953263e-10 3.135185e-02
30000  30000  4      179.888    100.0723 7.953263e-10 3.135185e-02
30000  30000  4      179.631    100.2153 7.953263e-10 3.135185e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
30000  30000  4       99.8343  100.2153

End of tests

Interestingly, I can run my memory at 2133 MHz using XMP on my Gigabyte P67A-UD4-B3 and the GFlops are the same, but the results are not stable (i.e. varying residuals).  I tried tweaking voltages to correct it but was unsuccessful.  If anyone has a solution, please let me know.)

---

### Post by Rhubarb on 2011-05-01
Core i7 975 running at stock speed of 3.33GHz (even though linpack thinks it's 3.589GHz), with 16GB DDR3 RAM (it's not super fast DDR 3 RAM):-
```
CPU frequency:    3.589 GHz
Number of CPUs: 1
Number of cores: 4
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 44000
Leading dimension of array                  : 44000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 15488884096, at the size = 44000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
44000  44000  4      1084.954   52.3462  1.747579e-09 3.217343e-02
44000  44000  4      1085.306   52.3292  1.747579e-09 3.217343e-02
44000  44000  4      1085.463   52.3216  1.747579e-09 3.217343e-02
44000  44000  4      1086.361   52.2784  1.747579e-09 3.217343e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
44000  44000  4       52.3189  52.3462 

End of tests
```

So, according to [wikipedia]("https://secure.wikimedia.org/wikipedia/en/wiki/Super_computing#Timeline_of_supercomputers"), my desktop is equivalent to a super computer from 1993 :)

---

### Post by aerofly5 on 2011-05-01
2GB of ram, 2Ghz OC'd Pentium E2160 (1.8Ghz standard clock)
Ubuntu 11.04 (fluxbox)
The massive perf increase between test 2 and 3 is when I decided to close my 30 firefox tabs and the 4 instances of thunar, gimp, etc etc
I also realise that my pride and joy is pretty crappy, but its amazing the performance you get from running a desktop like fluxbox. It runs Portal on full bloom, 1920x1080, 8x MSAA, 16x Anisotropic filtering, high textures/models/shaders etc. at 20 fps through wine. Portal 2 (yay!) give me 15fps on the same specs
Also, during this test I was running banshee. On my computer, banshee uses a significant amount of resources




Number of equations to solve (problem size): 13700
Leading dimension of array: 13700
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Mon May  2 00:28:58 2011

CPU frequency:    2.024 GHz
Number of CPUs: 1
Number of cores: 2
Number of threads: 2

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 13700
Leading dimension of array                  : 13700
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 1501798096, at the size = 13700

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
13700  13700  4      289.267    5.9274   1.901662e-10 3.587101e-02
13700  13700  4      303.308    5.6530   1.901662e-10 3.587101e-02
13700  13700  4      264.172    6.4905   1.901662e-10 3.587101e-02
13700  13700  4      267.225    6.4164   1.901662e-10 3.587101e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
13700  13700  4       6.1218   6.4905  

End of tests

---

### Post by drphilngood on 2011-08-07
Found a great deal on some new ram - G.SKILL Ripjaws X Series 8GB (2 x 4GB) - and, sure enough, it cured what was ailing me. ;-)

Average: 59.0333
Maximal: 59.0388
[ATTACH]199515[/ATTACH]

My ole' Lynnfield will go higher but this is as high as I'm comfortable running it until I improve my cooling.
[IMG]http://img.photobucket.com/albums/v490/drphilngood/Cheers-dp.gif[/IMG]

---

### Post by festivemongoose on 2011-11-01
[B]2 x Intel Xeon CPU X5650 @ 2.67GHz
Running CentOS 6.0 x86_64[/B]

Number of equations to solve (problem size): 40000
Leading dimension of array: 40000
Number of trials to run: 2
Data alignment value (in Kbytes): 4
Current date/time: Tue Nov  1 10:36:29 2011

CPU frequency:    1.589 GHz
Number of CPUs: 2
Number of cores: 12
Number of threads: 24

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 40000
Leading dimension of array                  : 40000
Number of trials to run                     : 2    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 12800804096, at the size = 40000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
40000  40000  4      350.921    121.5941 1.486401e-09 3.305806e-02
40000  40000  4      350.674    121.6795 1.486401e-09 3.305806e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
40000  40000  4       121.6368 121.6795



**A KVM Virtual Machine Guest with **_**12 vcpu:**_

Number of equations to solve (problem size): 30000
Leading dimension of array: 30000
Number of trials to run: 2
Data alignment value (in Kbytes): 4
Current date/time: Tue Nov  1 10:38:29 2011

CPU frequency:    1.553 GHz
Number of CPUs: 12
Number of cores: 12
Number of threads: 12

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 30000
Leading dimension of array                  : 30000
Number of trials to run                     : 2    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 7200604096, at the size = 30000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
30000  30000  4      213.382    84.3643  8.580995e-10 3.382637e-02
30000  30000  4      213.641    84.2620  8.580995e-10 3.382637e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
30000  30000  4       84.3132  84.3643 



**A KVM Virtual Machine Guest with **[U][B]6 vcpu:

[/B][/U]Number of equations to solve (problem size): 30000
Leading dimension of array: 30000
Number of trials to run: 1
Data alignment value (in Kbytes): 4
Current date/time: Tue Nov  1 10:16:30 2011

CPU frequency:    2.978 GHz
Number of CPUs: 6
Number of cores: 6
Number of threads: 6

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 30000
Leading dimension of array                  : 30000
Number of trials to run                     : 1    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 7200604096, at the size = 30000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
30000  30000  4      393.404    45.7590  7.907299e-10 3.117066e-02

---

### Post by Mr.Carramba on 2011-11-01
new pc new test :popcorn:

weird thing that CPU speed is detected as 4.425 ... but it is actually 3.40 hum..

```

->./xlinpack_xeon64 
Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 30000     
Leading dimension of array: 30000
Number of trials to run: 2
Data alignment value (in Kbytes): 4
Current date/time: Tue Nov  1 18:01:09 2011

CPU frequency:    4.425 GHz
Number of CPUs: 1
Number of cores: 4
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 30000
Leading dimension of array                  : 30000
Number of trials to run                     : 2    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 7200604096, at the size = 30000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
30000  30000  4      144.665    124.4379 8.421348e-10 3.319704e-02
30000  30000  4      145.012    124.1402 8.421348e-10 3.319704e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
30000  30000  4       124.2890 124.4379

End of tests

```

---

### Post by festivemongoose on 2011-11-01
> **Mr.Carramba said:**
> new pc new test :popcorn:

weird thing that CPU speed is detected as 4.425 ... but it is actually 3.40 hum..




What CPU are u using? i find it strange that you would outperform a server with 24 threads that i posted....

---

### Post by Mr.Carramba on 2011-11-02
> **festivemongoose said:**
> What CPU are u using? i find it strange that you would outperform a server with 24 threads that i posted....

Well I use normal [INTEL CORE I7 2600K 3.40GHZ 8MB S-1155]("http://www.dustin.se/intel-core-i7-2600k-340ghz-8mb-s-1155/product/5010544373"), however I have [OCZ Revo 2X]("http://www.ocztechnology.com/ocz-revodrive-x2-pci-express-ssd.html")   as primary hd. 

But you rise interesting technical question. Maybe my memory is faster? I run test again with the same results :) This is my stationary machine and it also totaly outperforms outperform the server :

```

Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 30000
Leading dimension of array: 30000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Wed Nov  2 09:12:29 2011

CPU frequency:    2.325 GHz
Number of CPUs: 2
Number of cores: 8
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 30000
Leading dimension of array                  : 30000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 7200604096, at the size = 30000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
30000  30000  4      307.246    58.5909  8.439482e-10 3.326853e-02
30000  30000  4      306.864    58.6638  8.439482e-10 3.326853e-02


```

---

### Post by festivemongoose on 2011-11-02
> **Mr.Carramba said:**
> Well I use normal [INTEL CORE I7 2600K 3.40GHZ 8MB S-1155]("http://www.dustin.se/intel-core-i7-2600k-340ghz-8mb-s-1155/product/5010544373"), however I have [OCZ Revo 2X]("http://www.ocztechnology.com/ocz-revodrive-x2-pci-express-ssd.html")   as primary hd. 

But you rise interesting technical question. Maybe my memory is faster? I run test again with the same results :) This is my stationary machine and it also totaly outperforms outperform the server :

```

Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 30000
Leading dimension of array: 30000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Wed Nov  2 09:12:29 2011

CPU frequency:    2.325 GHz
Number of CPUs: 2
Number of cores: 8
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 30000
Leading dimension of array                  : 30000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 7200604096, at the size = 30000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
30000  30000  4      307.246    58.5909  8.439482e-10 3.326853e-02
30000  30000  4      306.864    58.6638  8.439482e-10 3.326853e-02


```

no the server i posted was 122 GFlops.

Its connected through 8gbs Fiber to a SAN (but disk io has nothing to do with this benchmark)

it has 96GB DDR3 ECC triple channel 1333
2 sockets or 6 cores with Hyperthreading meaning it can handle 24 threads (24 logical cores)

makes no sense that a desktop cpu would come close. i guess this benchmark is flawed.

---

### Post by Mr.Carramba on 2011-11-02
> **festivemongoose said:**
> no the server i posted was 122 GFlops.

Its connected through 8gbs Fiber to a SAN (but disk io has nothing to do with this benchmark)

it has 96GB DDR3 ECC triple channel 1333
2 sockets or 6 cores with Hyperthreading meaning it can handle 24 threads (24 logical cores)

makes no sense that a desktop cpu would come close. i guess this benchmark is flawed.

I guess you need to increase the number of equations to solve and dimensions of leading array to allocate ~90% of the ram, then you will get different results. Considering the same amount of memory used as well as the similar CPU performance I guess the result is ok.

Try to set values to 360000 since your ram can handle it, and I bet you will get more realistic performance results.

---

### Post by Mr.Carramba on 2011-11-02
some googling reveals that 130 Gflops on sandy bridge i7 2900K is not unusual. [http://www.overclock.net/intel-cpus/916911-true-power-sandy-bridge-130-gflop.html](http://www.overclock.net/intel-cpus/916911-true-power-sandy-bridge-130-gflop.html)
As I wrote previously try to increase the size of the test and I am sure the result will bump up!

---

### Post by festivemongoose on 2011-11-02
> **Mr.Carramba said:**
> some googling reveals that 130 Gflops on sandy bridge i7 2900K is not unusual. [http://www.overclock.net/intel-cpus/916911-true-power-sandy-bridge-130-gflop.html](http://www.overclock.net/intel-cpus/916911-true-power-sandy-bridge-130-gflop.html)
As I wrote previously try to increase the size of the test and I am sure the result will bump up!


I tried that already, didn't improve results, juts took longer to finish. see results below.

The reality of the matter is that this server will destroy any desktop in performance (except in video games obviously). its not even close. However this benchmark does not adequately represent that. therefore its flawed. It doesnt even seem to care about logical cores (hyperthreading)

Please read the specs: Dell PowerEdge M610 w/ Intel Xeon CPU X5650 + 96GB DDR3 1333 (triple channel, 6 x 16GB dimms) it has 2 local 15k drives and a fiberchannel 8GB/s link to an EMC SAN with over 100 drives.

You have to relaize that ONE 16GB dimm costs more than a whole desktop computer.


Here are results with Hyperthreading on and off:


**HYPER-THREADING ON:** [COLOR=Red]**123.0563**[/COLOR]

CPU frequency:    1.587 GHz
Number of CPUs: 2
Number of cores: 12
Number of threads: 24

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 50000
Leading dimension of array                  : 50000
Number of trials to run                     : 2    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 20001004096, at the size = 50000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
50000  50000  4      680.130    122.5329 2.235481e-09 3.187639e-02
50000  50000  4      674.369    123.5798 2.235481e-09 3.187639e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
50000  50000  4       123.0563 123.5798


**HYPER-THREADING OFF: **[COLOR=Red]**124.4193 GF average**[/COLOR]

CPU frequency:   1.587 GHz
Number of CPUs: 2
Number of cores: 12
Number of threads: 12

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 50000
Leading dimension of array                  : 50000
Number of trials to run                     : 2    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 20001004096, at the size = 50000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
50000  50000  4      668.819    124.6052 2.235481e-09 3.187639e-02
50000  50000  4      670.821    124.2334 2.235481e-09 3.187639e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
50000  50000  4      ** 124.4193** 124.6052

---

### Post by Mr.Carramba on 2011-11-02
> **festivemongoose said:**
> I tried that already, didn't improve results, juts took longer to finish. see results below.

The reality of the matter is that this server will destroy any desktop in performance (except in video games obviously). its not even close. However this benchmark does not adequately represent that. therefore its flawed. It doesnt even seem to care about logical cores (hyperthreading)

Please read the specs: Dell PowerEdge M610 w/ Intel Xeon CPU X5650 + 96GB DDR3 1333 (triple channel, 6 x 16GB dimms) it has 2 local 15k drives and a fiberchannel 8GB/s link to an EMC SAN with over 100 drives.

You have to relaize that ONE 16GB dimm costs more than a whole desktop computer.


Here are results with Hyperthreading on and off:


**HYPER-THREADING ON:** [COLOR=Red]**123.0563**[/COLOR]

CPU frequency:    1.587 GHz
Number of CPUs: 2
Number of cores: 12
Number of threads: 24

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 50000
Leading dimension of array                  : 50000
Number of trials to run                     : 2    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 20001004096, at the size = 50000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
50000  50000  4      680.130    122.5329 2.235481e-09 3.187639e-02
50000  50000  4      674.369    123.5798 2.235481e-09 3.187639e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
50000  50000  4       123.0563 123.5798


**HYPER-THREADING OFF: **[COLOR=Red]**124.4193 GF average**[/COLOR]

CPU frequency:   1.587 GHz
Number of CPUs: 2
Number of cores: 12
Number of threads: 12

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 50000
Leading dimension of array                  : 50000
Number of trials to run                     : 2    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 20001004096, at the size = 50000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
50000  50000  4      668.819    124.6052 2.235481e-09 3.187639e-02
50000  50000  4      670.821    124.2334 2.235481e-09 3.187639e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
50000  50000  4      ** 124.4193** 124.6052

Dunno how this argument will hold but if we take a look at the total amount of Ghz available:
your server 12x1.587 = 19.044 (see note below)
my pc 4x4.425 = 17.7
The difference is not so big, and it can be the case that the new CPU handles the instructions much better

According to Intel > best performance will be obtained with the Intel® Hyper-Threading Technology turned off

I mostly currios why you Intel Xeon CPU X5650 is determined to CPU frequency:   1.587 GHz? According to the specs it should be 2.66 GHz and 3.04 in turbo mode.

---

### Post by festivemongoose on 2011-11-02
> **Mr.Carramba said:**
> Dunno how this argument will hold but if we take a look at the total amount of Ghz available:
your server 12x1.587 = 19.044 (see note below)
my pc 4x4.425 = 17.7
The difference is not so big, and it can be the case that the new CPU handles the instructions much better

According to Intel 

I mostly currios why you Intel Xeon CPU X5650 is determined to CPU frequency:   1.587 GHz? According to the specs it should be 2.66 GHz and 3.04 in turbo mode.


Yes I can confirm it goes up to 3GHZ as soon as load test starts. 1.5GHZ is during idle. so this argument is meaningless. The test is flawed.  But thanks for your input

---

### Post by Mr.Carramba on 2011-11-02
> **festivemongoose said:**
> Yes I can confirm it goes up to 3GHZ as soon as load test starts. 1.5GHZ is during idle. so this argument is meaningless. The test is flawed.  But thanks for your input

But look at the output given by linpak, it run at 1.5 speed > CPU frequency:    1.587 GHzThank you too, I am very curios about the reasons for this malfunction. I don't think that there is something wrong with the benchmark software. It is used to score [TOP500]("http://en.wikipedia.org/wiki/TOP500") supercomputers and I guess somebody would have noticed errors by this time.

---

### Post by festivemongoose on 2011-11-02
The output is because when the scripts starts it outputs the CURRENT frequency.

Once the test starts the frequency rises. sometimes when i run the test it output 3Ghz, it just happened to be 3Ghz when the test started. 

When the script asks for frequency it gets the CURRENT amount, which at idle is correctly 1.5GHz. its NOT incorrect. why would it be higher when its doing nothing? do you understand?

---

### Post by Nosophorus on 2011-11-18
Hi!

My machine:

```
OS.: Ubuntu GNU/Linux Lucid Lynx 10.04 LTS
CPU: Intel Pentium D 2.66 GHz (2 CPUs, 1 Core Each)
RAM: 2 GiB
```

This computer is a little bit "old". I bought it in 2006 and I don't intend to get a new one for, at least, the next 5/10 years.

My stats:

```
Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 13700
Leading dimension of array: 13700
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Fri Nov 18 00:48:33 2011

CPU frequency:    2.658 GHz
Number of CPUs: 1
Number of cores: 2
Number of threads: 2

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 13700
Leading dimension of array                  : 13700
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 1501798096, at the size = 13700

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
13700  13700  4      215.180    7.9683   1.797777e-10 3.391142e-02
13700  13700  4      214.998    7.9750   1.797777e-10 3.391142e-02
13700  13700  4      215.090    7.9716   1.797777e-10 3.391142e-02
13700  13700  4      215.764    7.9467   1.797777e-10 3.391142e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
13700  13700  4       7.9654   7.9750  

End of tests

```

Amazing: **7.96** GFLOPS!

It would be interesting if we could find a supercomputer ranking (FLOPS) with all machines since the beginning of supercomputing.

If I had a time machine and came back to 1985, my computer would be the fastest in the world!

It astonishes me that, in the past, people with a much lower computing power at their hands could achieve such a marvelous things, such as Sputnik I, landing on the Moon, deep water research, space stations and so on.

For example, it is said that it took the computational power of only 3 [Commodore 64]("http://en.wikipedia.org/wiki/Commodore_64") to send man to the Moon!

It is funny and a little bit sad that in our age, with all its computational power splendor, people use their computing power to watch porn, MSN Messenger strip tease and social network drivels. :D:D

Well, that's democracy!

See You!

Nosophorus

---

### Post by LxndrPhnx on 2011-11-25
Running Ubuntu 11.04 on an Asus G74Sx, i7-2670QM processor, 8GB RAM 

```
tyler@tyler-G74Sx:~/linpack_10.3.7/benchmarks/linpack$ ./xlinpack_xeon64
Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 30000
Leading dimension of array: 30000
Number of trials to run: 1
Data alignment value (in Kbytes): 4
Current date/time: Fri Nov 25 22:37:15 2011

CPU frequency:    3.015 GHz
Number of CPUs: 1
Number of cores: 4
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 30000
Leading dimension of array                  : 30000
Number of trials to run                     : 1    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 7200604096, at the size = 30000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
30000  30000  4      285.790    62.9897  8.421348e-10 3.319704e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
30000  30000  4       62.9897  62.9897 

End of tests

```

62! Awesome :P

---

### Post by CloudGlider on 2011-12-06
```

Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 20000 
Leading dimension of array: 20000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Tue Dec  6 16:28:39 2011

CPU frequency:    3.476 GHz
Number of CPUs: 1
Number of cores: 4
Number of threads: 8

Parameters are set to:
                                                                                                                                               
Number of tests                             : 1                                                                                                
Number of equations to solve (problem size) : 20000                                                                                            
Leading dimension of array                  : 20000                                                                                            
Number of trials to run                     : 4                                                                                                
Data alignment value (in Kbytes)            : 4                                                                                                
                                                                                                                                               
Maximum memory requested that can be used = 3200404096, at the size = 20000                                                                    
                                                                                                                                               
============= Timing linear equation system solver =================                                                                           
                                                                                                                                               
Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)                                                                           
20000  20000  4      59.883     89.0752  4.097986e-10 3.627616e-02                                                                             
20000  20000  4      72.107     73.9751  4.097986e-10 3.627616e-02                                                                             
20000  20000  4      72.643     73.4294  4.097986e-10 3.627616e-02                                                                             
20000  20000  4      72.399     73.6768  4.097986e-10 3.627616e-02                                                                             
                                                                                                                                               
Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       77.5391  89.0752 

End of tests


```

---

### Post by Takahashi_NZ on 2011-12-08
Ubuntu 10.04 Tyan S2665 with 2x 3.2Ghz Xeon SL7AE and 2GB Ram

```
j@XXXXX:~/linpack_10.3.7/benchmarks/linpack$ Input data or print help ? Type [data]/help :
Number of equations to solve (problem size): 13700
Leading dimension of array: 13700
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Fri Dec  9 17:24:17 2011

CPU frequency:    5.809 GHz
Number of CPUs: 2
Number of cores: 2
Number of threads: 4

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 13700
Leading dimension of array                  : 13700
Number of trials to run                     : 4
Data alignment value (in Kbytes)            : 4

Maximum memory requested that can be used = 1501798096, at the size = 13700

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
13700  13700  4      186.533    9.1920   1.807222e-10 3.408959e-02
13700  13700  4      185.325    9.2519   1.807222e-10 3.408959e-02
13700  13700  4      185.910    9.2228   1.807222e-10 3.408959e-02
13700  13700  4      185.640    9.2362   1.807222e-10 3.408959e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
13700  13700  4       9.2257   9.2519

End of tests
```

not bad for an 8 year old pc me thinks.

---

### Post by Takahashi_NZ on 2011-12-09
Ubuntu 11.10 desktop Toshiba Tecra p5, T7300 core 2 duo @ 2ghz


```
j@xxxxxx:~/Downloads/linpack_10.3.7/benchmarks/linpack$ ./xlinpack_xeon64Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 16000
Leading dimension of array: 16000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Fri Dec  9 17:39:02 2011

CPU frequency:    1.994 GHz
Number of CPUs: 1
Number of cores: 2
Number of threads: 2

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 16000
Leading dimension of array                  : 16000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 2048324096, at the size = 16000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
16000  16000  4      206.397    13.2327  2.526586e-10 3.493516e-02
16000  16000  4      216.923    12.5905  2.526586e-10 3.493516e-02
16000  16000  4      222.559    12.2717  2.526586e-10 3.493516e-02
16000  16000  4      224.903    12.1438  2.526586e-10 3.493516e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
16000  16000  4       12.5597  13.2327 

End of tests
```

not sure if 16000 was the right number for 3gb of ram, would have expected a bit more given this machine is half the age of the tyan. I guess it is running a gui too.

---

### Post by blackrim on 2012-01-05
Just an additional one with the same data inputs as the first coming in at over 320 Gflops and a few Intel Xeon CPU E7- 4870 's

```
Number of equations to solve (problem size): 20000
Leading dimension of array: 20000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Thu Jan  5 16:55:50 2012

CPU frequency:    2.381 GHz
Number of CPUs: 4
Number of cores: 40
Number of threads: 40

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4
Data alignment value (in Kbytes)            : 4

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      16.555     322.2047 3.563910e-10 3.154841e-02
20000  20000  4      16.650     320.3759 3.563910e-10 3.154841e-02
20000  20000  4      16.603     321.2728 3.563910e-10 3.154841e-02
20000  20000  4      16.610     321.1364 3.563910e-10 3.154841e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       321.2475 322.2047

End of tests

```

---

### Post by roobie on 2012-01-12
> **blackrim said:**
> Just an additional one with the same data inputs as the first coming in at over 320 Gflops and a few Intel Xeon CPU E7- 4870 's

```
Number of equations to solve (problem size): 20000
Leading dimension of array: 20000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Thu Jan  5 16:55:50 2012

CPU frequency:    2.381 GHz
Number of CPUs: 4
Number of cores: 40
Number of threads: 40

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4
Data alignment value (in Kbytes)            : 4

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      16.555     322.2047 3.563910e-10 3.154841e-02
20000  20000  4      16.650     320.3759 3.563910e-10 3.154841e-02
20000  20000  4      16.603     321.2728 3.563910e-10 3.154841e-02
20000  20000  4      16.610     321.1364 3.563910e-10 3.154841e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       321.2475 322.2047

End of tests

```

Is that your work station? Insane results. I mean 40 cores.... :KS

Here are my results with an unclocked Intel TM 2600K i7 @ 3.4 GHz [Quad core w/ HT] on Xubuntu 11.10:

N.B The output says that the CPU is running @ ~4.4 GHz, which is the turbo speed, or w/e it's called.

```

ubuntu@ubuntu:~/Downloads/linpack_10.3.7/benchmarks/linpack$ ./xlinpack_xeon64 
Input data or print help ? Type [data]/help :

Number of equations to solve (problem size): 20000
Leading dimension of array: 20000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Thu Jan 12 17:41:31 2012

CPU frequency:    4.428 GHz
Number of CPUs: 1
Number of cores: 4
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      44.239     120.5754 4.097986e-10 3.627616e-02
20000  20000  4      49.116     108.6028 4.097986e-10 3.627616e-02
20000  20000  4      51.171     104.2421 4.097986e-10 3.627616e-02
20000  20000  4      51.961     102.6558 4.097986e-10 3.627616e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       109.0190 120.5754

End of tests

```

---

### Post by RickyTrampta on 2012-02-26
Results with core i7 2600K not over-clocked 16Go of RAM


```
$ ./xlinpack_xeon64 
Input data or print help ? Type [data]/help :
60000
Number of equations to solve (problem size): 20000
Leading dimension of array: 20000
Number of trials to run: 4
Data alignment value (in Kbytes): 4
Current date/time: Sun Feb 26 10:30:36 2012

CPU frequency:    3.810 GHz
Number of CPUs: 1
Number of cores: 4
Number of threads: 8

Parameters are set to:

Number of tests                             : 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used = 3200404096, at the size = 20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      54.529     97.8221  4.097986e-10 3.627616e-02
20000  20000  4      54.661     97.5866  4.097986e-10 3.627616e-02
20000  20000  4      54.842     97.2631  4.097986e-10 3.627616e-02
20000  20000  4      54.873     97.2080  4.097986e-10 3.627616e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       97.4699  97.8221 

End of tests

```

---

### Post by kronoxx on 2012-08-07
Overclocked i5-2300 CPU @ 2.80GHz
8 GB RAM
ASUS MAXIMUS-IV Extreme-Z
Gentoo 3.5.0 (-march=core2 -O2)
```

CPU frequency:    3.109 GHz
Number of CPUs: 1
Number of cores: 4
Number of threads: 4

Parameters are set to:

Number of tests: 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used=3200404096, at the size=20000

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      62.289     85.6349  4.097986e-10 3.627616e-02
20000  20000  4      62.288     85.6369  4.097986e-10 3.627616e-02
20000  20000  4      62.288     85.6365  4.097986e-10 3.627616e-02
20000  20000  4      62.364     85.5323  4.097986e-10 3.627616e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       85.6102  85.6369

```

---

### Post by kronoxx on 2012-08-07
Overclocked i5-2300 CPU @ 2.80GHz
8 GB RAM
ASUS MAXIMUS-IV Extreme-Z
Kubuntu 12.04 Linux 3.2.0-27-generic

```
CPU frequency:    3.108 GHz
Number of CPUs: 1
Number of cores: 4
Number of threads: 4

Parameters are set to:
                                                                                                                                                                                              
Number of tests: 1                                                                                                                                                                            
Number of equations to solve (problem size) : 20000                                                                                                                                           
Leading dimension of array                  : 20000                                                                                                                                           
Number of trials to run                     : 4                                                                                                                                               
Data alignment value (in Kbytes)            : 4                                                                                                                                               
                                                                                                                                                                                              
Maximum memory requested that can be used=3200404096, at the size=20000                                                                                                                       
                                                                                                                                                                                              
============= Timing linear equation system solver =================                                                                                                                          

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
20000  20000  4      61.158     87.2189  4.097986e-10 3.627616e-02
20000  20000  4      61.054     87.3681  4.097986e-10 3.627616e-02
20000  20000  4      60.970     87.4885  4.097986e-10 3.627616e-02
20000  20000  4      62.803     84.9339  4.097986e-10 3.627616e-02

Performance Summary (GFlops)

Size   LDA    Align.  Average  Maximal
20000  20000  4       86.7524  87.4885
```

[COLOR=Red]Can't believe this. Its amazing! Kubuntu faster than Gentoo with last customized image![/COLOR]

---

