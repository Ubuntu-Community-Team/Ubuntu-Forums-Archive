---
title: "Jaunty total halt and kernel panics"
date: 2009-05-02
forum: General Help
---

### Post by macabro22 on 2009-05-02
I am having very random lock-ups after the Jaunty upgrade. I can't work for a long time undisturbed and many different programs seem to trigger the problem, often when I am navigating on Firefox. I suspect Pulseaudio as well because the sound playback stutters when using rhythmbox.

I run memtest overnight and the RAM is ok. Filesystem integrity is also fine as revealed by fsck.

I will post my log files and any more info that can help.

Please help me out I have no clue what to do.

---

### Post by pinegreen on 2009-05-18
Same here, exactly same symptoms. vaio FW.

---

### Post by whoop on 2009-05-23
What kernel are you running?
```

uname -a

```

---

### Post by macabro22 on 2009-05-24
Linux GlaDOS 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

---

### Post by whoop on 2009-05-24
Well, this bug was reported several times:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347848](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347848)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/374831](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/374831)

But there is not a known solution as far as I can tell.

---

