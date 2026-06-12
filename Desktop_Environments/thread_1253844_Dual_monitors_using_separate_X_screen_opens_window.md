---
title: "Dual monitors using separate X screen opens windows on wrong monitor"
date: 2009-08-30
forum: Desktop Environments
---

### Post by Jerrac on 2009-08-30
I have dual monitors set up using the separate X screen option in nvidia-settings. My problem is that when I opens new windows on the wrong monitor. As in, I open a window or program on my left monitor, and it shows up on my right monitor. The only program that seems to open on the correct monitor is Firefox.

Any suggestions?

---

### Post by trakz on 2009-09-08
I too am running into this issue, would be great to have a solution...

---

### Post by trakz on 2009-09-08
Nervermind, found the solution: [https://answers.launchpad.net/ubuntu/+source/glib2.0/+question/77380](https://answers.launchpad.net/ubuntu/+source/glib2.0/+question/77380)

---

### Post by Jerrac on 2009-09-09
> **trakz said:**
> Nervermind, found the solution: [https://answers.launchpad.net/ubuntu/+source/glib2.0/+question/77380](https://answers.launchpad.net/ubuntu/+source/glib2.0/+question/77380)
Yes! Thank you! The instructions to install an updated glib2.0 from the PPA did the trick.

For anyone else searching the forums for this problem, go to the quoted link, and follow the instructions in the comment titled: "keepitsimpleengr  said on 2009-07-20".

---

