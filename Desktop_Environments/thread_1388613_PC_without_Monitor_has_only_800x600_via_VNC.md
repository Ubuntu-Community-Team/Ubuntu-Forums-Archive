---
title: "PC without Monitor has only 800x600 via VNC"
date: 2010-01-23
forum: Desktop Environments
---

### Post by produnis on 2010-01-23
I installed Karmic 32bit on my new server.
During installation, a monitor was attached, and so I had a resolution of 1024x768.

Now, the server is placed in my cellar, without a monitor.

If I connect via VNC to it, I only got a resolution of 800x600. I cannot select any higher resolution via System-Settings in GNOME

Question: Is there any way to set the resolution to 1024x768 as default?

I tried to modify /etc/X11/xorg.conf, but there is no xorg.conf on my system!
Even if I create one, these will be ignored by the system
:(

If I try to start the x11vnc-server with parameter -scale 1028x768  I get "segmentation fault"....

Any help really welcome
:)

---

### Post by krunge on 2010-01-23
> **produnis said:**
> 
I tried to modify /etc/X11/xorg.conf, but there is no xorg.conf on my system!
Even if I create one, these will be ignored by the system

Wow, that's sad...  I was going to suggest you create a fake Monitor section, and have it ignore autodetection.  I wonder what is happening?
> 
If I try to start the x11vnc-server with parameter -scale 1028x768  I get "segmentation fault"....

Could you collect the full x11vnc output (e.g. x11vnc -o /tmp/file.log ...) and either attach it to this thread or send to me in PM?  Thanks.

---

### Post by produnis on 2010-01-24
Thanks for your help,

I now solved the problem..

My self-created xorg.conf was buggy...
I found the solution here: [http://ubuntuforums.org/showpost.php?p=8144910&postcount=1](http://ubuntuforums.org/showpost.php?p=8144910&postcount=1)

The content of xorg.conf should be like that:

```

Section "Device"
Identifier "VNC Device"
Driver "vesa"
EndSection

Section "Screen"
Identifier "VNC Screen"
Device "VNC Device"
Monitor "VNC Monitor"
SubSection "Display"
Modes "1024x768"
EndSubSection
EndSection

Section "Monitor"
Identifier "VNC Monitor"
HorizSync 30-70
VertRefresh 50-75
EndSection
```

Now it works!!
:)

---

### Post by krunge on 2010-01-24
Could you still post the output I asked for regarding the seg fault?  Thanks.

---

### Post by a904guy on 2011-06-12
I've found a solution to the highest resolution 800x600 using the vesa driver. You can use the dummy driver in xorg to get a full list of supported resolutions to use in a headless VNC.

[http://blog.mediafederation.com/andy-hawkins/ubuntu-headless-vnc-vesa-800x600-fix/]("http://blog.mediafederation.com/andy-hawkins/ubuntu-headless-vnc-vesa-800x600-fix/")

---

