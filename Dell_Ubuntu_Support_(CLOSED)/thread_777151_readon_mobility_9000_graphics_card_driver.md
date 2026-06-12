---
title: "readon mobility 9000 graphics card driver"
date: 2008-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by archon123 on 2008-05-01
I just installed the ubuntu 8.04 on my dell inspiron 600m with a readon mobilty 9000 graphics card. The driver for my graphics card isn't working. I tried enabling a restricted driver through system->administration->hardware drivers but the driver wasn't listed.

How can I install a driver for my graphics card?

---

### Post by shae on 2008-05-01
The best supported driver for a Radeon 9200 and below is the open source driver.

---

### Post by archon123 on 2008-05-01
Ok, when I try to enable visual effects I get a message that desktop effects can not be enabled. Doesn't this usually mean that the driver for the graphics card isn't working? Could there be another reason for this?

Thanks

---

### Post by v.proch on 2008-05-23
I have the same problem with this graphics card on Dell Latitude D600 with 8.04 (with 7.10 everything was ok).
Has anybody solved that problem? I have found lots of advices on the interrnet but none really worked.

---

### Post by Kevbert on 2008-05-23
I have an Acer laptop with the 9000.  I believe your problem is possibly that you need to enable a software source (I'm not sure which one).  I have all Ubuntu software boxes ticked, you shouldn't need backports enabled.  I'm not using a restricted driver.

---

### Post by Kevbert on 2008-05-25
Have a look at this:
[http://forlong.blogage.de/article/pages/Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check")
It may be that your card has been blacklisted. Compiz-check will sort that out.

---

### Post by Jeroen Wit on 2008-05-26
At last everyting is working now for Dell D600 radeon rv250 driver !!!
Edit your compiz-manager. 

/etc/xdg/compiz$ sudo nano compiz-manager

add this line:
SKIP_CHECKS="yes"

My xorg.conf file looks like this :


 Section "Device"
        Identifier "Radeon 9000"
        Driver "ati"
        BusID "PCI:1:0:0"
        Option "GARTSize" "64"
        Option "MergedFB" "off"
        Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
        Identifier "Generic Monitor"
        Option "DPMS"
        HorizSync 30-70
        VertRefresh 50-160
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device "Radeon 9000"
        Monitor "Generic Monitor"
        DefaultDepth 24
        SubSection "Display"
                Depth 24
        Virtual 1920 1440 
                Modes "1400x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Option "AIGLX" "true"
        Identifier "Default Layout"
        Screen "Default Screen"
        InputDevice "Generic Keyboard"
        InputDevice "Configured Mouse"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection



You can Copy and Paste this text in to your xorg.conf file from
 Section "device"

my resolution is 1400x1050 !!
color depth 24 bit !!
glxgears 3695 frames in 5.0 seconds = 738.948 FPS

I hope this will help everybody with radeon mobility 9000 card.

My regards,

---

### Post by Rocket2DMn on 2008-06-15
I hope this isn't too late to help:
I have this laptop and this video card, and can tell you that it is too old to support the restricted fglrx video drivers.  If you ever did try to install them, run
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Check this link for allowing desktop effects - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

