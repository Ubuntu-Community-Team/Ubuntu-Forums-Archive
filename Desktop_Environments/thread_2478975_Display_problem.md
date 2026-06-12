---
title: "Display problem"
date: 2022-09-10
forum: Desktop Environments
---

### Post by jgw on 2022-09-10
I have a computer that displays on a 65" TV.  My current system display says 1920x1080 (its not).  When I first set up my display I had a much different display (3840x2160 (16:9) which is also the actual screen size!) which was better.  What happened, quite long ago, is that my display got changed to the 1920x1080 settings and the display was filling the machine so I let it be.  Now, however I am having a problem.  Oh, here is a xrandr report:

```
:~$ xrandr
Screen 0: minimum 320 x 200, current 3072 x 1728, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 3072x1728+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1920x1080     60.00*+  50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   2880x576      50.00  
   1600x900      60.00  
   2880x480      60.00    59.94  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1440x576      50.00  
   1024x768      75.03    70.07    60.00  

```

```
lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. AMD RS780/RS880 PCI to PCI bridge (int gfx)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000]
01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS780 HDMI Audio [Radeon 3000/3100 / HD 3200/3300]
02:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)

``` 

My physical display from system profiler:
Resolution	        	3072x1728 pixels
OpenGL Renderer		AMD RS780 (DRM 2.50.0/5.15.0-47-generic, LLVM 13.0.1)
X11 Vendor		        The X.Org.Foundation

Please note the Resolution.  It is not the same as shown in the settings!  The problem is, I think,  that the computer really doesn't know the size of the screen as all my stuff goes through a receiver (denon avr-s530bt av surround sound receiver) so my sound is handled correctly (5.1 speakers).  So, the computer is getting the screen size from the receiver.   I use a program called Kodi to display movies and that was the problem.  When I am watching a movie there is a switch the display to one big picture without anything else on the screen.  When I do that kodi gives me a display of the movie in a box about 1/3 of the size of the screen.  I am not saying that all the above is the problem but I am posting this in the hope that somebody might have an thought about all of this.  

This paragraph explained a problem which I caused.  I went and messed with the display in Kodi and, in turn, Kodi gifted me with what I did and that caused the problem.  I was zooming the partial display and, evidently, my display stuck at that one with a little zoom and my display thought the pages were to big (I think).  I am now back and the problems below are no longer happening.  Oh, I almost forgot.  My screen is currently not behaving as well.  The top of this page is going away and I have to take my mouse and move it over the top of my screen to get it back.  I am using Firefox but it has never done that before and now I have to hunt for what I am working on!  I just tried to post on the Kodi forum but I had to stop because my screen was behaving poorly.  My solution for getting the top back is going to the right side and pushing the mouse to the top of the page and then pulling down from the middle and then the real top appears.  This is very strange. 

I just went to system settings and changed my display.  I had the display set to "Adjust to TV" and turned that off.  Now my top still goes away but to get to the top I simply move my mouse up to the top and it appears!  If I could figure out how to make the 3840x2160 (16:9) size I suspect my problems might take flight. 

Thoughts?

---

### Post by MAFoElffen on 2022-09-10
Many thoughts. But first could you run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") and post the URL of the report it generates? I know you provided lots of hardware details. I applaud you for that. The graphics sections in that report get a bit more detailed. so people do not need to look up as much (In a different format.)

In the meanwhile, I have some questions on what you did post.

1.) In your lspci output, I see AMD Radeon 3000 listed twice as 01:05.0 and 01:05.1. Can you explain that in your own words. Do not be afraid of being too technical or not. 
2.) I'm curious that your xrandr output says that the display connected to is only 1080P(???) You said it is 4K right? Did  you happen to change cables lately? (Like a value cable or something?) And the command should be 
```

xrandr -q

```
Does it show any different from the Grub CLI if you do "videoinfo" ?

OH DANG... I reread everything. (Instead of skimming over it.) Well... I can't say for sure what is going on for sure, (without more info) but I will try. I've only supported the Linux Graphics Layer for a bit over 15 years...

High end GPU's like NVidia and AMD, they pole the connected ports to see what the capabilities of the connected displays are... So if you use some type of AV switch (that includes the video) then the GPU see's the middleman switch capabilties, instead of the display, on the other side of that middleman. This happens a lot with KVM Switches. But what you described in your AV switch is just audio right? That would effect the audio part of your GPU, but not the Video. On hardware switches (as a middleman), I declared what is on the other side. So that it just comes up with those settings on that port.

On a software switch, playing as a middleman, once the software middleman is unloaded, the the GPU should be able to see the connected display again. You HDMI cable is directly connected from card to display right? Good quality cable?

Another thing you didn't mention, is if you are using kernel KMS as a graphics helper during boot...

---

### Post by jgw on 2022-09-11
Thanks for the reply!

This is my second try at writing this, I decided to look at something and wiped it out.  My main problem is that I have been doing computers for over 50 years and now on the down slope.  Not an excuse but a fact.  Where I actually do stuff I use a KVM.  My receiver (AV) transfers everything from the computer, programs, etc.  As far as I can tell its setup correctly and I REALLY hope I don't have to get into that one. Its a Denon and Denon has lots of support so, if I do, I do.  In other words, the receiver/AV send ALL information to the TV.  I have had that receiver for several years and its worked fine (until I mess it up)

The receiver:  denon avr-s530bt av surround sound receiver

I never knew that ubuntu had a paste park and have been using pastbin for years.  You will find the report you wanted at [https://paste.ubuntu.com/p/bc6yPVWrz4/](https://paste.ubuntu.com/p/bc6yPVWrz4/)  

Thanks again!

---

### Post by jgw on 2022-09-13
I want to give appreciation for the replay and now I know about the system info script which will come in handy.  Thanks again!

OK!  I have fixed my problem.  My solution was that  didn't have my input of the receiver in the right input (there are something like 8 of them).  I swear I had read the directions, and tried them all over the years, about 100 times.  This time, however, I plugged it in the right plugin and, suddenly, my system had the size of my TV!  My problem has gone away!

---

### Post by MAFoElffen on 2022-09-15
Glad that it is working again. MY NVidia cards are like this. Very sensitive to which ports are plugged in first, to what is the primary display.

LOL. Me too. About to retire. Over 32 years as an IT Professional. Have forgotten enough that I brush up every once in a while. The basic concepts are the same, with a few evolved twists. LOL

---

### Post by jgw on 2022-09-15
Thanks for your thoughts and reminding me to set this one as 'solved" (thought I had - wrong again!)

This was an exercise in just not paying attention.  I have the manual, but the remote has choices and the buttons are clearly marked.  I was plugged into "dvd", the one I needed was "TV, Media"  Both were clearly marked.  When I used to code I would have known better because that was the good old days when I did pay attention.  Guess those good old days are really gone. <g>

thanks again!!

---

