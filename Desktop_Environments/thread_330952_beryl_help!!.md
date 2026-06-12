---
title: "beryl help!!"
date: 2007-01-03
forum: Desktop Environments
---

### Post by uthturn on 2007-01-03
how do i set up beryl to work with my s3 unichrome i have openchrome installed and 3d in enabled when i try to run it i get the error 
 XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension
please explain in the noobish way possible

---

### Post by encompass on 2007-01-04
Could you show what howto you followed?

---

### Post by Waappu on 2007-01-04
Hi

Try if this works.
Add end of your /etc/X11/xorg.conf file
```
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

