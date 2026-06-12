---
title: "Changing resolution"
date: 2006-06-01
forum: Desktop Environments
---

### Post by sanderjd on 2006-06-01
I'm using the nvidia driver for my geforce 4 ti and I can only reach a resolution of 1028x768 in the preferences->resolution menu. How can I change this? I know that my card and monitor support at least 1600x1200.

---

### Post by exigentsky on 2006-06-01
[QUOTE=sanderjd]I'm using the nvidia driver for my geforce 4 ti and I can only reach a resolution of 1028x768 in the preferences->resolution menu. How can I change this? I know that my card and monitor support at least 1600x1200.[/QUOTE]

I had the same problem. Go to /etc/Xorg.conf and wher eyou see many resolutions listed, add 1600x1200 in each line. Also make sure that the horizontal and vertical sync are accurate. Otherwise, you may be stuck at 60 Hz.

---

