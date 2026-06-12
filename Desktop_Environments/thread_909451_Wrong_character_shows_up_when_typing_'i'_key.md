---
title: "Wrong character shows up when typing 'i' key"
date: 2008-09-03
forum: Desktop Environments
---

### Post by three_cups_of_java on 2008-09-03
This is an intermittent problem. Sometimes, when I press the 'i' key, a '6' will show up. Sometimes, when I type a capital 'i' (Shift+i), a '^' shows up. And sometimes, the 'i' keys acts as if I'm holding it down when I'm not. This problem seems to come in bursts. Everything will be fine for a while, then all of a sudden, the 'i' key acts like the '6' key. (The '6' key does not act like the 'i' key).

I am using a US keyboard layout.

My keyboard is plugged into a KVM, but I see this problem even when the keyboard is plugged directly into my computer.

I've tried multiple keyboards too. The problem persists. It seems to be an OS issue...

This only happens with the 'i' key.

I'm using 7.10, but I also had this issue with 7.04.

Please help!

---

### Post by billgoldberg on 2008-09-03
> **three_cups_of_java said:**
> This is an intermittent problem. Sometimes, when I press the 'i' key, a '6' will show up. Sometimes, when I type a capital 'i' (Shift+i), a '^' shows up. And sometimes, the 'i' keys acts as if I'm holding it down when I'm not. This problem seems to come in bursts. Everything will be fine for a while, then all of a sudden, the 'i' key acts like the '6' key. (The '6' key does not act like the 'i' key).

I am using a US keyboard layout.

My keyboard is plugged into a KVM, but I see this problem even when the keyboard is plugged directly into my computer.

I've tried multiple keyboards too. The problem persists. It seems to be an OS issue...

This only happens with the 'i' key.

I'm using 7.10, but I also had this issue with 7.04.

Please help!

Strange.

Post the output of your xorg file.

```
gedit /etc/X11/xorg.conf
```

---

### Post by three_cups_of_java on 2008-09-03
Here's my xorg.conf (sans comments):

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection
```

---

### Post by three_cups_of_java on 2008-09-04
> **three_cups_of_java said:**
> I'm using 7.10, but I also had this issue with 7.04.

Sorry, the above is wrong. It should read:

I'm using 8.04, but I also had this issue with 7.10.

---

### Post by three_cups_of_java on 2008-09-10
Any tips on debugging this issue? I'd love to fix it.

---

