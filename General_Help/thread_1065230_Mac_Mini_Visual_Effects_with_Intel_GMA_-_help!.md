---
title: "Mac Mini Visual Effects with Intel GMA - help!"
date: 2009-02-09
forum: General Help
---

### Post by gundo on 2009-02-09
Hello everyone,

Ive just installed Ubuntu for the first time on my intel mac mini.
Everything seems fine, except i cant get the visual effects running, but they would work when I booted into the live CD.

here is the output of lspci:
mark@macubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Here is the output of the checking script:
```

mark@macubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```

Does anyone know why this is not working?
Thanks very much,

mark.

---

