---
title: "Compiz mysteriously stopped working"
date: 2009-03-26
forum: General Help
---

### Post by rocketpants on 2009-03-26
I booted my machine up this morning and everything was working normally. This afternoon, I logged out and logged back in again, and Compiz has stopped working. I haven't changed anything on my system (although there were some updates this morning, I think).

I'm running Ubuntu 8.10, with an NVidia 9600GT, driver version 180.29

compiz-check gives:
```

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

```

Can someone please give me some ideas as to how to track down the problem?

---

### Post by Yashiro on 2009-03-26
Open Synaptic Package Manager. Look in the History menu option.
Check what updates were installed.

---

### Post by rocketpants on 2009-03-26
That was exactly the clue I needed. Included in the updates this morning were two updates to xserver (xserver-common and xserver-xorg-core).

I've reinstalled the NVidia driver and all is working again.

Yashiro - thankyou! You've saved me hours and hours of Googling for the answer.

---

### Post by Yashiro on 2009-03-26
No probs. :)

Re-installing the nvidia driver would have been my next post. From what you said, either your kernel or xorg got updated, which usually breaks nvidia drivers.

---

### Post by ballin on 2009-03-26
Perfect, same happened to me post updates and now working again :)

Many thanks

---

