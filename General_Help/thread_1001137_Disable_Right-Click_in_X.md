---
title: "Disable Right-Click in X"
date: 2008-12-03
forum: General Help
---

### Post by Aeolien on 2008-12-03
I'm setting up an Ubuntu box for my 85-year-old grandfather. He's never used a computer before and I have a very simple set up designed for him. The last thing I need to do is to remove the user's ability to right-click. How do I modify xorg.conf so that the right mouse button is also the left mouse button? I'm guessing that it has to do with the ButtonMapping option in the conf file, would this work?

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
# Added Option
Option "ButtonMapping "1 1"
#End of Add

        Option          "Emulate3Buttons"       "true"
EndSection
```

Also this is a global option, can I modify this for a given user, so that when I connect as an admin it doesn't do it? If I have to I'll go in and manually comment out the line, but it would be nice.

TIA

-Aeo

---

