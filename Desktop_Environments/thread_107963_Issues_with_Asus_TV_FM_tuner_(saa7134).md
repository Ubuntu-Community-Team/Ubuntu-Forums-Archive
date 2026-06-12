---
title: "Issues with Asus TV FM tuner (saa7134)"
date: 2005-12-24
forum: Desktop Environments
---

### Post by mpbretl on 2005-12-24
Ubuntu autodetects the Asus TV FM tuner card (saa7133 variant), but the default configuration gives very poor performance.  To partially alleviate this problem, I do the following:

For channels 5-6: modprobe saa7134 card=25 tuner=39
For channels 7-65: modprobe saa7134 card=25 tuner=42
For channels 66-77: modprobe saa7134 card=25 tuner=43

This gives acceptable (although not great) performance.  I ran through all 40+ tuners, and the best result was from this combination of 39, 42, and 43.

The whole v4l, v4l2, and dvb thing seems like a mess at the moment.  If anyone can redirect me to some useful people/information, I'd really appreciate it.  Thanks.

---

