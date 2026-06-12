---
title: "Help:"
date: 2005-04-17
forum: Desktop Environments
---

### Post by thegreedyturtle on 2005-04-17
```
Failed to load image amule.xpm

Details: Icon not found
```

The problem is when I install a program, it's icon cannot be read by gnome-panel. I checked the permissions, and they are identical to the other icons on the panel...

Also, it's not having any problems finding the same icon after I place a copy of it on the desktop and link to that...

Anyone have any ideas?

If it's of any use, here's the end of my xsession log.
```
(**) Configured Mouse: Buttons: 6
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) NVIDIA(0): Setting mode "1280x1024,1280x1024"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "1280x1024,1280x1024"
```

---

### Post by thegreedyturtle on 2005-04-17
Well, it's cleared up on it's own... I have a love/hate relationship with those 'fixes'...

---

### Post by dataw0lf on 2005-04-17
I know how you feel.  Thanks for letting us know that you 'fixed' it, though.

---

### Post by thegreedyturtle on 2005-04-24
i had to use killall gnome-panel

---

### Post by gotmonkey on 2005-05-12
I came across the same issue with the gnome panel. When I tried to create a launcher inside the panel, It only allowed me to use the default icons that came with gnome. When I created the launchers on the desktop, I could use the application specific icons, in my case they were ripperx, mozilla suite, k3b. Once I created them on the desktop, I dragged them to the gnome panel.

Not really a fix, but a work around

---

