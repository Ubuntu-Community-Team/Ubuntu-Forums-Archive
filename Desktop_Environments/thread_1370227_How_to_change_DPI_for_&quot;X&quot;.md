---
title: "How to change DPI for &quot;X&quot;"
date: 2010-01-02
forum: Desktop Environments
---

### Post by LexRiver on 2010-01-02
Hello, I'm trying to change DPI for "X" to look the fonts in firefox better. Fonts in GNOME looks nice, but not in Firefox and some other applications. I think it's because of DPI settings for the "X".

Command "xdpyinfo | grep resolution" returns "90x88 dots per inch". 
My resolution of monitor is 1680x1050.

Fonts DPI for GNOME is set to 96, and its looks nice.

So I'm trying to change  DPI for "X". 
1) I was trying to change /etc/X11/xorg.conf and add :
```

Section "Monitor"
    DisplaySize 444 277 # 1680 x 1050
EndSection

```But after that "X" doesn't starts at all. So I change xorg.conf back from console and it's back to normal.

2) I was trying to create "~/.Xresources" file with content
```

Xft.dpi: 96

```But nothing changes.

I'm using Ubuntu 9.10 Karmic Koala (AMD 64)
Monitor : DELL 2209WA (1680 x 1050)
Video card : Nvidia


Please help me and say what I'm doing wrong and how can I change DPI for "X" ?

---

### Post by farrell2k on 2010-01-02
[http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)

Maybe this will help.

---

### Post by thelatemail on 2010-04-18
I had the same issue under fluxbox and it seems saving the 'Xft.dpi: 96' (without quotes) text to ~/.Xdefaults instead of .Xresources did the trick.

---

