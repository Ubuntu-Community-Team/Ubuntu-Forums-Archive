---
title: "inspiron 4600 sound problem"
date: 2009-10-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mikemanblah on 2009-10-26
I have a emu10kx1 sound card. I have the little headphone jack in front of the disk tray and the green one in the back. When i plug speakers into the back, the only option that works is "Dell sound blaster live! emu10xk1 front (OSS)" Its on the back though in the green slot. But when i hit test it does this raspy sound but i'm still getting sound out of it. And when i set the sound thing to the sound card i dont get any sound on youtube or anything else. Could someone help me?
The computer is an ispiron 4600. I'm brand new to linux. I just chose it because i didnt have to go find the internet drivers. So if you reply please put it in noob form. Everything else is working great though

---

### Post by Mikemanblah on 2009-10-27
Bumppppppppppp

---

### Post by Zoot7 on 2009-10-28
Try using the gnome alsamixer to unmute and max the volume of all channels.
```
sudo apt-get install gnome-alsamixer
```

And also, you post the output of the following?

```
aplay -l

cat /proc/asound/devices

cat /proc/asound/version
```

---

