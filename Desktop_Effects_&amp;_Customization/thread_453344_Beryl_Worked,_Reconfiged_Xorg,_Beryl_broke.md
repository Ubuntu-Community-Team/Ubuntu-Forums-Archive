---
title: "Beryl Worked, Reconfiged Xorg, Beryl broke"
date: 2007-05-24
forum: Desktop Effects &amp; Customization
---

### Post by daynah on 2007-05-24
That's kinda it. I broke K doing something wit wy wouse (PS never got that working). Being the intelligent woman I am, I didn't make a back up so I reconfiged xorg with something like dpkg-reconfigure xserver-conf. When I came back, beryl manager was up but not using beryl. When I switched from metacity to beryl... the windows have no skins at all! Kinda hard to move around. So back to Metacity. I picked the "nvidia" driver in xorg (because I am, indeed, using nvidia)

Question: What did I break? :)

Thanks!

---

### Post by dfreer on 2007-05-24
Would need to see your /etc/X11/xorg.conf file and the output of this command:
```
glxinfo | head
```
But do you have the following lines in your /etc/X11/xorg.conf?
```

Section "Module"
        .......
        Load            "glx"
        .......
EndSection


Section "Device"
        Identifier      .......
        Driver          "nvidia"
        Busid           .......
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        .....
EndSection

```

Just remember: Always backup your /etc/X11/xorg.conf file, every time you edit it.

---

