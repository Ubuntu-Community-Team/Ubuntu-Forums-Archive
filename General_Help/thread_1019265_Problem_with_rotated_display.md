---
title: "Problem with rotated display"
date: 2008-12-22
forum: General Help
---

### Post by fatecris on 2008-12-22
I am using ubuntu 8.04 on two machines and on both when I rotate the display (system>screen resolution>rotation) I get the same result: the display does rotate properly but the graphics are really shaky. For example when I open a window it displays the background first then the title bar and eventually the content. To me it looks like that there is a problem with the graphic card.

For your information: one machine is using the Intel graphics  845 and the other one an ATI radeon X1600. I uninstalled compiz on my machine using the Intel 845G since I have read that there were some problems with this chipset on ubuntu 8.04. I did try to reconfigure xserver with:

```
dpkg-reconfigure xserver-xorg
```

but it does not change anything.

Here is my xorg file content on the machine using the intel 845G

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "pc104"
        Option          "XkbOptions"    "ctrl:swapcaps"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

Thanks in advance for any help

---

### Post by fatecris on 2008-12-29
Solved.

I just made a clean install with ubuntu 8.10.

On first boot, I entered in recovery mode (type ESC to see the grub) then I removed compiz with:

```

sudo apt-get remove compiz
sudo apt-get remove compiz-core

```

Reboot.

I tested vertical display to the right and left, and it works like a charm. :popcorn:

If the screens flickers try restarting the xserver with ctrl+alt+backspace or just reboot your box. Normally it should have kept in memory the last screen resolution.

---

