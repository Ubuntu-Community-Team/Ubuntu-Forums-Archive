---
title: "KDE Mouse Tweaking"
date: 2009-10-07
forum: Desktop Environments
---

### Post by captaincrook on 2009-10-07
Ahoy there,

I've recently decided to take a dive into KDE after a short stint with GNOME, and currently having XFCE (Xubuntu more precisely) as the main DE. I've decided to give KDE a spin since I use alot of QT apps now and for a more "modern" look, although I have a problem with the mouse when I use this DE.

Firstly, my move from GNOME to XFCE was pretty seamless with regards to my mouse. Everything seemed intact without any customizations, even after a few clean reinstalls the defaults were the same for both DEs in "real world tests". With KDE however, the sensitivity is noticeably much higher and I don't know whats wrong.

I checked the xset settings in my XFCE install using

```
xset -q |grep accel
```

to output the acceleration and threshold values currently set in the DE, and compared the results to the KDE defaults which was the same 

[quote="XFCE"]acceleration:  2/1    threshold:  4[/quote]
[quote="KDE"]acceleration:  20/10    threshold:  4[/quote]

yet the mouse is indeed more sensitive than XFCE and/or GNOME (NOTE: I haven't touched GNOME since Gutsy but my transition to XFCE was seamless).

I figured having the xset values the same would enable the same speed/sens levels across desktop environments as my migration had done, but I assume I could be wrong. So my questions here are: Is there something KDE specific that makes the mouse different from other DEs? And is it possible to have the same speed settings across Desktop Environments (preferably porting XFCE settings) using xset or another command? Note that I do use *buntu for gaming so this is a rather heartbreaking annoyance.

---

