---
title: "Compiz problem"
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by arophous on 2007-12-21
Hi everyone,

I have an Amilo Pro v2010, managed to install 7.10 perfectly, only problem is i cannot get desktop effects to start even though i installed the graphics card driver from VIA.  Im not really sure what else to try as everything is about ATI/Nvidia...

anyway here is what i get from compiz typed in terminal:

```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

typing fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome (PM8x0/CN400) 20060710 x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 6.5.1

```

How do i make compiz work properly?

Thanks,
Aro

---

### Post by Sef on 2007-12-21
Did you install the restricted drivers?   

System > Administration > Restricted Drivers Manager

---

### Post by arophous on 2007-12-21
Yeh, it said my hardware didn't need any restricted drivers.

---

### Post by ayenack on 2007-12-21
Can I just say that the card as far as I know is next to useless for 3D applications so I'd say that compiz is out of the question anyway.

---

