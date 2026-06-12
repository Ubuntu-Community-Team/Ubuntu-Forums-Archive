---
title: "Getting Asus TVFM 7135 to work..."
date: 2005-07-08
forum: Desktop Environments
---

### Post by man.life on 2005-07-08
Ubuntu detected the card since installation, because I didn't add "saa7134" to /etc/modules and this is the result of "lsmod | grep saa"

```
saa7134               102408  0
video_buf              21732  1 saa7134
v4l2_common             5664  1 saa7134
v4l1_compat            14244  1 saa7134
ir_common               4804  1 saa7134
videodev                9792  1 saa7134
soundcore              10016  3 saa7134,snd
i2c_core               22320  2 saa7134,i2c_sis96x
``` 

But when I try tvtime to scan channels, I get this message:

```
No tuner found on input 0.  If you have a tuner, please select a different input using --input=<num>.
```

Does someone use this card? Did someone configure it successfully?

---

