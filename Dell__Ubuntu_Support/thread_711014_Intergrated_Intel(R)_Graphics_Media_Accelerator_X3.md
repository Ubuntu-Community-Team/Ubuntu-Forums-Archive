---
title: "Intergrated Intel(R) Graphics Media Accelerator X3100"
date: 2008-02-29
forum: Dell  Ubuntu Support
---

### Post by RookieX on 2008-02-29
Hi, I have installed Ubuntu 7.10 on my Dell Inspiron 1520. My video card is an Intergrated Intel(R) Graphics Media Accelerator X3100. Could someone please tell me how to get drivers for the card. Thanks in advance,

RookieX

---

### Post by supermikey on 2008-03-06
The one that works best (I have the same one) is to use the Intel driver instead of the i810.


```


sudo apt-get install xserver-xorg-video-intel
```

Hope this helps!

---

### Post by vmayer on 2008-06-24
**I have a Toshiba Tecra M8 with the Intergrated Intel(R) Graphics Media Accelerator X3100.  Output of my compiz-check:**

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
[B]
I am having no problems with Ubuntu itself, but games such as Glest, Supertuxkart, etc are causing my computer to freeze up.  Could someone offer me some advice on how to make them work?  Btw, I am completely new to Ubuntu and Linux in general.  [/B]

---

### Post by Forlong on 2008-06-24
vmayer, you have posted in the archive section of the forum. Thus, your posting won't probably be read by many people.

You should consider starting your own thread about this problem and make sure to use a descriptive title that already addresses the freeze issue.


Good luck.

---

### Post by pumakuma on 2008-07-05
pumakuma@pumakuma-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      Xgl

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

what does it mean that it is skipping it?

---

