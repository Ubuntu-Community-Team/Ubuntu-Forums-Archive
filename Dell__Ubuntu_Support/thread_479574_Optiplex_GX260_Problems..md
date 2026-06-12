---
title: "Optiplex GX260 Problems."
date: 2007-06-20
forum: Dell  Ubuntu Support
---

### Post by reed026 on 2007-06-20
Hello.

I am quite a new Ubuntu user, so I don't understand a lot of how this works. However, I have tried my best going through forum articles and the documentations however I can not find an answer to my problem.

Problem #1
Using the Live CD I have done both the Start / Install and Install in Safe graphics mode. 
Everything works fine during installation until the after the 1st load screen. Basically the screen goes black with an underscore making that continues blinking. It does this on both.

So I figured I would try the alternate CD.  Which leads me to my next problem.

Problem #2
Booting from alternate CD with VGA set at 1280 x 800 (and smaller resolutions)
I get through all of the load screens until where it asks to choose the resolutions. 
I leave it as it came, selecting the bottom three 1280 x600 800 x600 and another I can not remember.
After I hit continue it starts the next load screen and stops at 6% saying "Please Wait" I let it sit there for 20-30 minutes and rebooted. I attempted this 3 times with the same error. 

My comp specs:
Dell Optiplex GX260
512mb of RAM
120GB HD (100GB partioned for WindowsXP)
30GB HD ( Trying to install Ubuntu on this HD for dual boot)
Radeon 7000 Graphics Card x 2 (4 monitors)

I'm honestly trying to step away from windows..

I'm curious as if it is my graphics card?

---

### Post by reed026 on 2007-06-20
I may have figured out my problem, but I have not attempted a new installation.

I checked into my bios and realized that I was running A00 when there was an A09 update available.
Also downloading the VBios update for my Radeon VE 7000,  and will attempt to reinstall after that has completed.

---

### Post by reed026 on 2007-06-20
Now I get to another error. The Live CD still will not boot, and the alternate hangs at 6% on "Select and Install Software" - "Installed xresprobe"

---

### Post by reed026 on 2007-06-21
Alright, I downloaded Xubuntu today as the alt CD and attempted to install. As soon as it gets past xorg install it goes into please wait and freezes. 

There is nothing wrong with the CD, as I have done the testing before each install.

---

### Post by reed026 on 2007-06-22
Well, this would be my final update on the matter I presume. 

Last night I had to bright idea to pop ubuntu into another computer I had. When i did, the Live CD worked fine. So, I figured I could just pop my HD in, install Ubuntu, then pop it back into my shell.
Didn't work like that.

So I decided to try the alt cd one more time and just go to bed, and that's what I did. I configured it up until when it asks for the screen resolutions and went to bed. I wake this morning and it is properly installed and running.

Now, my only problem is, I need a larger screen resolution. Ubuntu says it's 1024 x 758 but it looks more like 800 x 600.

I'm glad that I can dig into developing PHP again, but I have never this hard of an install. ( I have 2 machines running Fedora ) 

Need to look into the repository so I can grab WINE to run some windows programs for me though :/

---

