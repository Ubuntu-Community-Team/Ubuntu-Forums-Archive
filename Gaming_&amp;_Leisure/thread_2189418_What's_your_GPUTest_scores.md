---
title: "What's your GPUTest scores"
date: 2013-11-22
forum: Gaming &amp; Leisure
---

### Post by dannyboy79 on 2013-11-22
I wanted to test out the newest AMD BETA driver from the website and when I compared the results of my glmark2 scores something was seriously wrong. With the latest stable release driver, Catalyst 13.4 I got 5,341 and with the latest BETA Catalyst 13.11 I got 59. I've learned that the newest drivers there's a bug and the test max's out at 60 FPS so it's worthless to run glmark2 if you're running the latest BETA AMD driver.

So I thought I should look into other benchmarking apps for Linux.

So here's my results from putting my HD5750 thru the various benchmarks that come within GPUTest 0.6.0. It's GUI is python based and you should have everything required already to run it. Just download the zip from here: [GPUTest 0.6.0]("http://www.geeks3d.com/20131028/gputest-0-6-0-opengl-benchmark-for-windows-mac-os-x-and-linux-downloads/#download") and if it doesn't run, issue the following
```
sudo apt-get install python-tk
``` 
to install the python module it uses and you should be good to go. You just double click gputest_gui.py from wherever you extracted to, mine onto my desktop within a subfolder named GPUTest_Linux_x64_0.6.0

**Please run the following tests in a 1280x720 window with anti-aliasing OFF so the results are all of the same resolution/setting please. I've been informed that cards will always provide different results the first time it's run due to the card being "cold" so please run each test twice and post the 2nd run scores. Please list the graphics driver you're using also as well as whether or not you're using desktop effects like compiz or what not.**> 
Furmark
Tessmark (X16)
Gimark
Pixmark Piano
Pixmark Volplosion 


Table of scores here:
[IMG]https://lh3.googleusercontent.com/-xr3gtH6tg0E/Up6UkGngFFI/AAAAAAAACTM/_PJepvs2Ow0/s850/gputests_2-3-13.png[/IMG]

Results can be found within a file called _geeks3d_gputest_scores.csv which should be in the folder that you run gputest_gui.py from, Here's my results:
> Module,Renderer,ApiVersion,Width,Height,Fullscreen,AntiAliasing,AvgFPS,Duration,MaxGpuTemp,Score
FurMark,ATI Radeon HD 5700 Series ,4.3.12614 Core Profile Context 13.25.18,1280,720,NO,Off,36,60000,0,2171
TessMark (X8/X8),ATI Radeon HD 5700 Series ,4.3.12614 Core Profile Context 13.25.18,1280,720,NO,Off,59,60000,0,3598
GiMark,ATI Radeon HD 5700 Series ,4.3.12614 Core Profile Context 13.25.18,1280,720,NO,Off,38,60000,0,2337
PixMark Piano,ATI Radeon HD 5700 Series ,4.3.12614 Core Profile Context 13.25.18,1280,720,NO,Off,7,60000,0,464
PixMark Volplosion,ATI Radeon HD 5700 Series ,4.3.12614 Core Profile Context 13.25.18,1280,720,NO,Off,27,60000,0,1668


UPDATE: i got an HD7770 Black Edition from a friend who was getting directX errors in windows and he knew I used linux and there's no directx so he just gave it to me. AWESOME. Added those scores. Weird how Pixmark Volplosion was lower though?

---

