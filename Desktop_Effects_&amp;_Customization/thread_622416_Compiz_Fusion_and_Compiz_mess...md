---
title: "Compiz Fusion and Compiz mess.."
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by Zeko2210 on 2007-11-24
Hello everyone.

I tried to install Compiz first and during the install procedure I found out Compiz Fusion is maybe better. So I followed the documentation on installing CFusion, and when I try to install packages I get this output in terminal:

I```
nstall these packages without verification [y/N]? y
(Reading database ... 124103 files and directories currently installed.)
Unpacking compiz-fusion-plugins-main (from .../compiz-fusion-plugins-main_0.5.2+git20070917-0ubuntu3~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-fusion-plugins-main_0.5.2+git20070917-0ubuntu3~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libput.so', which is also in package compiz-extra
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking compiz-fusion-plugins-extra (from .../compiz-fusion-plugins-extra_0.5.2+git20070917-0ubuntu1~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-fusion-plugins-extra_0.5.2+git20070917-0ubuntu1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgroup.so', which is also in package compiz-extra
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-fusion-plugins-main_0.5.2+git20070917-0ubuntu3~ppa1_i386.deb
 /var/cache/apt/archives/compiz-fusion-plugins-extra_0.5.2+git20070917-0ubuntu1~ppa1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So, I figured out Compiz package is making a problems for Compiz Fusion. I don't know what to do, and my CompizConfig Settings Manager won't start at all.

Please help to this desperate student......
Thanks in advance.

---

### Post by FuturePilot on 2007-11-24
Which version of Ubuntu are you running? 7.10 comes with most of Compiz Fusion already installed.

---

### Post by Zeko2210 on 2007-11-25
Ok, I have updated to 7.10 last night. 
Now I am able to run Compiz settings manager, but when I want to turn on desktop effects I get message *Desktop effects could not be enabled*. I have read in 7.10 docs that it means my graphics card doesn't support effects. I have GeForce FX Go5200 32M/64M on laptop. When I try compiz --replace in terminal I get this: 

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0328 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 
metacity: Unknown option --eplace

```

Now I am not sure if compiz -- replace is right command for CFusion or only for Compiz, but I noticed from the first line that my Xgl might not work. I wonder if this is Graphics Adapter problem or just Xgl is not started. Then again I have read in doc's that Xgl is automatically installed on 7.10. 

Can anyone direct me what to do?? I don't even know how to check if my card supports this Xgl technology which is going to be subject of my interest in next semester courses.:)

---

### Post by Forlong on 2007-11-25
> **Zeko2210 said:**
> ```
Less than 65536kb of memory and nVidiaaborting
```
Your graphics card has too less memory to run Compiz properly.
If still want to use it, try this:
```
SKIP_CHECKS=yes compiz
```

---

