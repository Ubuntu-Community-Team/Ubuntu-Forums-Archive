---
title: "kvm switch monitors"
date: 2005-07-12
forum: Desktop Environments
---

### Post by tuco on 2005-07-12
Hi,
  I did a search and can't quite find the thread with the answer. I recently installed kubuntu and did the same thing I did when I installed Ubuntu (Hoary verison), I direct connect my mouse, keyboard and monitor to my computer so that it would have the right settings. Then I would turn off my computer and plug my computer to the kvm switch. I did this method without issues with Hoary but when I tried it with Kubuntu, it would auto detect the kvm switch and lower my resolution to 640x480. Is there a ways to prevent it from auto-checking everytime at bootup?

---

### Post by jaranguren on 2005-07-12
Hi Tuco,  I actually have this same setup at work.  I have a 17" monitor I use at work that is connected to a desktop computer and my laptop via a KVM switch.  

I ran into this same problem before where when I switch my laptop video output to my 17" monitor I was only getting 640x480 or something like that.  I think what fixed my problem was setting the VertRefresh and HorizSync.  Below is an excerpt of my current xorg.conf.  It even works when I redirect output to a projector.

Hope this helps.

```

...
Section "Device"
        Identifier      "Intel Corporation 82830 1st"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "LCD"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "LCD Screen"
        Device          "Intel Corporation 82830 1st"
        Monitor         "LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "Monitor"
        Identifier      "CRT"
        Option          "DPMS"
        VertRefresh     48.0 - 100.0
        HorizSync       30.0 - 80.0
EndSection

Section "Screen"
        Identifier      "CRT Screen"
        Device          "Intel Corporation 82830 1st"
        Monitor         "CRT"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "CRT Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection
...

```

---

### Post by tuco on 2005-07-13
[QUOTE=jaranguren]Hi Tuco,  I actually have this same setup at work.  I have a 17" monitor I use at work that is connected to a desktop computer and my laptop via a KVM switch.  

I ran into this same problem before where when I switch my laptop video output to my 17" monitor I was only getting 640x480 or something like that.  I think what fixed my problem was setting the VertRefresh and HorizSync.  Below is an excerpt of my current xorg.conf.  It even works when I redirect output to a projector.

Hope this helps.

```

...
Section "Device"
        Identifier      "Intel Corporation 82830 1st"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "LCD"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "LCD Screen"
        Device          "Intel Corporation 82830 1st"
        Monitor         "LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "Monitor"
        Identifier      "CRT"
        Option          "DPMS"
        VertRefresh     48.0 - 100.0
        HorizSync       30.0 - 80.0
EndSection

Section "Screen"
        Identifier      "CRT Screen"
        Device          "Intel Corporation 82830 1st"
        Monitor         "CRT"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "CRT Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection
...

```[/QUOTE]


Thanks that did the trick.

---

### Post by BurningSnowman on 2005-09-10
[QUOTE=jaranguren]Hi Tuco,  I actually have this same setup at work.  I have a 17" monitor I use at work that is connected to a desktop computer and my laptop via a KVM switch.  

I ran into this same problem before where when I switch my laptop video output to my 17" monitor I was only getting 640x480 or something like that.  I think what fixed my problem was setting the VertRefresh and HorizSync.  Below is an excerpt of my current xorg.conf.  It even works when I redirect output to a projector.

Hope this helps.

```

...
Section "Device"
        Identifier      "Intel Corporation 82830 1st"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "LCD"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "LCD Screen"
        Device          "Intel Corporation 82830 1st"
        Monitor         "LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "Monitor"
        Identifier      "CRT"
        Option          "DPMS"
        VertRefresh     48.0 - 100.0
        HorizSync       30.0 - 80.0
EndSection

Section "Screen"
        Identifier      "CRT Screen"
        Device          "Intel Corporation 82830 1st"
        Monitor         "CRT"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "CRT Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection
...

```[/QUOTE]
Hi there,

Sorry for reviving a slightly old thread, but I just wanted to add that this solution worked for me too.

I'm new to Ubunutu, and just found this thread through a search, having had similar display problems due to getting a KVM.

I'm running the 'normal' version with Gnome rather than Kubuntu, but the xorg.conf advice still seems to have worked perfectly for me. 640x480 was really not a plausible way to run a desktop. Thanks very much, you've saved me from returning to Windows. :)

---

### Post by netbuz10101 on 2007-11-20
Hi. Ive got a similar problem, but im not using KBMs, i want the computer to not auto-detect the monitor on startup, as im trying to use VNC without any physical monitor attached (Im trying to spend no money on this, so no KVM). Any ideas? It will usually start up and ask if i want to run in low graphic settings. on a different machine i commented out all screen resolutions other than 1024, and it boots up fine without a monitor attached. (I cant remember if i told it to always start in low graphics mode). I tried doing the same to the machine in question and it still wont **start the way I want:**

*start up sans monitor
*Resolution set to 1024x768

Im heading out now, but im going to have it throw a fresh install of ubuntu 7.10

thanks in advance!

---

