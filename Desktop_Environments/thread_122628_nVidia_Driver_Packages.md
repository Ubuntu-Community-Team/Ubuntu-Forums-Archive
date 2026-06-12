---
title: "nVidia Driver Packages"
date: 2006-01-28
forum: Desktop Environments
---

### Post by megabytez on 2006-01-28
I've heard that there are nvidia drivers included with ubuntu which I can install from synaptic. Could anyone tell me the names of these package(s).

---

### Post by Perfect Storm on 2006-01-28
```
sudo apt-get install nvidia-glx nvidia-settings
sudo nvidia-glx-config enable
```

reboot

```
smeg
```

Pick System tools in the left treeview. Then click **New Entry**

name: Nvidia Settings
Command: nvidia-settings

---

### Post by megabytez on 2006-01-28
nvidia-glx is available but nvidia-settings doesnt exist.

---

