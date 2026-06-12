---
title: "A really tricky TNT2/Beryl one for you :D"
date: 2006-12-14
forum: Desktop Environments
---

### Post by jbtito03 on 2006-12-14
Hi folks

I have a very tricky one for you today :D

Couple of months ago i had no 3D by default (althou many had no problems with their TNT2 cards) and to make 3d work i had to make the composite extension in xorg.conf disabled. Now... 3d works but slower than on other systems (about 1/3 preformance). 

As you all know, beryl needs composite and it works with the TNT2. Now the question:

How can someone use Beryl/3D if 3D cant be used if the composite ext. is on which needs Beryl/3D?

Hehehe... makes me smile :D really :D :D :D

Cheers

JB

---

### Post by jbtito03 on 2006-12-14
Okey... at least i can run glxgears and my 3d screensaver :D Also that is something :D


Cheers...


JB

---

### Post by JanusDC on 2007-02-03
You can use GLX and Composite together if you put the following option in your Section "Device" with the driver nvidia:
```
Option         "AllowGLXWithComposite" "true"
```

---

