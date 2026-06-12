---
title: "X just segfaulted right as my fiancee thought Ubuntu might replace WinXP!"
date: 2009-01-18
forum: Desktop Environments
---

### Post by Pogeymanz on 2009-01-18
Is there anything that can be done to prevent a segfault? I forgot the exact library that had the problem. (I'll check the log again later)

The last time I used Ubuntu was version 7.10 and I've never had X segfault on me... and I'm running bleeding Arch Linux.

I read about a bug where some people get X crashes when they press the del key while running certain programs, but this isn't that. She was playing freecell and had been for nearly an hour- so just mouse-clicks.

Is there a way to downgrade to an older, more stable Xorg?

EDIT: The card is:
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

I just installed a new driver... Do you think that's it? I don't want it to crash while she's using it again, so she'll stick to Windows for a few days.

---

### Post by RJARRRPCGP on 2009-01-18
The problem may be the version of video driver. 

I do know that with Nvidia, the Nvidia driver version must be 72.xx or 7x.xx if you have a GeForce 2. 

Also, I had X crashes galore with Vector 5.9, because of a kernel mismatch with the driver or because of using later than 7x.xx with a PC that's getting long in the tooth, a PC that I used for testing Vector 5.9, an old unit, an Asus A7N266-VM/AA board with integrated GeForce 2 GPU.

With Intel onboard video, I dunno. Maybe try a newer driver release.

---

