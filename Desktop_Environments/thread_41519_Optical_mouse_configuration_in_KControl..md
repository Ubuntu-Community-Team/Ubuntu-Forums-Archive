---
title: "Optical mouse configuration in KControl."
date: 2005-06-13
forum: Desktop Environments
---

### Post by z-vet on 2005-06-13
Hi all.
In KControl > Peripherals > Mouse there is a tab called "Wheel Mouse Optical" where i found an option to change my mouse's sensor resolution from 400 cpi to 800 cpi, which gives me a faster, smoother and more accurate pointer. But each time i restart KDE this option changing to it's default value of 400 cpi, so i need to change it back manually. My question is how to avoid it and set the change i made to be permanent?

---

### Post by meldroc on 2005-06-14
How did you get this extra tab in the mouse kcontrol module?  It is completely absent from mine.

---

### Post by z-vet on 2005-06-14
[QUOTE=meldroc]How did you get this extra tab in the mouse kcontrol module?  It is completely absent from mine.[/QUOTE]
 I don't know, meldroc, it's just was there. I've never seen it before too (i used KDE 3.4 on other distros).

---

### Post by meldroc on 2005-06-15
I just found in the docs for kcontrol that this advanced tab only works for Logitech mice.  My Razer Diamondback, doesn't qualify.

I was able to go into /etc/X11/xorg.conf and set the resolution there.

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "9"
        Option          "ZAxisMapping"          "4 5"
        Option          "Resolution"            "1600"
EndSection
```

---

### Post by z-vet on 2005-06-15
[QUOTE=meldroc]I just found in the docs for kcontrol that this advanced tab only works for Logitech mice.  My Razer Diamondback, doesn't qualify.

I was able to go into /etc/X11/xorg.conf and set the resolution there.

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "9"
        Option          "ZAxisMapping"          "4 5"
        Option          "Resolution"            "1600"
EndSection
```[/QUOTE]
 Well, i always loved Logitech and now i know why. ;)

---

### Post by meldroc on 2005-06-16
[QUOTE=z-vet]Well, i always loved Logitech and now i know why. ;)[/QUOTE]
 Hey, don't knock the Razer Diamondback!  Those are kickass mice!

---

### Post by themoddingden on 2005-06-16
tanks for the info.
i'll have to try this with my mx 1000:)

---

### Post by z-vet on 2005-06-16
[QUOTE=meldroc]Hey, don't knock the Razer Diamondback!  Those are kickass mice![/QUOTE]
Sorry, man, it's just my opinion.

---

