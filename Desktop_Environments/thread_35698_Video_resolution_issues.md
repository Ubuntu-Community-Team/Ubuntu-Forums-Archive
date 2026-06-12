---
title: "Video resolution issues"
date: 2005-05-19
forum: Desktop Environments
---

### Post by himuraken on 2005-05-19
I am unable to get my screen resolution higher than 1280x1024. In windows I can achieve 1600x1200 with my video card and monitor. Hardware: Nvidia GeForce FX 5200 w/ 256MB RAM on KDS Visual Sensations 19" CRT. I have loaded and successfully tested the nvidia linux driver. Any suggestions?

---

### Post by metallikop on 2005-05-19
[QUOTE=himuraken]I am unable to get my screen resolution higher than 1280x1024. In windows I can achieve 1600x1200 with my video card and monitor. Hardware: Nvidia GeForce FX 5200 w/ 256MB RAM on KDS Visual Sensations 19" CRT. I have loaded and successfully tested the nvidia linux driver. Any suggestions?[/QUOTE]
 Under Section "Screens" in your /etc/X11/xorg.conf Make sure your Modes under SubSection "Display" have "1600x1200".  (you'll have to edit as root)

Here's mine for example:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV40 [GeForce 6800]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

---

### Post by dmatubu on 2005-05-19
I have an Intel 852/855 integrated chip. In Windows it goes up to 1024x768 but in all *nix flavors I've tried, I can't get it over 800x600, even using Intel's own i810 driver. I'd really like to use Ubuntu, it's my favorite thus far. If anyone has any info on getting this video card to increase the resolution I'd be thankful. Manually editing xorg.conf has no effect (believe me I've tried several things so far with no luck).

---

### Post by himuraken on 2005-05-19
In other distrobutions I have got this setup higher so I know it isnt the hardware.

I edited my xorg.conf as instructed now it reads:

[COLOR=Red]Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:3:0:0"
EndSection

Section "Monitor"
        Identifier      "Visual Sensa"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "Visual Sensa"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
[/COLOR]

I restarted my X server and logged back in. I am still running at 1280x1024 and under the screen resolution option in -> System-> Preferences-> Screen Resolution the max is still 1280. Where would you suggest going from here?

---

### Post by himuraken on 2005-05-19
Sorry everyone, my mistake, I THOUGHT that I restarted X when I had not. Everything is running great now. But it makes me wonder why every other distro detected and configured xorg.conf correctly but Ubuntu 5.04 didn't.

Thanks again

---

