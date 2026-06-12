---
title: "n610c 1400x1050 resolution"
date: 2006-09-24
forum: Desktop Environments
---

### Post by jrobinson5 on 2006-09-24
I've got a Compaq n610c laptop. The native resolution is 1400x1050, but the highest listed in the resolution window is 1024x768. How do I get 1400x1050?

---

### Post by bigken on 2006-09-24
in the terminal type sudo dpkg-reconfigure xserver-xorg and use the space to select your screen resolutions ;)

---

### Post by jrobinson5 on 2006-09-25
I did it and answered the default to everything except the part where it asks for the resolutions, where I checked 1400 and unchecked everything else. Nothing happened.

---

### Post by andypaxo on 2006-09-25
This [webpage on setting up 1400x1050 on an Acer]("http://ubuntu.vdb-studios.be/installationDapper.php") is linked to from the [Ubuntu Guide]("http://ubuntuguide.org").

Whilst the hardware may not be exactly the same as yours, the resolution switching program that is used may be helpful to you.

No guarantees, but you might want to take a peek...

---

### Post by jrobinson5 on 2006-09-30
Andy, I tried to follow the instructions you linked me to. No luck.

```
jrobinson@laptop:~$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

ATI chipset detected.  915resolution only works with Intel 800/900 series graphic chipsets.
jrobinson@laptop:~$
```

---

### Post by dresnu on 2006-11-01
Make a copy of your /etc/X11/xorg.conf file, then edit it and make the Screen section look like this:```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection

```

I also have an n610c and have no problem with the 1400x1050 resolution. You can also change the DefaultDepth to 24 if you need more colors.
Hope it helps!

---

