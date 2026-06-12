---
title: "Now this is weird"
date: 2009-05-19
forum: Desktop Environments
---

### Post by Drokles on 2009-05-19
I was just having some harmless fun editing xorg.conf and it went very well except.. Why are my panels all screwed up? I remember the trash bin being to the right of the workspace button and network connections being... Somewhere else definitely (-_-)'.

[IMG]http://img217.imageshack.us/img217/8690/wtht.png[/IMG]

Does anyone know what to do? My current xorg.conf settings are as follows:
```
Section "Monitor"
    Identifier     "MyMonitor"
    HorizSync        30 - 81
    VertRefresh    55 - 80
    DisplaySize    390 393
    VendorName     "SHG Computers"
    ModelName      "SCT17-8BS"
    Modeline "1280x1024" 151.83  1280 1360 1544 1888  1024 1024 1027 1072 -HSync -VSync
EndSection

Section "Device"
    Identifier     "GeForce 7900 GT/GTO"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce 7900 GT/GTO"
    Monitor        "MyMonitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

```But I'm pretty sure that they should be ok. (You're welcome to comment on it btw.)

Help will be appreciated!

~ Drokles

---

### Post by Zom-b on 2009-05-19
[S]does it let you just drag them back to where they were?[/S]

wait wait wait, i'm thinking about something else, right click and see if they are locked, then if they aren't click on move and see if you can put them back?

---

### Post by Drokles on 2009-05-19
Ah thanks. It worked for the lower bar, but on the top one it doesn't quite work.

---

### Post by Concrete on 2009-05-19
Hello

Did u try to delete "bar" and create a new 1?

---

### Post by Drokles on 2009-05-19
Thanks. Problem solved.

---

### Post by Concrete on 2009-05-19
Nice... u can post here what was the solution? ;)

---

