---
title: "startup...never know what screen resolution you'll get"
date: 2009-03-19
forum: General Help
---

### Post by horax on 2009-03-19
Whatup with this?

When I start Ubuntu, you never know what resolution you'll get....1200x850 (or whatever) or 650x400 (or whatever)...TOO HUGE or just right.

If it starts up in the lower res version, I can't change the resolution any higher in the screen resolution section...I have to keep rebooting until I get the size of res that I want.

Any ideas on how to get past this?

-hx

---

### Post by dajasc on 2009-03-19
I probably can't help you, but this is an opportunity to just add that xorg seems to be the weakest point of any linux distro.  It isn't just Ubuntu, it's unstable, cranky, and irritating everywhere it goes.  But hey it's free and I'm not working on it so I can't complain too much.

When I've had similar problems (not since 6.06) I installed envy and my problems went away.  Of course that is assuming an nvidia or ati graphics card.

---

### Post by Nano_ext3 on 2009-03-19
Can you post the output of:

```
less /etc/X11/xorg.conf
```

Also you may want to try and install the ATI drivers or Nvidia Drivers if you have one of the two.  See my blog at [http://thelinuxcauldron.wordpress.com/2009/03/17/how-to-session-installing-your-nvidia-or-ati-card/]("http://thelinuxcauldron.wordpress.com/2009/03/17/how-to-session-installing-your-nvidia-or-ati-card/")

Get back to us here, if you require more help!

Cheers!

-Nano

---

### Post by horax on 2009-03-22
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"

---

### Post by horax on 2009-03-22
Just downloaded the package you mentioned in your blog...let's see if that helps.

---

### Post by CatKiller on 2009-03-22
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

---

### Post by linux_tech on 2009-03-22
Typing ```
 xrandr
``` in the terminal will give you the available resolutions

---

### Post by CatKiller on 2009-03-22
> **linux_tech said:**
> Typing ```
 xrandr
``` in the terminal will give you the available resolutions

Only if X knows about those resolutions. If it's already discarded a whole bunch of them because they are outside of the refresh rate ranges that it's using, then those resolutions will not show up in the xrandr table.

---

