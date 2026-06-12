---
title: "GX260 Adding AGP nvidia card troubles"
date: 2008-02-26
forum: Dell  Ubuntu Support
---

### Post by MarkFowler on 2008-02-26
:frown:
I have a Dell gx260 computer with gutsy gibbon installed. It installed and updated just fine. I have all the current updates. I am trying to install an AGP video card to replace the onboard Intel graphics. I have 3 different cards and none of them work. The machine appears to boot but I see nothing on the monitor.

Any help would be appreciated.

:popcorn:

---

### Post by Sam Lars on 2008-02-26
Does anything appear on the monitor at any point?  Do you at least see the Ubuntu loading bar screen?

---

### Post by MarkFowler on 2008-02-27
No, I see nothing at all. When I move the cable back to the onboard Intel graphics is works fine. I haven't used the cards in awhile but I find it hard to believe that all 3 would be dead at the same time. Also the machine acts like it is booting up normally. I hear the drive spin and all the other noises as usual.

Thanks for the reply

---

### Post by Sam Lars on 2008-02-27
So does it boot to the Intel regardless?
Have you gone into the BIOS to tell it to not use the onboard graphics?

---

### Post by MarkFowler on 2008-02-27
The only setting in the BIOS is to "AUTO"matically use the AGP slot if a card is there or to only use the integrated video. I have it set to "AUTO".

With this setting and an AGP card in the slot I get no Video at either the AGP card or the onboard video. If I remove the AGP card, I can get the video on the Intel onbard graphics again.

Dell seems to like to make simple things hard.

Thanks again for your suggestions.

---

### Post by Sam Lars on 2008-02-29
So, just to clarify, does the issue seem to be that the computer boots to the onboard Intel straight from the BIOS, whether the card is in or not?

---

### Post by jaakan on 2008-03-02
I think you have to check your bios settings after you add your AGP card.



[http://support.dell.com/support/edocs/systems/opgx260/en/ug/advfeat.htm#1101564](http://support.dell.com/support/edocs/systems/opgx260/en/ug/advfeat.htm#1101564)


* Primary Video Controller — When video is integrated on the system board, the options are Auto (default) and Onboard.

When an AGP card is used, the options are AGP (default) and Auto.

---

### Post by MarkFowler on 2008-03-03
Great jaakan. I should have caught that. I am at work will try that when I get home. 
Thank you so much for your time.

---

### Post by MarkFowler on 2008-03-03
Well jaakan, that helped but not a lot. I now see the video as it boots. It seems to get through the portion where the word UBUNTU is displayed on the screen witha progress bar. The progress bar seems to reach the right side then the screen goes blank with a blinking cursor down 4 or 5 lines on the left hand side.. I could not get it to do anything,. I ended upu shutting down the computer and restarting. Same thing three different times. Pulled the AGP card out and set the setting back to normal and it worked. I am typing this on the cmoputer now. I did see something about IRQ used by the video card. I may play with those settings. Not much to loase at this point.

Thank you so much for the ideas.

---

### Post by Sam Lars on 2008-03-04
To have a better idea about why it's failing...
Post your xorg.conf
Get the computer to boot with the card to the cursor screen, then boot it without, and post /var/log/Xorg.0.log.old

---

### Post by jaakan on 2008-03-04
I'm going to guess you going to need to boot to "recovery mode" aka single user mode

cp /etc/X11/xorg.conf /etc/X11/xorg.conf_old ( make a back up )

vim or vi /etc/X11/xorg.conf ( edit )

to force save in VI or VIM hit 
" : " then enter
" wq! " then enter

w = write
q = quit
! = force

then you look for something like this 

Section "Device"
        Identifier      "nVidia Corporation NV44A [GeForce 6200]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

set the driver to "vesa" or "vga"

to get the busid run lspci

which will give you an output like the following

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by MarkFowler on 2008-03-06
Thanks for the last two ideas. I will be out of town for several days. I will try both suggestions when I get back.  Again thanks for your time  and the suggestions.

---

### Post by luvit on 2008-03-13
> **MarkFowler said:**
> :frown:
I have a Dell gx260 computer with gutsy gibbon installed. It installed and updated just fine. I have all the current updates. I am trying to install an AGP video card to replace the onboard Intel graphics. I have 3 different cards and none of them work. The machine appears to boot but I see nothing on the monitor.

Any help would be appreciated.

:popcorn:
I have pure success, heres what I did:

I downloaded the alternate ISO and it solved my video problem on my GX260.  I now can leave my BIOS at 256MB Video RAM _and_ have 1024x768 75Hz refresh rate.

For reference I viewed my display settings:
  System>Administration>Screens and Graphics - Graphics Card Tab - Driver: intel Experimental modesetting driver for l...

Before I installed Ubuntu I upgraded my BIOS which may have contributed to my fantastic video success. You can get the BIOS update from my blog. Lemme Know!

---

### Post by MarkFowler on 2008-03-17
Thanks for all the help. I figured since I really hadn't installed much software yet I would just reinstall the OS with the AGP card all setup before I started. Worked like a charm. Didin't even need the alternative version. I have used windiws since version 3.1 but have just started using Ubuntu about 3 weeks ago. Sometime in the future I will have to learn about this problem but for now I am satisfied.

Thanks again for all the suggestions. 

The Ubuntu forums folks are amazing!

---

