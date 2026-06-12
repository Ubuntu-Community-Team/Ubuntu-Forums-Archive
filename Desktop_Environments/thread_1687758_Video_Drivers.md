---
title: "Video Drivers"
date: 2011-02-14
forum: Desktop Environments
---

### Post by Android565 on 2011-02-14
My laptop's video cable recently broke so I'm now attempting to use it with an external monitor, however I'm having some issues with the video. The monitor connects via the laptops VGA socket.

Initially I got the error "Cannot display video mode" from the monitor when using the FGLRX driver however I was able to boot into Failsafe-X and so have now switched to the VESA driver by editing xorg.conf.

Is there anything you can suggest which might get the monitor running at a higher resolution than 800 by 600? Either by using a different driver or reconfiguring VESA/FGRX? (It should work at 1024 by 768)

Thanks.

---

### Post by An Sanct on 2011-02-14
Can you edit xorg.conf so, that it has that resulution?

You should see something like this
```

Section "Screen"     
Identifier    "Default Screen"     
Monitor        "Configured Monitor"     
Device        "Configured Video Device"     
DefaultDepth    24     
SubSection    "Display"         
Depth    24         
Modes    "1024x768"     
EndSubSection 
EndSection

```
It is more neatly formatted with tabs tho ...

---

### Post by grahammechanical on 2011-02-14
Have you tried System>Preferences>Monitors. I think that you will give a button that offers to detect the monitor you are using.

Does the VGA cable have all the pins or are some missing. Someone (in beginners section) suggested that problems arise when using VGA cables that do not have all 15 pins in use.

Regards.

---

### Post by Android565 on 2011-02-15
> **An Sanct said:**
> Can you edit xorg.conf so, that it has that resulution?

You should see something like this
```

Section "Screen"     
Identifier    "Default Screen"     
Monitor        "Configured Monitor"     
Device        "Configured Video Device"     
DefaultDepth    24     
SubSection    "Display"         
Depth    24         
Modes    "1024x768"     
EndSubSection 
EndSection

```
It is more neatly formatted with tabs tho ...


Thanks, this works, seems fglrx had just been defaulting to a higher resolution. Had previously tried this method with VESA which I don't think can handle the resolution.

Also, the VGA cable only has 14 pins but still seems to work.

---

### Post by An Sanct on 2011-02-15
Great :)

PS. The VGA pinout has three lines and the middle one is GND all 4 or 5 of them, from left to right the second one should be missing, that is normal and does not influence video performance.

---

