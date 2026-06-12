---
title: "Font for KDE apps"
date: 2006-06-12
forum: Desktop Environments
---

### Post by psychicdragon on 2006-06-12
Can anyone tell me how I can specify the font to use in KDE applications when I don't have KDE installed. I assume I have to create a ~/.kderc file or something like that...

---

### Post by asimon on 2006-06-12
Yes, the fonts are in ~/.kderc , for the format see this one of the machine I am currently sitting in front:
```

[General]
StandardFont=DejaVu Sans,9,-1,5,50,0,0,0,0,0
activeFont=DejaVu Sans,9,-1,5,75,0,0,0,0,0
background=236,236,236
fixed=DejaVu Sans Mono,9,-1,5,50,0,0,0,0,0
font=DejaVu Sans,9,-1,5,50,0,0,0,0,0
menuFont=DejaVu Sans,9,-1,5,50,0,0,0,0,0
selectBackground=188,249,82
selectForeground=0,0,0
taskbarFont=DejaVu Sans,9,-1,5,50,0,0,0,0,0
toolBarFont=DejaVu Sans,9,-1,5,50,0,0,0,0,0
windowBackground=255,255,255
windowForeground=0,0,0

```

But the easiest would be to just install kcontrol and configure it through it.

---

### Post by psychicdragon on 2006-06-12
Thanks dude, that's perfect. I'd rather not install kcontrol if I don't have to since I'll never have to use it again. :KS

---

### Post by asimon on 2006-06-12
[QUOTE=psychicdragon]Thanks dude, that's perfect. I'd rather not install kcontrol if I don't have to since I'll never have to use it again. :KS[/QUOTE]
Ah, in such cases I would just install kcontrol, use it once, and then 'dpkg --purge kcontrol' it again, or even better use aptitude to remove the installed dependencies too.  ;-)

---

