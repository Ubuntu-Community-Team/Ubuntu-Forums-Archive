---
title: "Just installed.  Have a few questions."
date: 2005-09-16
forum: Desktop Environments
---

### Post by snoochems on 2005-09-16
Hi all.
I've just installed the x64 version of Hoary on my main home PC.  I've used Ubuntu before on my laptop, so I am a little familar with this OS.  

Anyways, I've booted up, and noticed that my resolutoin for my LCD screen is stuck at 1024x786 or lower.  It's natice 1280x1024, so everything looks blury and crappy.  

I've entered in the terminal:

sudo apt-get update
sudo apt-get upgrade

but this hasn't fixed the problem.  What is the problem?

I've got a ATI video card, so i went over to ATI and downloaded the linux driver, but i'm confused as to which one to get.  And how do you install it?

One other thing.  This PC has 1.5GB of RAM.  If the system monitor is correct, i'm using nearly 800MB of this RAM just having firefox open.  Surely this isn't right?!  THis is (far) worse than windows x64's 300MB+ usage.  What have i done wrong?

Thank you very much for your help.

---

### Post by snoochems on 2005-09-16
Oh, and one more thing that i would like help with... 

can UBUNTU run dual monitors.  I have two monitor connected ATM that work fine in windows as dual screen, but in UBUNTU, both monitors just mirror each other.

I don't think i can live/work without dual monitors, so please help me.

---

### Post by snoochems on 2005-09-17
bump

---

### Post by Gary Powers on 2005-09-17
Snoochems, you can edit the xorg.conf file (/etc/X11/xorg.conf) and add your desired setting to it.

First of course, back it up (cp xorg.conf xorg.conf_backup), then open gedit from the command line and don't forget sudo, then down in the device section (i recall) you will find the settings.  Just add 1280x1024 to each line.  You may have to reboot for this to become available.

Gary

---

### Post by Lord Illidan on 2005-09-17
[QUOTE=snoochems]Hi all.
I've just installed the x64 version of Hoary on my main home PC.  I've used Ubuntu before on my laptop, so I am a little familar with this OS.  

Anyways, I've booted up, and noticed that my resolutoin for my LCD screen is stuck at 1024x786 or lower.  It's natice 1280x1024, so everything looks blury and crappy.  

I've entered in the terminal:

sudo apt-get update
sudo apt-get upgrade

but this hasn't fixed the problem.  What is the problem?

I've got a ATI video card, so i went over to ATI and downloaded the linux driver, but i'm confused as to which one to get.  And how do you install it?

One other thing.  This PC has 1.5GB of RAM.  If the system monitor is correct, i'm using nearly 800MB of this RAM just having firefox open.  Surely this isn't right?!  THis is (far) worse than windows x64's 300MB+ usage.  What have i done wrong?

Thank you very much for your help.[/QUOTE]

Whoa, there, are you sure about 800 mb of RAM with just firefox open? I mean, I have never seen something like this before... Windows on my 32 bit pc takes only 192 mb, and that with firefox, anti virus, anti spyware and firewall running.. and Ubuntu takes that much too, on the same machine.. Firefox is not a big app.

---

### Post by lisje on 2005-09-17
[QUOTE=snoochems]Hi all.
I've just installed the x64 version of Hoary on my main home PC.  I've used Ubuntu before on my laptop, so I am a little familar with this OS.  

Anyways, I've booted up, and noticed that my resolutoin for my LCD screen is stuck at 1024x786 or lower.  It's natice 1280x1024, so everything looks blury and crappy.  

I've entered in the terminal:

sudo apt-get update
sudo apt-get upgrade

but this hasn't fixed the problem.  What is the problem?

I've got a ATI video card, so i went over to ATI and downloaded the linux driver, but i'm confused as to which one to get.  And how do you install it?

One other thing.  This PC has 1.5GB of RAM.  If the system monitor is correct, i'm using nearly 800MB of this RAM just having firefox open.  Surely this isn't right?!  THis is (far) worse than windows x64's 300MB+ usage.  What have i done wrong?

Thank you very much for your help.[/QUOTE]
 you can alter you resolution options in this file:
/etc/X11/xorg.conf

---

### Post by snoochems on 2005-09-17
Thanks i'll try that next time i reinstall Ubuntu.  

I tried some guides here to install the ATI drivers, but managed to break my ubuntu install.

How do i do this?

---

### Post by pbrockway2 on 2005-09-17
Hi,

I'd also like to change the resolution.  Following the comments here I backed up /etc/X11/xorg.conf, added the following lines
```
Section "Screen"
  DefaultDepth  16

  SubSection "Display"
    Depth  16
    Modes "1280x1024"
  EndSubSection

```
and restarted.

However there was no change to the resolutions presented by System->Preferences->Screen Resolution.

Did I say the right magic words to xorg.conf? (There is no "Modes" section).  Any help would be appreciated.  Thanks.

---

### Post by Xian on 2005-09-18
What is in your 'Section "Monitor"' heading of the xorg.conf file? And why choose a DefaultDepth of 16? Most people select 24 but perhaps there is a reason here.

---

### Post by pbrockway2 on 2005-09-18
The "Monitor" section is:
```
Section "Monitor"
  Identifier  "Generic Monitor"
  Option  "DPMS"
  HorizSync  28-49
  VertRefresh  43-72
EndSection

```

The only reason for the 16 was so it would resemble the way the monitor is setup for Windows. (Ie, I know it can function that way).    I've now changed it back to 24.

---

### Post by cutOff on 2005-09-18
The "Screen" section should be like that (for a 1024x768 resolution)

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV17 [GeForce4 MX 440]"
        Monitor         "Monitor generico"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
EndSection
```

---

### Post by pbrockway2 on 2005-09-18
Everything is fine now. Gracias Xian, cutOff.

---

### Post by Xian on 2005-09-18
What is the output of this command:

$ xrandr

---

