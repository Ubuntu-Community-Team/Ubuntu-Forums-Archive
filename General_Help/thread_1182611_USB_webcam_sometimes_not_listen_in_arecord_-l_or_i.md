---
title: "USB webcam sometimes not listen in arecord -l or in skype sound in"
date: 2009-06-09
forum: General Help
---

### Post by hackys on 2009-06-09
Hi

my USB webcam sometimes is not listen in arecord -l or in skype sound in, so i can't use skype. But in lsusb the webcam is listen and also i can see my self in Cheese. I have to reboot the system and hope, this time it will be there. Any idea how to fix this?

Ubuntu 8.10, USB Logitech Quick Zoom, audiopulse

---

### Post by s.fox on 2009-06-09
Hi,

Can post the output of 

```
lsusb
```

Then we will know more about the chip set your camera has :)

Thanks,

-Ash R

---

### Post by hackys on 2009-06-09
```
supersasho@LOGUX:~$ lsusb
Bus 002 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:08b4 Logitech, Inc. QuickCam Zoom
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by hackys on 2009-06-11
i'll give it a small bump

---

### Post by s.fox on 2009-06-11
Hi,

Sorry for the wait,   I think it would be worth installing EasyCam.  It should assist you in setting up your camera.  [Here ]("https://help.ubuntu.com/community/EasyCam")is a link to the setup guide.

-Ash R

---

### Post by hackys on 2009-06-11
Hi, thanks for helping me out :) i've installed the easycam, started it, the driver is installed, so i just wait for some reboots to come and see if the webcam will allways be there. i'll report back to confirm my problem to be [SOLVED] or to seek for another solution :)

---

### Post by hackys on 2009-06-12
Hi, so this easycam did not help. After 2 reboots the audio device from USB webcam disappeared. :(

---

### Post by hackys on 2009-06-22
The problem persist. Could it be that the driver is broken? Any help would be appreciated. :)

---

### Post by hackys on 2009-06-29
Ok, i just found out, that not just the webcam audio randomly disappears, also my tvcard's audio is disappearing.. so this is an audio issue not just webcam. (i don't use the tvcard so often, that's why i didn't notice). Some help from community? :)

---

### Post by hackys on 2009-07-09
There's really no one who could possibly help me?

Edit: i found this in kern.log when my tvcard audio wasn't working

```
Jul  9 20:17:19 LOGUX kernel: [   17.052648] cannot find the slot for index 2 (range 0-2), error: -16

Jul  9 20:17:19 LOGUX kernel: [   17.052656] cx88_audio: probe of 0000:01:07.1 failed with error -12
```

---

### Post by hackys on 2010-05-11
The solution was to install a newier distribution, just to let others know.

---