### Post by efflandt on 2013-11-23
These are scores for 12.04 on i5 650 3.2 GHz desktop in 1280x720 window:```
Module,Renderer,ApiVersion,Width,Height,Fullscreen,AntiAliasing,AvgFPS,Duration,MaxGpuTemp,Score
FurMark,GeForce GTX 550 Ti/PCIe/SSE2,4.3.0 NVIDIA 319.32,1280,720,NO,Off,43,60000,0,2605
GiMark,GeForce GTX 550 Ti/PCIe/SSE2,4.3.0 NVIDIA 319.32,1280,720,NO,Off,21,60000,0,1276
PixMark Piano,GeForce GTX 550 Ti/PCIe/SSE2,4.3.0 NVIDIA 319.32,1280,720,NO,Off,8,60000,0,483
PixMark Volplosion,GeForce GTX 550 Ti/PCIe/SSE2,4.3.0 NVIDIA 319.32,1280,720,NO,Off,23,60000,0,1414
Plot3D,GeForce GTX 550 Ti/PCIe/SSE2,4.3.0 NVIDIA 319.32,1280,720,NO,Off,609,60000,0,36541
TessMark (X16/X16),GeForce GTX 550 Ti/PCIe/SSE2,4.3.0 NVIDIA 319.32,1280,720,NO,Off,321,60000,0,19274
Triangle,GeForce GTX 550 Ti/PCIe/SSE2,4.3.0 NVIDIA 319.32,1280,720,NO,Off,3279,60000,0,196820
```Following is 13.10 on MSI laptop with i7-4700MQ (probably 2.4 GHz, have not tested if turbo works in Linux). Note that first block with Intel video could not run all tests, no progress was shown for any test (progress bar just solid white). 2nd block used optirun (not sure how to get primusrun to work for anything at all yet):```
Module,Renderer,ApiVersion,Width,Height,Fullscreen,AntiAliasing,AvgFPS,Duration,MaxGpuTemp,Score
FurMark,Gallium 0.4 on llvmpipe (LLVM 3.3, 256 bits),2.1 Mesa 9.2.1,1280,720,NO,Off,0,60000,0,30
PixMark Volplosion,Gallium 0.4 on llvmpipe (LLVM 3.3, 256 bits),2.1 Mesa 9.2.1,1280,720,NO,Off,2,60000,0,135
Plot3D,Gallium 0.4 on llvmpipe (LLVM 3.3, 256 bits),2.1 Mesa 9.2.1,1280,720,NO,Off,6,60000,0,389
Triangle,Gallium 0.4 on llvmpipe (LLVM 3.3, 256 bits),2.1 Mesa 9.2.1,1280,720,NO,Off,176,60000,0,10603

FurMark,GeForce GTX 765M/PCIe/SSE2,4.3.0 NVIDIA 319.60,1280,720,NO,Off,23,60000,0,1425
GiMark,GeForce GTX 765M/PCIe/SSE2,4.3.0 NVIDIA 319.60,1280,720,NO,Off,42,60000,0,2524
PixMark Piano,GeForce GTX 765M/PCIe/SSE2,4.3.0 NVIDIA 319.60,1280,720,NO,Off,12,60000,0,767
PixMark Volplosion,GeForce GTX 765M/PCIe/SSE2,4.3.0 NVIDIA 319.60,1280,720,NO,Off,28,60000,0,1703
Plot3D,GeForce GTX 765M/PCIe/SSE2,4.3.0 NVIDIA 319.60,1280,720,NO,Off,146,60000,0,8773
TessMark (X16/X16),GeForce GTX 765M/PCIe/SSE2,4.3.0 NVIDIA 319.60,1280,720,NO,Off,129,60000,0,7759
Triangle,GeForce GTX 765M/PCIe/SSE2,4.3.0 NVIDIA 319.60,1280,720,NO,Off,148,60000,0,8936
```For the most part Intel graphics are unusable for gaming. Strange that it was faster than nvidia in triangle test (not sure what that does, since it appears to not move or flash at all). My desktop blows them both away in that test, but is slower than laptop nvidia in GiMark, Piano, and Volplosion tests.

---

### Post by R33D3M33R on 2013-11-23
Catalyst 13.11 Beta 6, HD 7750, i3 2120, Kubuntu 13.10, Desktop effects: ON

```
Module,Renderer,ApiVersion,Width,Height,Fullscreen,AntiAliasing,AvgFPS,Duration,MaxGpuTemp,Score
FurMark,AMD Radeon HD 7700 Series ,4.3.12614 Core Profile Context 9.01.8,1024,640,NO,Off,29,60000,0,1755
GiMark,AMD Radeon HD 7700 Series ,4.3.12614 Core Profile Context 9.01.8,1024,640,NO,Off,57,60000,0,3459
PixMark Piano,AMD Radeon HD 7700 Series ,4.3.12614 Core Profile Context 9.01.8,1024,640,NO,Off,7,60000,0,444
PixMark Volplosion,AMD Radeon HD 7700 Series ,4.3.12614 Core Profile Context 9.01.8,1024,640,NO,Off,20,60000,0,1210
Plot3D,AMD Radeon HD 7700 Series ,4.3.12614 Core Profile Context 9.01.8,1024,640,NO,Off,665,60000,0,39906
TessMark (X32/X32),AMD Radeon HD 7700 Series ,4.3.12614 Core Profile Context 9.01.8,1024,640,NO,Off,208,60000,0,12485
Triangle,AMD Radeon HD 7700 Series ,4.3.12614 Core Profile Context 9.01.8,1024,640,NO,Off,1816,60000,0,108901
```

