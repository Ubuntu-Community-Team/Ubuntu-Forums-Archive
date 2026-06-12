---
title: "Screen Resolution Problem (New Dell Sys)"
date: 2007-08-18
forum: Dell  Ubuntu Support
---

### Post by arvadawest on 2007-08-18
Good day to you all,
I just received my new Dell XPS 410N system yesterday with Ubuntu desktop ed.  It is a duo core, 2gb ram, 250hd, and an nVidia GeFore 7300 LE 256mg video card.  I also have the 24" widescreen monitor.  The best resolution I can get is 1024x768.  Everything is really wide and not proportional.  I installed all the latest updates and patches.  I am a newbie to Ubuntu and I could really use the help so I can get a better resolution that is easy to read.  Thank you for your help.  -aw

---

### Post by arvadawest on 2007-08-18
Hi,
I know that no one has responded to this post, but I went to the restricted driver area and declicked the box for the nVidia GeForce 7300 and tried to reboot my system and I just get a white screen.  I am dead in the water.  Help on both my new system and the resolution problems??  Thanks. -aw

---

### Post by daageep on 2007-08-18
I assume the white screen means your computer booted everything except the video drivers correctly. At the white screen, you can press control + alt + f1 to get to another terminal. Log in and proceed

Here is a way to install the nvidia drivers through command line:

sudo apt-get install module-assistant && m-a prepare && m-a a-i nvidia && apt-get install nvidia-glx nvidia-settings

If all this worked then you have nvidia driver's installed (doesn't mean you're using the driver yet). 

Added "nvidia" to /etc/modules then sudo dpkg-reconfigure xserver-xorg. This will ask you a bunch of questions related to X. The important questions are choosing the graphics driver (choose nvidia obviously) and the resolution. For the resolution they will give you a list of possible resolutions. 

Roughly these instructinos mean: install module-assistant (helps you automatically install modules), prepare all the stuff needed in general to install modules, a-i means automatically install nvidia, install the other nvidia stuff, tell your comp to use nvidia instead of your other driver's.

Reboot after all this.

---

### Post by durrell on 2007-08-18
I had to manually configure my xorg.conf to get it to work on my widescreen monitor. First I did:

```
gtf 1440 900 70
```

And got this:

```
  # 1440x900 @ 70.00 Hz (GTF) hsync: 65.59 kHz; pclk: 126.98 MHz
  Modeline "1440x900_70.00"  126.98  1440 1536 1688 1936  900 901 904 937  -HSync +Vsync

```

Then put it into my xorg.conf like this:

```

Section "Monitor"
        Identifier      "Generic Monitor
        HorizSync       30.0 - 82.0
        VertRefresh     50.0 - 85.0
        Option          "DPMS"
        Modeline        "1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904$
        Modeline        "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904$
        DisplaySize     1440 900
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV44A [GeForce 6200]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
        Depth           24
        Modes           "1440x900_70.00" "1440x900_60.00"
        EndSubSection
EndSection

```

Of course you'd need to make sure you do it for your resolution, refresh rates, and identifiers. That's how I got it to work though.

---

### Post by arvadawest on 2007-08-18
Thank you both for your replies.  But before you both replied, I reinstalled the OS with the disk that came with the system and it found the drivers and all is well.... But....

please my posting on "when rebooting on ubuntu desktop ed" this is so strange.  When I shutdown and startup it is ok, but when I tell it to "restart" it goes to the screen where it removes the orange bars, but when it tried to go back to the screen (booting up) by adding the bars, it stalls.  Very strange.  Thanks.

---

