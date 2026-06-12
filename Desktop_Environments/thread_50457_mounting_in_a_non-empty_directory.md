---
title: "mounting in a non-empty directory"
date: 2005-07-20
forum: Desktop Environments
---

### Post by julien_g on 2005-07-20
hi all,

how can I take a non-empty directory as a mountpoint and keep it's content?
in my case, i want to mount a smb share into my home directory without overwriting hidden config files

thanks in advance

---

### Post by frodon on 2005-07-20
I think this command do the job : ```
mount -o bind source_directory destination_directory
```

---

### Post by roblubbers on 2005-07-20
if you mount over a non-empty directory you do not loose your data.
If you umount the original data will then be visible again

---

### Post by julien_g on 2005-07-20
[QUOTE=roblubbers]if you mount over a non-empty directory you do not loose your data.
If you umount the original data will then be visible again[/QUOTE]

i know that, but i want both the mounted data and the original data in this directory

---

