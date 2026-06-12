---
title: "My WM Unity Benchmarking (Window Manager vs Window Manager)"
date: 2013-02-13
forum: Gaming &amp; Leisure
---

### Post by holastickboy on 2013-02-13
Hi!  The Unigine Heaven Benchmark 4 was released today, and it stresses your system more than ever (huge drop in my fps compared to the older version).  Because I was interested in seeing how the Window Managers competed with each other (particularly after the latest benchmarks from Phoronix didn't seem to focus on disabling desktop effects to improve performance), I thought I would do my own benchmarks, with all the gaming tweaks performed beforehand.  It's important to remember that these benchmarks have been done with system tweaking.  If you're serious about Linux gaming, you will probably put as much effort as I do into looking at driver installation, desktop tweaks, etc to improve performance.

**_My software setup:_**
Kernel: 3.5.0-23-generic x64
Ubuntu: Ubuntu 12.10 x 64
Nvidia-experimental 310 driver (much better performance than 304)

**_Hardware Setup_**
CPU: AMD Phenom II x4 840 3.4ghz (4 core)
RAM: 8GB DDR3-1333mhz RAM (running in ganged mode)
Video: Inno3d Nvidia GeForce GTX460 OC 1GB 256bit Gen 2 (running at 750/1900/1500)
Sound: SoundBlaster X-FI Extreme Audio

**_Window managers tested (fresh installs for each)_**
- Unity
- LXDE
- KDE (4.10)
- MATE
- Cinnamon
- RazorQT
- Gnome 3
- XFCE

**_Settings used for each:_**
- Desktop effects are turned off for all to ensure maximum performance
- Vsync/Vblank disabled to allow FPS to go above 60
- Adaptive mode disabled on Nvidia drivers to ensure maximum clock speeds are used at all times 
- swappiness setting at 10 to ensure no slowdown when loading textures (default is 60, which means that there is a lot of swap partition usage, significantly slowing performance due to excessive CPU usage)
- Full screen on all tests
- All Window managers had the latest, stable install as of 14th of Feb 2013 from the Ubuntu repositories (or other repositories for WM that are not in Ubuntu repositories)

**_Important Notes:_**
It's important to test Unity on 12.10, because you cannot disable desktop effects in full-screen games on 12.04 (it appears as if you can disable it, but there is a known bug which actually doesn't disable the effects, lowering benchmark results substantially).


**_Unigine Engine Settings:_**
Quality = High
AA = Off
Fullscreen = Yes
Res = 1920x1080
Tessalation= Normal
Stereo 3D= off
Multimonitor = Off


**_The Results:_**

***Unity***
FPS: 20.6
Min FS: 6.9
Max FPS 34.5
Score: 520

***XFCE***
FPS: 28.6
Min FPS: 12.5
Max FPS 51.5
Score: 720

***Cinnamon***
FPS: 21.9
Min FPS: 11.4
Max FPS 36.1
Score: 551

***MATE***
FPS: 22.4
Min FPS: 11.4
Max FPS 37.4
Score: 564

***KDE 4.10***
FPS: 29.0
Min FPS: 12.8
Max FPS 52.7
Score: 731

***GNOME 3***
FPS: 22.2
Min FPS: 11.4
Max FPS 36
Score: 558

***LXDE***
FPS: 29.1 
Min FPS: 13.0
Max FPS 52.8
Score: 732

***RazorQT***
FPS: 22.8
Min FPS: 11.6
Max FPS 30.1
Score: 574


**_Overall Rankings_**
1. LXDE (732)
2. KDE 4.10 (731)
3. XFCE (720)
4. RazorQT (574)
5. MATE (564)
6. Gnome3 (558)
7. Cinnamon (551)
8. Unity (520)


**_Conclusions:_**
I was totally surprised with the overall performance of the Window Mangers in this benchmark.  Notice the huge disparity in performance results from the top 3 to the rest of the pack?  The top 3 results were super close in performance, especially LXDE (which I had never tried before) and KDE 4.10 (which is a new version, again, that I have never tried before).  XFCE does a really good job to keep up with the top two, and can only be described as slightly slower (though in real life, you will never notice the difference).

I was surprised with the lack of performance of RazorQT.  It is running QT like KDE, and even uses the same KWIN engine as KDE, but is supposed to be lighter.  The actual desktop performance is very zippy, but it appears that by running this Window Manager as your default will nipple-cripple your gaming performance.

It was sad to see that MATE, Unity, GNOME 3 and Cinnamon were bad performers, especially Unity (which is the desktop that I am currently using).  While I find that all of these games don't make a noticeable difference in real life gaming, when it comes to benchmarking, they are noticeably slower (especially Unity).

The Unigine Engine is by far the most intense 3D rendering experience in Linux currently.  I cannot think of something that else that pushes your hardware to the edge (and for the most part, a lot of it would be unplayable for me unless I was running LXDE, XFCE or KDE according to the results).  I didn't test stuff like Quake 3, Team Fortress, or any other Linux game.  The problem with doing that is that they all perform so well, that it wouldn't make a difference in real life.  Unigine is a glimpse of the games we are going to see on Linux, and when my system is under stress, I wanted to see if changing my window manager would make a difference... and it did.

**_How will this change my desktop choice:_**
It won't.  Currently, none of the games I have on Linux really push the hardware to a point where I am making choices to improve my FPS.  I currently use Unity for my WM, and it serves its purpose very well.  As games improve in appearance, I might have to look at jumping ship to a better performing Window Manager.  That being said, if you are in a situation where you are struggling with current content, then you should probably look at LXDE, KDE or XFCE.  LXDE honestly surprised me with how zippy it was in general (windows opened and closed so quickly).  In the end, the choice is yours, and that's what makes Linux so great (and what Windows users will never understand about us).

---

### Post by bfromcolo on 2013-02-15
First thanks for the detailed report of your experiences.  

I recently assembled a system from spare parts to play with the Steam Beta (e5400 @ 3.2, and a stock GTX-260), and I have 12.04 Ubuntu running with the latest NVIDIA beta drivers. 

After reading your report I excitedly installed KDE expecting to see a 50% improvement in my Heaven benchmark.  But interestly enough I get identical scores with the options I chose:

Custom
Quality = high
Tesselation = moderate (in practice its disabled when the benchmark runs)
AA = x4
1680 x 1050
Full Screen

Whether under Unity or KDE I get the same FPS and score, and nearly identical min and max FPS (within 0.2 and you see that vary from run to run anyway).

FPS - 13.8
Min - 8.5
Max 21.4
SCore - 347

Not sure what this means relative to your results, but it appears at my resolution and settings the desktop environment does not seem to play into the score.

---