Windows 7 vs. Linux comparison:
[ATTACH=CONFIG]248018[/ATTACH]

Windows version is very buggy and even produced a memory leak and a BSOD at Tessmark.

---

### Post by Ranko Kohime on 2013-11-25
> **efflandt said:**
> For the most part Intel graphics are unusable for gaming (~5 seconds/frame instead of frames/sec in 1st test).
I've gamed extensively on my Sandy Bridge i3, and your laptop is two generations newer, so I'd say it's more likely that test isn't worth much.  :)

That being said, I cannot get ANY of the tests to run on my system at all.  :-?

---

### Post by dannyboy79 on 2013-11-25
> **Ranko Kohime said:**
> I've gamed extensively on my Sandy Bridge i3, and your laptop is two generations newer, so I'd say it's more likely that test isn't worth much.  :)

That being said, I cannot get ANY of the tests to run on my system at all.  :-?what does ```
glxinfo | grep renderi
``` return?

---

### Post by DanglingPointer on 2013-11-25
Probably best if the results are tabulated at the start of the thread like the glmark2 scores thread.

It would be a good resource for those trying to figure out which gpu card to buy.

---

### Post by dannyboy79 on 2013-11-26
> **DanglingPointer said:**
> Probably best if the results are tabulated at the start of the thread like the glmark2 scores thread.

It would be a good resource for those trying to figure out which gpu card to buy.

i agree. i am curious how people are getting the text copied and pasted into this thread. the results screen for me was just a window with unselectable text. What am I missing here, is there a log file that's being written somewhere?

---

### Post by R33D3M33R on 2013-11-26
There is a file named _geeks3d_gputest_scores.csv in the benchmark folder to which the results are being written.

---

### Post by Ranko Kohime on 2013-11-27
> **dannyboy79 said:**
> what does ```
glxinfo | grep renderi
``` return?
```
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend,
```

---

### Post by dannyboy79 on 2013-12-01
> **Ranko Kohime said:**
> ```
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend,
```
which intel driver are you using? there's no reason you shouldn't be able to run the tests yet you can game. makes no sense

---

### Post by Ranko Kohime on 2013-12-01
> **dannyboy79 said:**
> which intel driver are you using? there's no reason you shouldn't be able to run the tests yet you can game. makes no sense
i915

---

### Post by dannyboy79 on 2013-12-03
> **Ranko Kohime said:**
> i915
why don't you try intel's driver? isn't it just "intel"? i've heard great things about the latest Mesa driver. Admittedly I am very confused about intel gfx drivers as I have never needed to use them so I don't know what's the best intel driver to use.

---

### Post by DanglingPointer on 2013-12-03
Awesome!

I'll be running all the tests at 720 window with no AA as you mentioned.

I will also be watercooling the 290X by the end of the month to sustain a GHz on the card; I'll run another test then to see the difference (the card throttles down when it reaches 94C or uses too much power)

Also perhaps if you could throw a recommendation on the first thread to run the benchmark once before running the official benchmark cause for people with cards like the 290(X) which can get hot, the first run will always have better results since it would have a cold start.

---

### Post by DanglingPointer on 2013-12-03
OS: 12.04 64bit
Driver: CCC 13.11v9.4Beta
GPU: R9-290X Uber Bios
CPU: i7 2600
RAM: 16GB DDR3 1333
GPUTest: x64 0.6.0

Results:
```
Module,Renderer,ApiVersion,Width,Height,Fullscreen,AntiAliasing,AvgFPS,Duration,MaxGpuTemp,ScoreGiMark,AMD Radeon R9 290 Series,4.3.12614 Core Profile Context 13.25.18,1280,720,NO,Off,71,60000,0,4273
Plot3D,AMD Radeon R9 290 Series,4.3.12614 Core Profile Context 13.25.18,1280,720,NO,Off,615,60000,0,36952
PixMark Piano,AMD Radeon R9 290 Series,4.3.12614 Core Profile Context 13.25.18,1280,720,NO,Off,18,60000,0,1089
PixMark Volplosion,AMD Radeon R9 290 Series,4.3.12614 Core Profile Context 13.25.18,1280,720,NO,Off,107,60000,0,6476
TessMark (X16/X16),AMD Radeon R9 290 Series,4.3.12614 Core Profile Context 13.25.18,1280,720,NO,Off,513,60000,0,30834
Triangle,AMD Radeon R9 290 Series,4.3.12614 Core Profile Context 13.25.18,1280,720,NO,Off,844,60000,0,50668
FurMark,AMD Radeon R9 290 Series,4.3.12614 Core Profile Context 13.25.18,1280,720,NO,Off,147,60000,0,8831
```

