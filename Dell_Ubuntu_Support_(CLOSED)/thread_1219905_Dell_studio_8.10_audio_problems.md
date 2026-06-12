---
title: "Dell studio 8.10 audio problems"
date: 2009-07-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wardy277 on 2009-07-22
Hi i have bought a new Dell Studio and i cant seem to get the audio working. (I also cant seem to get compiz working but thats another matter) I have been using ubuntu for a few years now and am retty familiar with it.

I can seem to get any sound out of it. I have tried various things but none of them have worked.

I get the following error when running auto-detect test:
**Sound Events:**
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
```

**Music and Movies:**
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument
```

**Audio conferencing**
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect stream: Invalid argument
```

here is my aplay output:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


any help would be greadly appriciated?

---

### Post by atulkakrana on 2009-07-24
Same problem dude...Trying to solve from last 5 months..it also damaged my laptop speakers....No solution.

---

### Post by wardy277 on 2009-07-24
Glad I'm not the only one. Anyone got a solution

---

