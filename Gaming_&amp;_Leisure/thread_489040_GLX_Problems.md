---
title: "GLX Problems"
date: 2007-06-30
forum: Gaming &amp; Leisure
---

### Post by iceolate on 2007-06-30
This is my first post on this forum, and I'm having some serious problems. I've read 
numerous other threads and websites, but I just can't get this working and I need some help.

I'm trying to play Neverwinter Nights. I have already setup the files and when I went to play,
it told me that it failed to initialize the graphics. I installed the nvidia-glx package from 
Synaptic and rebooted, it refuses to boot into X. 

I went into recovery mode and restored the original xorg.conf file and restarted, and I was able to boot in. 
Right now, it lists the Nvidia Accelerated Graphics Driver as the only entry in the Restricted Drivers Manager. 

When I try to run ./nwn, I get this message:

```

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Failed to initialize graphics.

```

Right now, the driver is not enabled because I rebooted the computer and it really messed up and wouldn't boot into the X login screen. 
I don't really know what to do at the recovery mode prompt, so I just restored the xorg.conf file again.

Please help me.

Thanks.

---

### Post by cogadh on 2007-06-30
Follow the instructions [here]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") to properly install the Nvidia accelerated drivers.

---

### Post by iceolate on 2007-06-30
Hey thanks. That worked perfectly! And it only took about 5 minutes. 
I don't know why I didn't see that post anywhere. Cheers. Off to play NWN.
Thanks again!!!

---

### Post by cogadh on 2007-07-01
Glad to help!

For future reference, that doc was part of the [Ububtu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page"), an excellent site to keep bookmarked.

---

