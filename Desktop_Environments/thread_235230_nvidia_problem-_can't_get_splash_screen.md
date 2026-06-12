---
title: "nvidia problem- can't get splash screen"
date: 2006-08-12
forum: Desktop Environments
---

### Post by av05 on 2006-08-12
Hi all,

after installing ubuntu, and upgrading to latest, i'm trying to install the nvidia fx 5500.
i followed the guidelines at [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia:](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia:)
- installed nvidia-glx
- installed all relevant linux-restricted-modules
- ran nvidia-glx-config enable
- restarted X
and dont get the expecetd nvidia splash screen.
i followed all the troubleshooting items, and still wasn't able to get anything. 
Does anyone have any idea to share ?
](*,)

---

### Post by taurus on 2006-08-12
Make sure you use "nvidia" for your Driver in /etc/X11/xorg.conf instead of "nv..."

```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by av05 on 2006-08-12
thanks for the reply, taurus!
I did that already- it's the 4th troubleshoot item.

to be more precise, I get the following error messages when X starts:
```
Module NVIDIA not found
NVIDIA(0): Failed to load the NVIDIA kernel module
NVIDIA(0): Aborting

```

Any idea????

---

### Post by evillawngnome on 2006-08-12
Try posting in the hardware help forum, they might be more familiar with this issue. Best of luck!

---

