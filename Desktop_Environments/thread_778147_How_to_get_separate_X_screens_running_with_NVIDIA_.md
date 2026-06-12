---
title: "How to get separate X screens running with NVIDIA settings."
date: 2008-05-01
forum: Desktop Environments
---

### Post by leotemp on 2008-05-01
nothing i seem to do activates my second display using "Separate X screens" When i use Twinview it activates and displays just fine but i can click modify in NVIDIA settings and set it to "separate screens" 100 times and even after saving the config when i reboot the second screen will still be "disabled" What am I missing here?

---

### Post by elvinatom on 2008-05-01
hit alt+F2 and type
```
gksu nvidia-settings
```
Then set it up again, click on "Save X Configuration file", log off and then on again.

---

