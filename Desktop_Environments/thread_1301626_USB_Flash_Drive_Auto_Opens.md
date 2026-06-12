---
title: "USB Flash Drive Auto Opens"
date: 2009-10-26
forum: Desktop Environments
---

### Post by Ratscallion on 2009-10-26
Hi.

Whenever I plug in any of my USB Flash Drives, external drives etc they automatically open in nautilus. (ie, I plug in my External drive (which has 3 partitions) and 3 nautilus' open up).

My question to you is: Is there a way to stop this happening with some and still happen with others or just stop it altogether?

Cheers.

---

### Post by Giblet5 on 2009-10-26
It's the hal daemon that does this.

Stop hald from loading at startup and all USB/CD insertions will be ignored completely. (probably NOT what you want)

It's all or nothing, unless you're very comfortable with scripting and are careful to identify your USB sticks with useful partition labels.


I have wondered about this, myself.

I suspect that the Ubuntu team asked themselves: "Windows prompts the user. The prompt must be answered. Why not just open the thing and let the user close it if they don't want it open?"

Looking at the issue that way, that Windows prompt is annoying and retarded in an engrossing and empowering way. ;)

---

### Post by John Bean on 2009-10-26
> **Ratscallion said:**
>  Whenever I plug in any of my USB Flash Drives, external drives etc they automatically open in nautilus. (ie, I plug in my External drive (which has 3 partitions) and 3 nautilus' open up).

My question to you is: Is there a way to stop this happening with some and still happen with others or just stop it altogether?

```
gconftool-2 --type boolean -s /apps/nautilus/preferences/media_automount_open false
```

---

### Post by Ratscallion on 2009-10-26
What happened to the box that popped up like it does for cameras/ipods? That has a dropdown (similar to that in Windows) where, in some cases, only has two options: Open with File manager (nautilus); do nothing. May have to use John Bean's solution for now.. Thanks.

---

### Post by John Bean on 2009-10-26
> **Ratscallion said:**
> What happened to the box that popped up like it does for cameras/ipods? That has a dropdown (similar to that in Windows) where, in some cases, only has two options: Open with File manager (nautilus); do nothing. May have to use John Bean's solution for now.. Thanks.It does that for devices/folders that it recognises as special in some way - cameras, dvds, cds, etc. The setting I suggested affects all "unidentified" mounts; for the others it will continue to do whatever you told it to for that kind of "disk".

---

### Post by Ratscallion on 2009-10-26
Oh right cool.. Marking as [SOLVED], thanks :)

---