---

### Post by dannyboy79 on 2013-12-03
> **DanglingPointer said:**
> OS: 12.04 64bit
Driver: CCC 13.11v9.4Beta
 

i really want to know why you're able to run the Tessmark and Gimark and get a higher FPS than 59 or 60 and a score over 3,598. As you saw by my note no matter what my benchmarks always returned the same value similar to how glmark2 tops out at 59fps for me when I use the latest AMD beta driver.

Im at work, so i'll update the chart with your results later. AWESOME scores by the way

---

### Post by DanglingPointer on 2013-12-03
Mate, have you tried the usual suspects?...

In catalyst:
- ensure v-sync is off in the 3D section
- in the Monitor section, ensure tear-free is off

Are you using a digital monitor with a digitial D-DVI cable?  Is the monitor capable of a D-DVI cable (dual link is the best) [http://en.wikipedia.org/wiki/Digital_Visual_Interface](http://en.wikipedia.org/wiki/Digital_Visual_Interface)

Also on your monitor, check the information on the referesh rate. (usually a button on the monitor and some option on a menu).  Then compare it to what catalyst reports.  Perhaps some clues there.

---

### Post by dannyboy79 on 2013-12-03
> **DanglingPointer said:**
> Mate, have you tried the usual suspects?...

In catalyst:
- ensure v-sync is off in the 3D section
- in the Monitor section, ensure tear-free is off

Are you using a digital monitor with a digitial D-DVI cable?  Is the monitor capable of a D-DVI cable (dual link is the best) [http://en.wikipedia.org/wiki/Digital_Visual_Interface](http://en.wikipedia.org/wiki/Digital_Visual_Interface)

Also on your monitor, check the information on the referesh rate. (usually a button on the monitor and some option on a menu).  Then compare it to what catalyst reports.  Perhaps some clues there.yeap, that was it. I had tear-free enabled and v-sync enabled within the AMD Catalyst. Thanks for the heads up, I re-ran Gimark and Tessmark and now I get the real scores.

---

### Post by DanglingPointer on 2013-12-03
Fantastic! :)

Perhaps re-run the whole lot.

---

### Post by dannyboy79 on 2013-12-03
> **DanglingPointer said:**
> Fantastic! :)

Perhaps re-run the whole lot.
i did, they all turned out the same (within 1-3 points anyway)

---

### Post by Ranko Kohime on 2013-12-04
> **dannyboy79 said:**
> why don't you try intel's driver? isn't it just "intel"? i've heard great things about the latest Mesa driver. Admittedly I am very confused about intel gfx drivers as I have never needed to use them so I don't know what's the best intel driver to use.
As far as that goes, I've only ever heard of one Intel driver, the open source one.  (At least as far as is applicable to me)

The only proprietary driver I found from Intel was for a select few early Atom processors which were not covered by the open source driver.

If you've got information on this mythical "intel" driver, I'd be glad to hear it.  :)

ETA: i915 comes from the "xserver-xorg-video-intel" package, so we may be referring to the same driver.

---

### Post by jaime3 on 2013-12-16
Hi can you teach me how to post and run the program. I'm on Ubuntu 12.04 319.32 Nvidia driver. Nvidia Geforce GT 630M 2gb.

---

### Post by dannyboy79 on 2013-12-16
> **jaime3 said:**
> Hi can you teach me how to post and run the program. I'm on Ubuntu 12.04 319.32 Nvidia driver. Nvidia Geforce GT 630M 2gb.download the zip that i linked and run the command i listed and then simple double click gputest_gui.py to run the app

---

### Post by jaime3 on 2013-12-16
HP Envy DV7t-7200 with Intel Core i7-3630QM @ 2.40 Ghz
8 GB ram, Nvidia Geforce GT 630M 2GB Driver 319.32 OS
Ubuntu 12.04.3


[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Furmark698 [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]TessMarkx16  6212[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Gimark429[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]PixMarkPiano 168[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]PixMarkVolplosion 487
 
I wish I had my AMD gaming machine with ATI 6950 2gb result but sold it. [/FONT][/COLOR]

---

