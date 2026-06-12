---
title: "Dell 1905FP Monitor, Scrolling Diagonal Lines"
date: 2005-07-15
forum: Desktop Environments
---

### Post by mad_scientist03 on 2005-07-15
I just installed Ubuntu 5.04, and there are a series of diagonal lines that scroll across the screen continuously. The monitor I am using is the Dell 1905FP. When I "lspci", I get the following information for my video card:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

I have another computer that I administer that runs Fedora Core 3, and it uses the Dell 1905FP monitor as well. With that setup, the monitor performs perfectly. I have tried to copy over as many of the settings from the xorg.conf file on the Fedora machine to the Ubuntu machine, but I still see diagonal lines on the monitor in the Ubuntu setup. Specifically, here is the "Monitor" section from the Ubuntu machine.

Section "Monitor"
        Identifier      "DELL 1905FP"
        VendorName      "DEL"
        ModelName       "Dell 1905FP (Digital)"
        Option          "DPMS"
        HorizSync       30.0 - 80.0
        VertRefresh     56.0 - 76.0
EndSection

By default, Ubuntu only gave me the Identifier and Option lines; I inserted the others manually. The HorizSync and VertRefresh match the values in the xorg.conf file on the Fedora machine, where the other 1905FP works perfectly. In other words, I'm pretty sure the error is not in the "Monitor" section of the xorg.conf file.

Where else should I be looking to fix this screen issue? I get a headache looking at the monitor after 30 seconds or so; in other words, it's not useable.

Thanks for any help you can provide.

---

### Post by rwabel on 2005-07-16
[QUOTE=mad_scientist03]I just installed Ubuntu 5.04, and there are a series of diagonal lines that scroll across the screen continuously. The monitor I am using is the Dell 1905FP. When I "lspci", I get the following information for my video card:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

I have another computer that I administer that runs Fedora Core 3, and it uses the Dell 1905FP monitor as well. With that setup, the monitor performs perfectly. I have tried to copy over as many of the settings from the xorg.conf file on the Fedora machine to the Ubuntu machine, but I still see diagonal lines on the monitor in the Ubuntu setup. Specifically, here is the "Monitor" section from the Ubuntu machine.

Section "Monitor"
        Identifier      "DELL 1905FP"
        VendorName      "DEL"
        ModelName       "Dell 1905FP (Digital)"
        Option          "DPMS"
        HorizSync       30.0 - 80.0
        VertRefresh     56.0 - 76.0
EndSection

By default, Ubuntu only gave me the Identifier and Option lines; I inserted the others manually. The HorizSync and VertRefresh match the values in the xorg.conf file on the Fedora machine, where the other 1905FP works perfectly. In other words, I'm pretty sure the error is not in the "Monitor" section of the xorg.conf file.

Where else should I be looking to fix this screen issue? I get a headache looking at the monitor after 30 seconds or so; in other words, it's not useable.

Thanks for any help you can provide.[/QUOTE]
 very strange, I've the same Monitor and never had problems!
Identifier, Option, HorizSync and VertRefresh should be enough. Vendor and Model isn't needed.

---

### Post by mad_scientist03 on 2005-07-18
[QUOTE=rwabel]very strange, I've the same Monitor and never had problems!
Identifier, Option, HorizSync and VertRefresh should be enough. Vendor and Model isn't needed.[/QUOTE]

Do the settings in my xorg.conf match yours? Could you post your xorg.conf file in its entirety so I could try to leverage the portions that should be the same on my machine?

Thanks for your time.

---

### Post by mad_scientist03 on 2005-07-18
I swapped video cards and now the display works fine. I don't know what the specific model of either video card is (they are both Rage chipsets, but beyond that I could not find much in the way of informative markings on the cards themselves).

I had them both using the default "ati" driver, as per the xorg.conf file, and for some reason the second card handles the driver much more nicely. I cannot get any other driver to work on either card. I installed the xorg-driver-fglrx package, but naively swapping "ati" with "fglrx" in the xorg.conf file would not work (the X server would not start and would point me to /var/log/Xorg.0.log for more information, which didn't help me out).

Regardless, everything seems to be working now, with the problem having been pinned on the (faulty?) graphics card.

---

### Post by rwabel on 2005-07-18
[QUOTE=mad_scientist03]Do the settings in my xorg.conf match yours? Could you post your xorg.conf file in its entirety so I could try to leverage the portions that should be the same on my machine?

Thanks for your time.[/QUOTE]

I've attached my xorg config

---

