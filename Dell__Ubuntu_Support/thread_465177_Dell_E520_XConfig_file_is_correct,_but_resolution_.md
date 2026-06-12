---
title: "Dell E520: XConfig file is correct, but resolution starts at 1024 instead of 1900"
date: 2007-06-05
forum: Dell  Ubuntu Support
---

### Post by jtp51 on 2007-06-05
I haven't touched the XConfig file and it has 1900 x 1200 listed first in the Modes for Depth value of 24.

When I start or restart, the resolution is at 1024 x 768 in the UltraSharp 2407WFP Wide-Screen Black Flat Panel Monitor.

What I have to do is go to the Nvidia control panel and select 1900 x 1200 or auto, click Apply, and then everything is set.

"How do I have the resolution set to 1900 x 1200 when I start or restart?"

Thanks,

---

### Post by Rocket2DMn on 2007-06-05
all i can suggest right now is to make sure that 24 is actually set as the default depth in xorg.conf

edit: perhaps you can post the relevant data from xorg.conf?

---

### Post by vigleik on 2007-06-05
You can make nvidia read its config file by executing "nvidia-settings -l" at startup.

---

### Post by hobieone on 2007-06-05
> **vigleik said:**
> You can make nvidia read its config file by executing "nvidia-settings -l" at startup.
 exactly how is this done? i've noticed this issue  withother systems besides dell  when involving widescreen monitors. such as 19 inch one  ans those wanting to run those at 1440x900

---

### Post by vigleik on 2007-06-05
> **hobieone said:**
> exactly how is this done? i've noticed this issue  withother systems besides dell  when involving widescreen monitors. such as 19 inch one  ans those wanting to run those at 1440x900

You mean how do you do something automatically on startup? In kde you would make a little script, something like

#!/bin/sh
nvidia-settings -l

make it executable and put it in the .kde/Autostart folder. In gnome, I don't know. But it's supposed to be easy, maybe go to System -> Preferences -> Sessions.

---

### Post by jtp51 on 2007-06-07
> **vigleik said:**
> You can make nvidia read its config file by executing "nvidia-settings -l" at startup.

Can I put that line in the rc.local file?

Is that what you meant by "at startup".

Thanks,

---

### Post by doublecheese on 2007-06-07
I would try:

 ```
gksudo nvidia-settings
```

Change it to what you want and tell it to write over the xorg.conf file.

---

### Post by jtp51 on 2007-06-07
That is a good thought and that is something that I tried.

Here is the relevant section from my xorg.conf file:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1920x1200_60 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

I don't see anything unusual?

Thanks,

---

### Post by Dscottmc7 on 2007-06-15
todd...U figure this out?  I've tried every suggestion to date (I think), to no avail.  I'm a newbie.  However, most can do 1600x1024 and down!  Have done "auto," edited every piece...one at a time in the xorg.conf file.  No matter what..no 1920X1200.  Help!  Anybody know?  (Appreciate it mucho):(

---

### Post by jtp51 on 2007-06-16
I did figure it out, but it was a bonehead mistake on my part.

I didn't have to create any start-up script or change anything under /etc/rc.d at all.

It turned out that I had 1900 instead of 1920. When I changed it to 1920 and did a restart it worked. My Dell monitor doesn't support 1900.

I've updated my xorg.conf file to show what I have currently,

---

### Post by dondad on 2007-07-02
> **jtp51 said:**
> That is a good thought and that is something that I tried.

Here is the relevant section from my xorg.conf file:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1920x1200_60 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

I don't see anything unusual?

Thanks,


Make sure that the names for the video card and monitor read exactly the same as those in their various sections.

---

