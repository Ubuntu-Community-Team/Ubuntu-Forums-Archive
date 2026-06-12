---
title: "No Extra Buttons or Scroll Wheel"
date: 2005-04-25
forum: Desktop Environments
---

### Post by Gwydion on 2005-04-25
Hello everyone.

I've just updated my work pc from XPsp2 to Ubuntu H. First off I really like how solid ubuntu is. I am very impressed with it. Now I am not a Linux newbie as I use Gentoo at home but this is my work PC. It is a Dell Optiplex SX 280 and a Microsoft wireless natural keyboard as well as a wireless MS Mouse.

The issue is the scroll wheel and the 2 thumb buttons do not work. Here is a part of my xorg.conf
     xorg.conf:
Section "InputDevice"

# Identifier and driver

    Identifier  "Mouse1"
    Driver      "mouse"
    Option "Protocol"    "ExplorerPS/2"
    Option "Device"      "/dev/input/mice"
    Option "Buttons" "7"
    Option "ZAxisMapping" "6 7"
...

The interesting thing is that when I run xev to see what buttons are there it only shows any information when I press buttons 1 2 or 3... the scroll wheel and the thumb buttons do not produce any results.

Now the keyboard and mouse is connected via USB as there are no ps/2 ports on this computer. 
The extra buttons were working fine in XP...

I've also included my lspci below 

0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corp. 82915G Express Chipset Family Graphics Controller (rev 04)
0000:00:02.1 Display controller: Intel Corp. 82915G Express Chipset Family Graphics Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

Any ideas as to what to try next?

---

### Post by woifi on 2005-04-25
go through this one: [http://ubuntuforums.org/showthread.php?t=28374](http://ubuntuforums.org/showthread.php?t=28374)

---

