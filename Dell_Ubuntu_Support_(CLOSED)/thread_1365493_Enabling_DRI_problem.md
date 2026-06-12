---
title: "Enabling DRI problem"
date: 2009-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by d13k on 2009-12-27
Hello. My problem revolves around me not being able to enable DRI in order to play World of Warcraft.
I followed guide from: [LINK]("http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine")

And it was all going good until I used command to check if my DRI is enabled.

I used the command: 
```
glxinfo | grep rendering
```

The result should have been something like:
```
direct rendering: Yes
```

Instead I got:
```
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```

Afterwards I extensively used Google and Ubuntuforums to find solution for my problem but unfortunately everything I did was unsuccessful.

I tried to change my xorg.conf file located in etc/X11 but I found that it doesn't exist there and read some posts saying that xorg.conf is obsolete in 9.10 but that it can still affect the system if present. 

I also tried installing driconf but that didn't work too.
The only thing I successfully managed to install was Wine.
First time I ran WoW using Wine the picture was very "messy" and after I tried to fix it, all I get is a black screen.

My system:

Dell Inspiron 6400
Ati Radeon X1400 Mobility
Ubuntu 9.10 (Karmic Koala)

---

### Post by gradinaruvasile on 2009-12-27
Unfortunately your card is not supported anymore by Ati in the Linux drivers. This means you have to use the opensource Ati driver which is not at par with Ati's restricted drivers...

On the other hand, you should have direct rendering with the opensource drivers. But i heard that there are some problems with karmic's radeon drivers.

Look here for newer drivers, maybe they can help...

[https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)

---

### Post by d13k on 2009-12-28
So I tried to install Open Source driver.
I followed guide that can be found on: [LINK]("https://help.ubuntu.com/community/RadeonDriver")
Since I didn't have xorg.conf file I created new one adding specifications for my card/monitor(Didn't add part with HorizSync and VertRefresh since I didn't know correct values for my monitor):

```
Section "Device"
        Identifier      "Radeon X1400 Mobility"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon X1400 Mobility"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x900" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
```

When I logged in like this Ubuntu told me that I'm running low graphics.
Then I decided to open up terminal and see what's going on with my graphic cards settings.

For command:
```
glxinfo | grep vendor
```

I got:
```

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

```

In the part where now is Mesa Project there was before DRI r300 if I recall corectly.

And for the direct rendering surprisingly I got affirmative answer:

```
direct rendering: Yes
```

Unfortunately my WoW problem persists, all I see is still a black screen.

---

