---
title: "Screen Resolution Issue X11/Gnome/Nvidia?"
date: 2010-02-23
forum: Desktop Environments
---

### Post by twistdhood on 2010-02-23
I have a strange issue.

I have a widescreen samsung that I want to set at 1680x1050. All fine and dandy. I use nvidia-settings and everything is groovy.

Now on x restart (ie logout restart etc) it gets reverted back to a 1024x768. I know my xorg.conf is correct, in fact my logs show:

```
(II) NVIDIA(0): Setting mode "1680x1050+0+0"
```

...

but wouldn't you know...the VERY last message that comes up is:

```
(II) NVIDIA(0): Setting mode "1024x768" 
```

I have no idea why this is. So does anyone know where to point me next? If anyone is aware of a bug in gnome/x11/nvidia that would describe this behavior I'd appreciate a nudge in the right direction. I've done just about all the trouble shooting I can think of on my own with this.

The ONLY quirk with my setup is I'm using a port switcher between 2 machines, I guess I could unhook that and see if it's interfering somehow, but I don't think that would interfere with this in anyway. At least it shouldn't...

So anyone have any good ideas to look for? It's really annoying to have to reset my resolution EVERY TIME I login...

Ubuntu: KK 9.10

xorg.conf
```

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050 +0+0; 1680x1050_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by wojox on 2010-02-23
You need to set the resolution as root. Open a terminal:

```
gksudo nvidia-settings
```

If it tells you you can't save it then:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

---

### Post by twistdhood on 2010-02-23
sudo/gksudo is not the issue here. I've confirmed the settings are correct. I have run with gksudo. I have saved to alternate file and sudo mv the file. I have even vi'd the file and input my own settings which I prefer anyways, but since I wasn't getting what I wanted I figured there was an issue with the nvidia settings, so I decided to try that route. So it's something beyond the common errors here.

Any other ideas?

---

### Post by twistdhood on 2010-07-22
After 'dealing' with this for seemingly forever, I finally sat down and argued with my system for quite some time.

Ironically I added a new account to my pc and stumbled upon a strange experience, the new account was configured properly! The screen resolution was exactly what it needed to be.

This got me trolling my private configurations, and low-and-behold..

~/.config/monitors.xml

inside had a resolution set to the constant preset...

I don't know (yet) what package this belongs to...but it's not an obvious first guess I for me...maybe because I work so much with RHEL at work and only have Ubuntu at home. But at any rate, I really hope this helps someone because it's been really annoying, but at least now it's been solved (this time...)!!!

---

