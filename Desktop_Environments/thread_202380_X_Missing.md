---
title: "X Missing"
date: 2006-06-23
forum: Desktop Environments
---

### Post by cikaybe on 2006-06-23
I downloaded and installed the ati drivers for my 9600pro. Now every time i start ubuntu, it gives me an error that says something like it failled to load the graphic environment and i only have acess to the bash. Can anyone help me?

---

### Post by Winblowz on 2006-06-23
Have you tried reconfiguring the X server?
```
sudo dpkg-reconfigure xserver-xorg
```

---

