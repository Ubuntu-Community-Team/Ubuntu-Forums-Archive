---
title: "Device Permissions Are Driving Me Crazy !"
date: 2006-03-04
forum: Desktop Environments
---

### Post by xXx 0wn3d xXx on 2006-03-04
OK, I have a psp. This psp has been working for 2 months with ubuntu. And all of a sudden, I plug in my psp and I can't write to it :) It says I need to be the root, and that's not how it was yesterday. I haven't changed anything since it last worked. I am the only user on this computer, and I don't have a root account. Only my admin one. I used to be able to do everything with it. What can I do ? It mounts fine.

---

### Post by o_fortuna on 2006-03-04
[QUOTE=MasterChief1234]OK, I have a psp. This psp has been working for 2 months with ubuntu. And all of a sudden, I plug in my psp and I can't write to it :) It says I need to be the root, and that's not how it was yesterday. I haven't changed anything since it last worked. I am the only user on this computer, and I don't have a root account. Only my admin one. I used to be able to do everything with it. What can I do ? It mounts fine.[/QUOTE]
You could try
```
sudo nautilus
```
in the terminal (Applications-->Accessories-->Terminal).

Then, navigate to /media/(whatever your psp folder is), right click, and click the permissions tab. Make sure it's set to write for all users.

---

