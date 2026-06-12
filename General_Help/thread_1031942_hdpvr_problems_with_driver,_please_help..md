---
title: "hdpvr problems with driver, please help."
date: 2009-01-05
forum: General Help
---

### Post by eppo on 2009-01-05
i'm trying to get my hauppauge hd-pvr working in linux.
i followed this guide:
[http://www.mythtv.org/wiki/index.php/Hauppauge_HD-PVR#Editing_HD-PVR_Recordings](http://www.mythtv.org/wiki/index.php/Hauppauge_HD-PVR#Editing_HD-PVR_Recordings)
everything seemed to install fine, in dmesg i get this when i did modprobe hdpvr:
[  247.976144] hdpvr: USB HD PVR /dev/video0 now disconnected
[  263.040791] hdpvr: USB HD PVR device now attached to /dev/video0
so that looks good. then i do cat /dev/video0 and at the command prompt i get this:
cat: write error: Bad address
and in dmesg i get this:
[  818.402542] hdpvr: ERROR start_streaming: no video signal at input 0
[  818.402588] hdpvr: start_streaming failed
if anyone could help me though this problem that would be great.
thanks

---

### Post by eppo on 2009-01-06
just an update, turns out if you dont have it hooked up to an hd settop box, it doesnt work. i picked up an HD box, and hooked it up. now it works fine.

---

### Post by DHunt on 2009-02-07
Actually, the HDPVR does work with a non-hd source.  By default the HDPVR sets itself to look for video via its component inputs which will contain nothing if you have a SVideo or Composite source hooked up.  To change this, I typed in the following commands via a terminal window:

This command changes the input to the front composite input:
v4l2-ctl --device=/dev/video0 -l --set-input=2

This command changes the audio to the front audio inputs:
v4l2-ctl --device=/dev/video0 -l --set-audio-input=1

From then on, you should have better luck in getting it to work.

---

