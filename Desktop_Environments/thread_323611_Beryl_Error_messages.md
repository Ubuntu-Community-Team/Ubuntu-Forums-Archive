---
title: "Beryl Error messages"
date: 2006-12-22
forum: Desktop Environments
---

### Post by 4Play on 2006-12-22
```

```Hello, I just spent the better part of two days trying to get a Compiz/XGL interface set up and working....has to reinstall Ubuntu in the process...etc. Finally got it working (after reading the 100th guide) But I get a few error messages I would like to know about..

My system:

AMD64 3000+
1GB RAM
GeForce 6800 GS (256MB)
Acer AL1916W (1400x900) LCD monitor

Ubuntu 6.10 (Edgy Eft) with all possible updates

So after trying to get Official Compiz to work, following several guides, and failing miserably. I decided to go with Beryl, and [this]("http://doc.gwos.org/index.php/BerylOnEdgy") tutorial.

Did everything as told, and miraculously, it actually worked when i invoked "beryl --display :0 &"
HOWEVER, i get these error messages:

```
 XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Initiating splash
Reloading all options.
```

running ```
emerald --replace &
``` works well, with no error messages.

Now, even though I get the above mentions errors, breyl still loads, with all the functions, even though it's performance could be better, considering the video card....minimization effects and cube switching are rather truncated.

I ran ```
glxgears -printfps
``` and got 3400 FPS, on average

XGL and compiz are installed: ```
/usr/bin/Xgl --help
``` and ```
/usr/bin/compiz --help
``` both return the help info the the programs...

Thanks 4 any help :D

---

### Post by JayTee on 2006-12-22
This link is actually from the gentoo forums but it's pertinent to your problem.
[http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#GLX_EXT_texture_from_pixmap_is_missing](http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#GLX_EXT_texture_from_pixmap_is_missing)

---

