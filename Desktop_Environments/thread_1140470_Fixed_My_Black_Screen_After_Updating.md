---
title: "Fixed My Black Screen After Updating"
date: 2009-04-27
forum: Desktop Environments
---

### Post by codygman on 2009-04-27
Thought This Might Help Some People :)

I upgraded about 5 hours ago to Jaunty from intrepid Ibex, booted up, and I had a black screen.

I immediately went to ctrl+alt+1 in order to operate from the shell, and typed in:

```
sudo pico /etc/X11/xorg.conf
```First of all my conf file looked like this:

```

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```I immediately added:

```
 Driver "intel" 
```right after the Identifier in the "Monitor" section.

I rebooted, i logged in same difference. I then went to my conf file, and changed the driver to "vesa", rebooted, and everything was working.

Well everything except compiz, and I can't live without my fancy compiz stuff i've got :)

I then found this:

[http://ubuntuforums.org/showthread.php?t=1136738](http://ubuntuforums.org/showthread.php?t=1136738)

I did everything there, my memory readings were a bit different, but it worked out. My xorg.conf file ended up looking like this:

```


Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
    VideoRam    261888
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```I then rebooted, went to system->preferences->appereance. From there I clicked the "visual effects tab" where I noticed the default setting was at "none". I set it to "extra", went to terminal, typed in:

```
compiz
```BAM! my desktop transformed to all the configurations I had in compiz.

So for anyones that having the problem, hope this helps.

---

