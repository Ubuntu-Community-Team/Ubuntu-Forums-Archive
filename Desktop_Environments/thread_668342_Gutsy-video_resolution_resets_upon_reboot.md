---
title: "Gutsy-video resolution resets upon reboot"
date: 2008-01-15
forum: Desktop Environments
---

### Post by djjosephk on 2008-01-15
I've Gutsy installed on an Aspire with a Centrino chipset and the video resolution resets itself from 1280x800 to 1024x780 every reboot. I have noticed that i doesn't happen when I restart X but only when I do a full shutdown. Any ideas?

---

### Post by SantinoC on 2008-03-06
i am having this same problem, only on a restart when the computer has been shutdown.

specs:

p4 2.53ghz
1gb ram
ati 9800 pro
Ubuntu gutsy
fglrx, compiz.

in my xorg.conf i deleted all the other resolution options so it only displays "1680x1050"

---

### Post by SantinoC on 2008-03-08
bump

---

### Post by SantinoC on 2008-03-08
i have figured out the problem.

in the CompizConfig "General" section the Display was set to 1600x1200, so im assuming everytime compiz was being initialized for the first time it was resetting the screen resolution, since setting it to the proper resolution(in my case 1680x1050) it loads perfect now, and i officially have my linux box setup exactly how i want it.

Now if i can only get MonoDevelop to stop crashing on me then id be truly set.

---

### Post by kuntergunt on 2008-03-13
I have a similar problem.
When I set my screen resolution to 1680x1050@60, everything seems ok.
When I reboot the screen has changed a little, there is a couple of pixels missing on the left and the right side and it's little bit blurry.
I check screen resolution in the preferences it says 1680x1050@60.
When I change to another resolution, apply and confirm, and then back to 1680x1050 the screen is perfect.
...until I reboot!

I use compiz,  ATI X1250 grapics, ATI fglrx driver,  Benq FP222WH flatsceen.

This is the monitor and screen section in xorg.conf:
Section "Monitor"
        Identifier      "BenQ FP222WH"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1680x1050"
        Horizsync       30.0-82.0
        Vertrefresh     56.0 - 76.0
  modeline "640x480" 30.60 640 656 664 816 480 482 483 505  # 31 MHz, 37.5 kHz, 74.3 Hz
  modeline "800x600" 47.92 800 824 848 1024 600 602 604 632  # 48 MHz, 46.8 kHz, 74.1 Hz
  modeline "1024x768" 78.70 1024 1056 1088 1312 768 770 773 808  # 79 MHz, 60.0 kHz, 74.2 Hz
  modeline "1152x864" 99.36 1152 1192 1240 1472 864 866 869 909  # 99 MHz, 67.5 kHz, 74.3 Hz
  modeline "1280x1024" 131.20 1280 1320 1384 1640 1024 1026 1030 1078  # 131 MHz, 80.0 kHz, 74.2 Hz
  modeline "1680x1050" 142.68 1680 1736 1816 2152 1050 1052 1055 1105  # 143 MHz, 66.3 kHz, 60.0 Hz
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "BenQ FP222WH"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1680    1050
                Modes   "1680x1050"     "1280x1024"     "1152x864"      "1024x768"      "800x600"      $
        EndSubSection
EndSection



Is the configuration wrong? Is the driver buggy?
Any ideas?

kuntergunt

---

