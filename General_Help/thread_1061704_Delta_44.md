---
title: "Delta 44"
date: 2009-02-06
forum: General Help
---

### Post by mantee on 2009-02-06
Hello,

I can not get any sound from my MAudio Delta 44
I go to System->Preferences->Sound
And I see 
M Audio Delta 44 ICE1712 multi (ALSA)
and 
 M Audio Delta 44 ICE1712 multi (OSS)
Listed.

I hit test for either and I get
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Internal data flow error.
```


I was reading [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") and after aplay -l I get
```
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M44 [M Audio Delta 44], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

It seems like the device was detected... any suggestions?

Thanks!

---

### Post by nlz on 2009-02-06
use envy24control to access this soundcard. It works out of the box. I do everything with this card. There is already a lot written about these cards on this forum. But feel free to ask stuff if you cannot find the answer.

---

