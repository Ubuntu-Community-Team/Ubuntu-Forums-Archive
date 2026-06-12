---
title: "Ati Card not working for Compiz"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by mikey12345 on 2007-11-03
Hi,

Hoping someone can help with this. I've got an ATi AGP Graphics card (quite old) and a copy of Ubuntu 7.10. I'm going to post the basic outputs below so hopefully someone can see what is wrong and help me.
(I'm getting the 'Desktop effects can not be enabled' error).
Thanks.




ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
ubuntu@ubuntu:~$ 



ubuntu@ubuntu:~$ cat /etc/X11/xorg.conf

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Rage 128 Pro Ultra TF"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "PLE430/431"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Rage 128 Pro Ultra TF"
        Monitor         "PLE430/431"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection
ubuntu@ubuntu:~$

---

### Post by Creazine on 2007-11-03
try this [http://ubuntuforums.org/archive/index.php/t-550082.html]("http://ubuntuforums.org/archive/index.php/t-550082.html")

---

### Post by Creazine on 2007-11-03
but i still thinking that old ati is bad reason to run compiz on newest ubuntu releases.
I got nvidia for a month (fired up it when installing cooler) and that was happy days with full 3d support and no problem at all. There are hard to find any cheap agp-nvidia card, but i suggest you to change you card. :-)

---

### Post by amadeus266 on 2007-11-03
My ATI 9200 runs Compiz but not all plugins work. Your card is probably just too old to run Compiz effectivly no matter how you set it up. I too would suggest replacing your card with something newer from Nvidia.

---

