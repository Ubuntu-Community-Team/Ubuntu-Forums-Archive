---
title: "Help needed from xubuntu user please"
date: 2013-02-24
forum: Desktop Environments
---

### Post by rsavage on 2013-02-24
Hi, I'm currently putting together a xubuntu iso for PowerPC. It's pretty much ready; I just need to clean up a few things and check I have things right. 
 
Could an i386 or amd86 user with a xubuntu 12.04 iso to hand give me the contents of the /preseed/xubuntu.seed file on the iso please? I've had a guess at it, but I'd like to see the real thing. It would save me having to download the whole iso and I''ve been hammering my download usage this month!
 
Cheers

---

### Post by westie457 on 2013-02-24
Here you go. this one is off AMD 64-bit.

---

### Post by matt_symes on 2013-02-24
Hi

Here you go.
```

matthew-S206:/home/matthew/storage/my_isos % cat xubuntu.seed
# Enable extras.ubuntu.com.
d-i     apt-setup/extras        boolean true
# Install the Xubuntu desktop.
tasksel tasksel/first   multiselect xubuntu-desktop
# No XFCE translation packages yet.
d-i     pkgsel/language-pack-patterns   string
matthew-S206:/home/matthew/storage/my_isos %
```

EDIT: Beaten to it :D

Kind regards

---

### Post by rsavage on 2013-02-24
Thanks a lot!

---

