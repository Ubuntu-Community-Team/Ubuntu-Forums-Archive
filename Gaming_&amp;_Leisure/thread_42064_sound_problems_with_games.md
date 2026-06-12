---
title: "sound problems with games"
date: 2005-06-15
forum: Gaming &amp; Leisure
---

### Post by ubuntu_demon on 2005-06-15
hi,

I haven't been playing games with Ubuntu untill now (it's summer and I've got some spare time).

I had some sound problems with games .. I have solved them except for frozen bubble. Maybe this helps someone else. That's why I don't delete or close this thread.

This are the relevant specs :
```

I've got an asus P4P 800 deluxe motherboard.

lspci gives me :

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC '97 Audio Controller (rev 02)

```

This is what I did :

$sudo apt-get install alsa-oss
(I switched to alsa using the multimedia selector) .. you might need a reboot

I  have to run nexuiz with exuiz-linux-x86-sdl
nexuiz runs allright including sound!

The only minor sound problem I've got left is :frozen bubble (no sound)

---

