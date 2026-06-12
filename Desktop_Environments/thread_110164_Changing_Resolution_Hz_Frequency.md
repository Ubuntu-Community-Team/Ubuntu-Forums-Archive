---
title: "Changing Resolution Hz Frequency"
date: 2005-12-30
forum: Desktop Environments
---

### Post by SadaraX on 2005-12-30
Hello. I recently re-installed Ubuntu onto my system, using all my previous video card drivers and settings. Before I was able to run my monitor successfully at the resolution of 1280x960 at 85Hz. However, now it only gives me the option of 60Hz. How to I add the option of 85 Hz into the resolution menu? I know it will work if I can only get the option.

System Spec's:
> 
Motherboard: EPOX EP-9NPA+Ultra NF4 ULTRA RT

Video Card: Geforce 6800GT 256MB DDR PCI Express x16 Video Card - ASUS EN6800/TD/256
	Type VGA XFX|
	Model PVT45GUDF3

Sound: Built-in Sound on EPOX board - NVidia CK084

CPU: AMD Athlon 64 X2 4200+ Manchester 2000MHz FSB Socket 939 Dual Core
	Processor Model ADA4200BVBOX

RAM: CORSAIR XMS 1GB 184-Pin DDR SDRAM DDR 400 (PC 3200) Unbuffered System
	Memory Model CMX1024-3200C2PT
	Model #:CMX1024-3200C2PT

Kernel: 2.6.12-9-686-smp

Distro: Ubuntu/Kubuntu 5.10, KDE 3.4.3.


---

### Post by rjwood on 2005-12-30
Hi and welcome back,
there have been many, many threads on this issue. I don't have your answer but, I think if you search 'screen resolution' you willprobably find it.   Good luck!!

---

### Post by chrisndebb on 2005-12-30
Good morning folks. I found this thread useful but be sure to KNOW your monitor's specs. I guessed and got into trouble with X. 

[http://www.ubuntuforums.org/showthread.php?t=109258&highlight=refresh+rates](http://www.ubuntuforums.org/showthread.php?t=109258&highlight=refresh+rates)

Good luck

---

### Post by whitesox on 2005-12-31
you could also try: ```
sudo dpkg-reconfigure xserver-xorg
```
and change your refresh rate when the wizard gets to that part.  Chose the medium option, and then choose your monitor settings, its very easy.
this is (border-line) safer, because if it is a bad refresh rate, and X won't start, you can always run it again from the terminal and not have to deal with vi.

---

### Post by yaztromo on 2006-01-02
Do some research on how to put modelines into X. And then use this site. It has never failed for me:

[http://www.dkfz-heidelberg.de/spec/linux/modeline/index.html.en](http://www.dkfz-heidelberg.de/spec/linux/modeline/index.html.en)

I needed a 70hz 1280x960 screen and now my xorg.conf looks life this:
```

Section "Monitor"
        Identifier      "NEC FE770"
        Option          "DPMS"
        Modeline "1280x960" 125.14  1280 1344 1496 1784   960  960  963 1002
        Modeline "640x480" 41.26   640  664  720  808   480  480  482  510
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor         "NEC FE770"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```

---

### Post by tirofiban on 2006-01-06
Hi,

I hope this post helps someone. I had the opposite problem. I was stuck in 85Hz frequency with a new monitor that needed no more than 75Hz (60 Recommended).

Card: ATI Radeon 8500 All-in-Wonder; Monitor Rosewill R912E.

I added Horizontal and Vertical info to xorg.conf. I even added a modeline. I used configuration editor to set the default resolution. I also tried the dpkg-configure. Nothing worked. 

I was able to change the resolution and frequency with the previous monitor. I even reinstalled Ubuntu. Then I tried a Knoppix live CD. Each time I was stuck with 85 Hz.

I changed the input cable from DVI to VGA (with a DVI-toVGA adapter on the ATI card) and guess what happened? I could pick any valid resolution or frequency for my new monitor.

As near as I can tell, the monitor kept telling Ubuntu to use 85Hz at startup and Linux went for it, overwritting my settings. (With a VGA cable, the monitor can't give the computer much detail regarding resolution and frequency.)
 
Interestingly enough, this monitor comes with software for Windows or Mac, in case the computer has difficulty recognizing the monitor. Now I know why a new 19" LCD was only $221! Oh, well it works now.

Linux is more fun on 19 inch monitors!

---

### Post by steelfanatic on 2006-04-04
Any other fixes for this monitor beside changing the cable? I like DVI :)

---

