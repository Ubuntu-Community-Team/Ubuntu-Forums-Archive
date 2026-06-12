---
title: "Effect grind desktop to a hault why?"
date: 2007-11-16
forum: Desktop Effects &amp; Customization
---

### Post by c-m on 2007-11-16
After a year or so absence I have just installed the latest ubuntu to go with my c2d cpu.

I tried enabling the basic effect, but even they made my desktop stumble to a halt.

I know I am only running an nvidia 6200 but I had a worse card than that last year, and thorough on of the howto's had drop shadows and transpanrencies.

Why are the effect so slow?

here is the output form my terminal

carl@carl-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
carl@carl-desktop:~$ compiz 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0161 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
^X^C
carl@carl-desktop:~$

---

### Post by c-m on 2007-11-25
I have noticed that other people have been able to run the visual effects with the nvidia 6200 chipset so why can't I?

It can't ttake all that much power, since in 6.10 i used to have drop shodows and transparency.

I have 2gb ddr2 and a core2duo at 2.66ghz

---

### Post by c-m on 2007-12-02
Still can't use any desktop effects, despite others with lesser spec'd systems not reporting any problems

[http://ubuntuforums.org/showthread.php?t=578409&page=2]("http://ubuntuforums.org/showthread.php?t=578409&page=2")

---

