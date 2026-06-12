---
title: "How to interchange the right and left stereo channels?"
date: 2006-02-25
forum: Desktop Environments
---

### Post by boa on 2006-02-25
Hi, subj.
ubuntu 5.10. ALSA/ESD

---

### Post by rfruth on 2006-02-25
Swap the cables ?

---

### Post by boa on 2006-02-25
[quote=rfruth]Swap the cables ?[/quote] :)
&#1057;able is not detached.
Program swap interests. This is possible?

---

### Post by thirdhaf on 2008-04-05
I was struggling with this myself and I found the following which may be useful if you are using ALSA.  First of all the ALSA FAQ is where I got this information: [http://alsa.opensrc.org/FAQ#How_can_I_tell_ALSA_to_swap_the_left_and_right_stereo_channels_on_my_soundcard.3F](http://alsa.opensrc.org/FAQ#How_can_I_tell_ALSA_to_swap_the_left_and_right_stereo_channels_on_my_soundcard.3F)

If you want the swap to work universally you need to create a file called 

```
/etc/asound.conf
```

In this file should be the following lines:

```
pcm.swapped {
    type         route
    slave.pcm    "cards.pcm.default"
    ttable.0.1   1
    ttable.1.0   1
}

pcm.default      pcm.swapped
```


And now you should be all set, hope this solves your problem.

---

