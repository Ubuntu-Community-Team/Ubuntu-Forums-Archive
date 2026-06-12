---
title: "screen resolution stuck"
date: 2007-11-27
forum: Desktop Environments
---

### Post by dyerotic on 2007-11-27
i am using ubuntu 7.04 and i upgraded my drivers (nVidia) and i cant get anything but 800x600...and i hate this resolution...i want 1024....how can i got about figuring out how to change this problem

---

### Post by jken146 on 2007-11-27
See this thread: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by dyerotic on 2007-11-27
wayy to complicated...there must be a way i dont have to stop my gnome...or something...

---

### Post by athomson on 2007-11-27
Hi,

There might be a faster way for you. You need to get both the horizontal and the vertical  refresh rates for your monitor before you try this.  The refresh rates are usually given as a range.  Once you have the refresh rates, you will need to edit the X11 config file and change the Monitor section to use those rates. You will also need to change the driver from 'nvidia' to 'nv' if you installed the restricted driver. 

Do not assume that the ones in the X11 config file are correct, in fact since you are getting a lower resolution, they probably are not correct.  

For the example here, I  have an old Hitachi SuperScan Pro 21, it's listed as horizontal 30-85 and vertical 50-150.

Open a terminal

Applications->Accessories->Terminal

Become root
sudo -i

Change to the X11 directory
cd /etc/X11

Backup up the xorg.conf file
cp xorg.conf xorg.conf.orig

Use your favorite editor to edit the file [gvim, vi, nano ...]

vi xorg.conf

Change the device to 'nv' if it's 'nvidia' and update the refresh rates. I have highlighted the lines in [COLOR="Red"]RED.[/COLOR]
```
Section "Device"
        Identifier      "nVidia Corporation NV34 [GeForce FX 5200]"
[COLOR="Red"]        Driver          "nv"[/COLOR]
        BusID           "PCI:1:0:0"
EndSection

Change the Monitor refesh rates to match you monitor's
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
[COLOR="Red"]        HorizSync       30-85
        VertRefresh     50-150[/COLOR]
EndSection
```

Update the Screen section so that the higher resolution modes are first. In this example, with the Hitachi 21 inch, I am not even interested in anything less than 1024, so I removed them.  

Make sure your monitor is capable of supporting the higher resolution modes that you are interested in. If you put the wrong ones in, it could damage your video adapter and/or your monitor.  So don't arbitrarily put in some big size, make sure your monitor supports what you want.

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV34 [GeForce FX 5200]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                [COLOR="Red"]Modes  "1280x1024" "1024x768"[/COLOR]
        EndSubSection
EndSection
```

Save the file and Reboot

If you have problems, <CTRL-BACKSPACE> will kill X11.  Copy the original file back.

---

Andy

---

