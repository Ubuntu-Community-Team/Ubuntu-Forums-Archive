---
title: "Graphic tablet - hide cursor pointer when stilus moving(ubuntu 16)"
date: 2017-01-27
forum: Desktop Environments
---

### Post by fotogoot on 2017-01-27
Tablet work. Work ability check in gimp - where brush cursor appears, pressing force is work. But in other programs and system interface - cursor pointer hiding after moving stilus above tablet surface, buttons and stilus work in right places, but cursor pointer unvisible.
Help me. How make cursor pointer visible?!

```

# lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 005 Device 002: ID 09da:000e A4Tech Co., Ltd. X-F710F Optical Mouse 3xFire Gaming Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 005: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter
Bus 010 Device 004: ID 5543:0081 UC-Logic Technology Corp. 
Bus 010 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 010 Device 002: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




# cat /proc/bus/input/devices | grep TAB
N: Name="UC-LOIC TABLET 1060"
N: Name="UC-LOIC TABLET 1060"
N: Name="UC-LOIC TABLET 1060"




# xinput list
&#9121; Virtual core pointer                       id=2   [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                 id=4   [slave  pointer  (2)]
&#9116;   &#8627; UC-LOIC TABLET 1060                        id=8   [slave  pointer  (2)]
&#9116;   &#8627; UC-LOIC TABLET 1060                        id=9   [slave  pointer  (2)]
&#9116;   &#8627; UC-LOIC TABLET 1060                        id=10   [slave  pointer  (2)]
&#9116;   &#8627; A4Tech PS/2+USB Mouse                      id=11   [slave  pointer  (2)]
&#9116;   &#8627; SIGMACHIP USB Keyboard                     id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                      id=3   [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                id=5   [slave  keyboard (3)]
    &#8627; Power Button                               id=6   [slave  keyboard (3)]
    &#8627; Power Button                               id=7   [slave  keyboard (3)]
    &#8627; SIGMACHIP USB Keyboard                     id=12   [slave  keyboard (3)]
    &#8627; UVC Camera (046d:0825)                     id=14   [slave  keyboard (3)]








# xsetpointer -l
2: "Virtual core pointer"   [XPointer]
3: "Virtual core keyboard"   [XKeyboard]
4: "Virtual core XTEST pointer"   [XExtensionPointer]
5: "Virtual core XTEST keyboard"   [XExtensionKeyboard]
6: "Power Button"   [XExtensionKeyboard]
7: "Power Button"   [XExtensionKeyboard]
8: "UC-LOIC TABLET 1060"   [XExtensionPointer]
9: "UC-LOIC TABLET 1060"   [XExtensionPointer]
10: "UC-LOIC TABLET 1060"   [XExtensionPointer]
11: "A4Tech PS/2+USB Mouse"   [XExtensionPointer]
12: "SIGMACHIP USB Keyboard"   [XExtensionKeyboard]
13: "SIGMACHIP USB Keyboard"   [XExtensionPointer]
14: "UVC Camera (046d:0825)"   [XExtensionKeyboard]




# xinput list-props 8
Device 'UC-LOIC TABLET 1060':
   Device Enabled (152):   1
   Coordinate Transformation Matrix (154):   1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
   Device Accel Profile (280):   0
   Device Accel Constant Deceleration (281):   1.000000
   Device Accel Adaptive Deceleration (282):   1.000000
   Device Accel Velocity Scaling (283):   10.000000
   Device Product ID (272):   21827, 129
   Device Node (273):   "/dev/input/event5"
   Evdev Axis Inversion (284):   0, 0
   Evdev Axis Calibration (285):   <no items>
   Evdev Axes Swap (286):   0
   Axis Labels (287):   "Abs X" (277), "Abs Y" (278), "Abs Pressure" (279)
   Button Labels (288):   "Button Left" (155), "Button Middle" (156), "Button Right" (157), "Button Wheel Up" (158), "Button Wheel Down" (159)
   Evdev Scrolling Distance (289):   0, 0, 0
   Evdev Middle Button Emulation (290):   0
   Evdev Middle Button Timeout (291):   50
   Evdev Third Button Emulation (292):   0
   Evdev Third Button Emulation Timeout (293):   1000
   Evdev Third Button Emulation Button (294):   3
   Evdev Third Button Emulation Threshold (295):   20
   Evdev Wheel Emulation (296):   0
   Evdev Wheel Emulation Axes (297):   0, 0, 4, 5
   Evdev Wheel Emulation Inertia (298):   10
   Evdev Wheel Emulation Timeout (299):   200
   Evdev Wheel Emulation Button (300):   4
   Evdev Drag Lock Buttons (301):   0




# xinput test 9
motion a[0]=1029 a[1]=937 
motion a[1]=940 
motion a[1]=943 
motion a[1]=946 
motion a[1]=948 
motion a[0]=1031 
motion a[1]=951 
motion a[0]=1032 
motion a[1]=953 
motion a[1]=956 
motion a[0]=1034 a[1]=953
```

---

### Post by wildmanne39 on 2017-01-28
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

