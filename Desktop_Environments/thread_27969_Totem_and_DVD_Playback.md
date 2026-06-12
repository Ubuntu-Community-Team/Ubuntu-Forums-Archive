---
title: "Totem and DVD Playback"
date: 2005-04-18
forum: Desktop Environments
---

### Post by dabeej on 2005-04-18
I noticed lots of threads saying installing libdvdcss2, enabling DMA, and then using totem-xine will fix peoples DVD issues. My issue is weird. I can play the dvd fine, as long as I don't move the slider in totem. If I try to go back or forward, I get  THE FAMOUS dvdcss error. I tried using the console to see if i can get some verbosity that would give me more information what is going on. I see nothing. Any suggestions? Even if you can't give any, and yet you have the same problem, let me know please.

---

### Post by Stormy Eyes on 2005-04-18
Have you considered using a different player? VLC plays DVDs well, uses GTK (though with a wierd file chooser), and just about ever other video format in use. **sudo apt-get install vlc**.

---

### Post by dabeej on 2005-04-18
Yes, I have. Same issue. When i move that slider. It gives out. It only shows that a52 error though. I wondered if that have anything to do with it. I might try wiping it out completely to see what happens.

---

### Post by dabeej on 2005-04-18
I run VLC, do a little seeking using the scroll in the movie and BOOM and this is what I get:


libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0
[00000286] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
[00000316] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
No accelerated IMDCT transform found
[00000252] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 1.0% failed

---

### Post by dabeej on 2005-04-18
I replaced and remove liba52 trying it both times to see any difference, none. I'm stumped. DMA is on.

hdparm /dev/hdd:

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

---

