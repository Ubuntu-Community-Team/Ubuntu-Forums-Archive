---
title: "Resolution problem.."
date: 2006-01-02
forum: Desktop Environments
---

### Post by bigbluewedding on 2006-01-02
Hello, I am new to both this community, Linux and Ubuntu, I chose Ubuntu because it seemed to be the most "user friendly" distribution avaliable that didn't seem to "suck" - excuse my language please. :)

My problem is that after a successful installation, I am stuck in 640 x 800 resolution, I have tried altering this by using the drop down menu, but I have no options avaliable.

Seeing as this is pretty critical, and that I am entirely new to Linux and Ubuntu, are there some good advice for "newbies" to fix this problem? Do I need to provide you with more information, and if so, what and how?

Thank you so much in advance for any help you may provide, I hope I posted this in the correct location, I also tried doing a search for this problem, as well as consult FAQ's, but it is all just a bit too much for a newcomer in desperate need for assistance, thank you. :confused:

---

### Post by zambizzi on 2006-01-02
Open up a terminal and type the command "sudo nano -w /etc/X11/xorg.conf" (without quotes).

This file is where X (your windowing system) gets its settings.  In there you should see a section that starts w/ this line:

```

Section "Screen"
        Identifier      "Default Screen"
...

```

You'll notice that your screen resolution and color depth settings are set there.  Inside of there you'll notice the subsection (here's an example of mine):

```

SubSection "Display"
        Depth           24
        Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

```

There may be several of them, each with a different "Depth" (i.e. 16, 8, etc.)  If yours only defines "640x480" then you may try adding a string w/ your maximum res. in the "Modes" line.  You will need to reboot your X server to see the changes (or just reboot to keep it simple.)

Also make sure you set the correct Horizonal and Vertical refresh rates while you're in there to get the best out of your monitor.  To do that, refer to the section that looks like this:

```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       31-80
        VertRefresh     56-76
EndSection

```

Another tip, get the nvidia drivers if you have an nvidia card...or the commercial ATI drivers if you have an ATI card.  Hopefully you have an nvidia card ;) 

Try to paste in the contents of your xorg.conf in here so we can help further should you continue to have issues after this.

HTH

---

### Post by Gustav on 2006-01-02
Type:
```
sudo dpkg-reconfigure xserver-xorg
```
and follow the instructions.

If that doesn't work, look at [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973).

Good luck!

---

### Post by bigbluewedding on 2006-01-02
It seems that it has identified both my monitor and graphics card correctly, so I am uncertain of what I need to change to obtain the results you mentioned. I also am not entirely sure how to install the drivers for my card, unless they are already installed? 

Below is a paste of what the terminal gave me:


Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 MX 440-SE]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Xpert 710"
        Option          "DPMS"
EndSection
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV17 [GeForce4 MX 440-SE]"
        Monitor         "Xpert 710"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "720x450" "640x480"
        EndSubSection
SubSection "Display"
Device          "NVIDIA Corporation NV17 [GeForce4 MX 440-SE]"
        Monitor         "Xpert 710"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "720x450" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "720x450" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "720x450" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
 EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "720x450" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "720x450" "640x480"
    EndSubSection
EndSection


So, should I try out auto-config, or is that futile?

Thanks :???:

---

### Post by zambizzi on 2006-01-02
To install the nvidia drivers open a terminal and type this command:

```

sudo apt-get install nvidia-glx

```

When that's done, you have to make two small changes to your xorg.conf.  In the section that starts with Section "Module" you need to comment-out the line that says Load "dri" and make sure there is a line that says Load "glx"...it should look something like this when you're done:

```

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        #Load   "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

```

Next...change the section labeled Section "Device"...change "nv" to "nvidia"...so it looks something like this:

```

Section "Device"
        Identifier      "NVIDIA Corporation NV41 [GeForce 6800]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

```

Make sure you only change the parts I specified...your hardware is different than mine so if you copy what I posted word-for-word you could mess something up.

Anyhow, I did it and it works great for me!  Maybe this will get rid of your issues.  My screen wouldn't even work until I installed the nvidia drivers!

Also, Gustav posted some very good information to help you troubleshoot.

---

### Post by bigbluewedding on 2006-01-02
I installed the proper Nvidia drivers as you suggested, but that didnt do the trick, then I followed Gustavs suggestions, and finally somehow configured it all properly!

Thank you both for your very valuable support, I finally feel I can explore and enjoy my new O/S.. Thanks! :)

---

