---
title: "Breezy with TV output as only monitor"
date: 2005-11-20
forum: Desktop Environments
---

### Post by jmh on 2005-11-20
Hi,

I've been reading many posts in these forums about TV out but to be honest I am confused (all my Linuxes tend to be servers, no GUI) and everything I have tried breaks the X server.

I have a Nvidia FX5200 and I want to set up a system which only uses the TV output (s-vid), no PC monitor at all. It seems others have done so but most posts are for TV + monitor type setups. And as I said, even sneezing in the same house as the PC breaks the X-server! The generic one works fine to the PC screen so I have a working base, and the TV does show the bootup but then that goes off once the GUI comes in.

Assuming it is do-able and I have missed something blindingly obvious, any pointers would be most useful. Not posting my xorg.conf (yet!) but can do of course.

Thanks!

---

### Post by Drain on 2005-11-20
[QUOTE=jmh]
I have a Nvidia FX5200 and I want to set up a system which only uses the TV output (s-vid), no PC monitor at all. It seems others have done so but most posts are for TV + monitor type setups. And as I said, even sneezing in the same house as the PC breaks the X-server! The generic one works fine to the PC screen so I have a working base, and the TV does show the bootup but then that goes off once the GUI comes in.[/QUOTE]

Wow, what are you doing to that poor Xserver? ;-) (just joking)

First, I'm going to assume you've got the nvidia-glx files installed correctly - you used the apt-get method, I hope? ;-) (since I just saw it a moment ago, here is a refresher [thread]("http://ubuntuforums.org/showthread.php?t=92001"). 

I've gotten tv-out as the only monitor working before, but it's been a while since I set it up. I did it as part of a MythTV installation, and followed directions [on Christopher Scholz's webpage]("http://www.cs.rit.edu/~css8044/?q=mythtv#nvidia") for configuring the xorg.conf file. (I think his instructions to install the nvidia drivers are out of date for Breezy, but the xorg.conf information on the tv-out should be sound). 

Hope that helps. Good luck!

---

### Post by jmh on 2005-11-21
Thanks for the pointers. I had a go at modifying the xorg.conf as per the link but clearly something is up as it blew again. I checked the log and it could not find a screen res. Anyway, Googling armed with more info now turned up this which works when merged into my xorg.conf:

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Analog TV"
        HorizSync    31.5 - 79.0
        VertRefresh  50.0 - 90.0
        Option      "dpms"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


So I have a working TV only system! Now if only I'd remembered to back the conf file up before I switched it off and packed it away for the night... just in case (!)

Thanks.

---

