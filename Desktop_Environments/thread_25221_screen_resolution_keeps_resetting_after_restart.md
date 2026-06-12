---
title: "screen resolution keeps resetting after restart"
date: 2005-04-09
forum: Desktop Environments
---

### Post by brickbat on 2005-04-09
hi, every time i restart, my screen resulution reverts back to 1280 x 800.

I tried modifying xorg preference but it doesnt change anything.

I also looked in xorg.conf but cant find a default resolution there.

Please help. I'm sick of setting it manually each time.

if i could get my refresh rate to 100 that would be a bonus.

ciao,
bb

---

### Post by humanity_to_others on 2005-04-09
Maybe your monitor refresh rate couldn't recognized correctly. Or you can enable or disable screen resolutions with ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by brickbat on 2005-04-09
thanks for the advice.

i did this but the refresh did not improve.

One thing that is interesting is that it says my monitor is a "ultrascanp99"

In fact it is a dell p990 (don't know if it ultrascan)

any other suggestions?

ciao
bb

---

### Post by mrbass on 2005-04-10
This 19" Trinitron display from Dell Computer Corporation of Round Rock, Texas, has a vertically flat screen to reflect more ambient light away from users. The UltraScan P990 offers up to 1600 x 1200 resolution at 75 Hz with an optimal resolution of 1280 x 1024 at 85 Hz. The dot pitch/aperture grille pitch is 0.25mm to 0.27mm. Horizontal scan range is **30–96k Hz** with a **48–120** Hz vertical range.

change those values in /etc/X11/xorg.conf

Section "Monitor"
        Identifier      "Dell P990"
        Option          "DPMS"
        HorizSync       30-96
        VertRefresh     48-120

if you have nvidia driver installed make sure that the 
Section 'screen' has
Monitor "Dell P990"

---

### Post by brickbat on 2005-04-10
Hi, I followed the directions and rebooted but nothing changed.  Do I need to do anything else to activate them.  I checked the file and it has got the "Dell P990"  and all the other changes.

ciao
bb

---

### Post by mrbass on 2005-04-10
well you should have modelines in your xorg.conf

something like so
      SubSection "Display"
                Depth           1
                Modes           "1152x768" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1152x768" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1152x768" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1152x768" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1152x768" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1152x768" "1024x768" "800x600"
        EndSubSection
EndSection

---

