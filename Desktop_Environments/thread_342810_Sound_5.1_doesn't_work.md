---
title: "Sound 5.1 doesn't work"
date: 2007-01-20
forum: Desktop Environments
---

### Post by ansi on 2007-01-20
[COLOR="Blue"]upd: oops! it is offtopic I think. Sorry.[/COLOR]

OS: Ubuntu 6.06.1 "Dapper Drake", 2.6.15-27-686
Sound card: internal into m/b (i195G chipset):

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
Subdevices: 1/1
Subdevice #0: subdevice #0 
```

Problem consists that I can't achieve 5.1 sound (surround) of audio-system: works (i.e play music) only 2 speakers of 5. I've tried to edit .asoundrc:
```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
```

But it didn't help: sounding became even worse and only 2 speakers played, again.

What do I do incorrectly? Thanks.

---

