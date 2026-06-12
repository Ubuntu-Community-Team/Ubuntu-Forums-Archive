---
title: "XFCE Sound problems"
date: 2009-01-17
forum: Desktop Environments
---

### Post by ubrox on 2009-01-17
I installed xubuntu-desktop to try XFCE. I am having sound problems now. It works just fine in Ubuntu/Gnome-session. But doesnt work well in XFCE. Any pointers to fix this?

Also, my volume hot keys not working. mute works, brightness works.

---

### Post by adamlau on 2009-01-17
Run the following in a terminal:

```
xfce4-mixer
```

Verify that your Master and PCM (and other supported) slide bars are set properly.

---

### Post by ubrox on 2009-01-17
already did before posting. the behavior of sound is the same as i had with gnome before pulse * 8.04 came by. the behavior is same as what i had with 7.10 

line seems to control the sound but not well. and at two or three points on the line scale, the sound peaks abruptly with lot of noise. I started pulse manually in xfce, t seemed to help little bit. but my hot keys are still not working

---

