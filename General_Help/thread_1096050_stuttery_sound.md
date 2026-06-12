---
title: "stuttery sound"
date: 2009-03-14
forum: General Help
---

### Post by ELD on 2009-03-14
My sound seems to be extremely stuttery so bad that i can't actually listen to anything in Intrepid, can anyone help me find out why?

---

### Post by unutbu on 2009-03-14
I don't have personal experience with the advice given here, but it is the solution I've seen most frequently here at ubuntuforums: [http://ubuntuforums.org/showpost.php?p=6823833&postcount=8](http://ubuntuforums.org/showpost.php?p=6823833&postcount=8)

See also
[psyke83's PulseAudio fixes and System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?t=789578")
[markbuntu's Multiple Sound Solution (ALSA w Pulseaudio)]("http://ubuntuforums.org/showthread.php?t=843012")
Search for the word "stutter"

---

### Post by ELD on 2009-03-14
Didn't help at all, still terrible :(

---

### Post by unutbu on 2009-03-14
After editing /etc/pulse/daemon.conf, did you reboot or run```

sudo /etc/init.d/pulseaudio restart
```
? Also, the guides say you might have to fiddle around with the numbers.

If that doesn't work, then, unfortunately, I have no idea.

---

### Post by ELD on 2009-03-14
I changed the numbers to that post, fiddled around with my own random numbers and yes i restarted pulse, to no effect.

---

### Post by ELD on 2009-03-14
For reference heres my soundscard:
> 
liam@liam-desktop:~$  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I've noticed that turning the sound down in ubuntu not on my speakers actually at a point stops the stuttering, what the frack?

---

### Post by ELD on 2009-03-14
Fixed, upgrading ALSA in one of the linked threads and a reboot worked a treat :D

---

### Post by unutbu on 2009-03-14
That's great news! Congratulations \\:D/

---

