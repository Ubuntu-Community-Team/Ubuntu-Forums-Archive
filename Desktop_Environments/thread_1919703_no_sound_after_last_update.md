---
title: "no sound after last update"
date: 2012-02-03
forum: Desktop Environments
---

### Post by doru001 on 2012-02-03
```
uname -a
Linux nichi 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux
```

After last update sound just stopped working in all applications. I tried older kernels, I added some option at the end of alsa-base.conf, but in vain. This is a shame.

---

### Post by doru001 on 2012-02-03
```
  *-multimedia:0          
       description: Multimedia audio controller
       product: AC'97 Sound Controller
       vendor: Silicon Integrated Systems [SiS]
       physical id: 2.7
       bus info: pci@0000:00:02.7
       version: a0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
       resources: irq:18 ioport:e000(size=256) ioport:e100(size=128)

```

Come on, how is this even possible?

---

### Post by doru001 on 2012-02-03
bump?

---

### Post by doru001 on 2012-02-03
This is the most idiotic thing I ever did. I plugged the microphone jack into the speakers, instead of the headset jack. The speakers were silent because of the microphone jack and the headset was silent because it was not plugged. I wasted hours.

---

