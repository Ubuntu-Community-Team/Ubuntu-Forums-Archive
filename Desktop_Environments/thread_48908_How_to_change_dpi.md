---
title: "How to change dpi?"
date: 2005-07-14
forum: Desktop Environments
---

### Post by shidai.liu on 2005-07-14
Dear all,

I've a resolution 1280x800 on 12.1 LCD. And the default dpi is 124x124 (xdpyinfo).
When using gnome, it's ok since gnome has its own dpi set to 96. But When I use
other window managers, the font becomes so large that the widgets take up a lot
of space.

One can put 'Xft.dpi: 96' to '~/.Xdefaults' to solve the problem. I'm just wondering
where is the systemwide setting?

Thank you very much.

---

### Post by souki on 2005-07-14
hello,

I have a 1280x800 display too. I have this in my /etc/X11/xorg.conf

```
Section "Monitor"
        Identifier      "Laptop TFT"
        HorizSync       28-64
        VertRefresh     43-60
        Option          "DPMS"
        DisplaySize     338     211     # 1280x800 96dpi
        #DisplaySize    451     281     # 1280x800 72dpi
EndSection
```

there is a thread [here](http://ubuntuforums.org/showthread.php?t=20976)  about fontconfig and dpi settings

---

### Post by shidai.liu on 2005-07-14
[QUOTE=souki]hello,

I have a 1280x800 display too. I have this in my /etc/X11/xorg.conf

```
Section "Monitor"
        Identifier      "Laptop TFT"
        HorizSync       28-64
        VertRefresh     43-60
        Option          "DPMS"
        DisplaySize     338     211     # 1280x800 96dpi
        #DisplaySize    451     281     # 1280x800 72dpi
EndSection
```

there is a thread [here](http://ubuntuforums.org/showthread.php?t=20976)  about fontconfig and dpi settings[/QUOTE]

Thanks very much. This is neat.

---

