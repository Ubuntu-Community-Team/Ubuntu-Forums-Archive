---
title: "Ayuda para hacer un Multiseat"
date: 2020-09-02
forum: Centroamerica Team
---

### Post by steev_666 on 2020-09-02
Hola a todos vengo pidiendo ayuda y consejos para poder crear en linux un Multiseat

He visto multiples sitios pero todos difieren mucho de el como crearlos y la mayor parte son muy viejos, lo mas actual es usando loginctl, pero parece que no es posible crear con solo una VGA

Aun asi he leido un poco y puede que sea posible creando un servidor de x11 y sobre este mismo asignar cada display a un conjunto de Monitor/teclado/raton

pero no parece ser que se use loginctl mas bien es usando DISPLAY=:0, DISPLAY=:0.1 DISPLAY=:0.2 DISPLAY=:0.n, esto crearia una sesion de X individual en cada monitor pero no estoy muy seguro de como se crea


Este es mi HW

```
seat0
    Sessions: *2
     Devices:
          &#9500;&#9472;/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
          &#9474; input:input1 "Power Button"
          &#9500;&#9472;/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
          &#9474; input:input0 "Power Button"
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/drm/card0
          &#9474; [MASTER] drm:card0
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/drm/card0/card0-DP-1
          &#9474; &#9474; [MASTER] drm:card0-DP-1
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/drm/card0/card0-DP-2
          &#9474; &#9474; [MASTER] drm:card0-DP-2
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/drm/card0/card0-DVI-D-1
          &#9474; &#9474; [MASTER] drm:card0-DVI-D-1
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/drm/card0/card0-HDMI-A-1
          &#9474; &#9474; [MASTER] drm:card0-HDMI-A-1
          &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/drm/card0/card0-HDMI-A-2
          &#9474;   [MASTER] drm:card0-HDMI-A-2
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/drm/renderD128
          &#9474; drm:renderD128
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/graphics/fb0
          &#9474; graphics:fb0 "amdgpudrmfb"
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1
          &#9474; sound:card1 "HDMI"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input21
          &#9474; &#9474; input:input21 "HDA ATI HDMI HDMI/DP,pcm=3"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input22
          &#9474; &#9474; input:input22 "HDA ATI HDMI HDMI/DP,pcm=7"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input23
          &#9474; &#9474; input:input23 "HDA ATI HDMI HDMI/DP,pcm=8"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input24
          &#9474; &#9474; input:input24 "HDA ATI HDMI HDMI/DP,pcm=9"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input25
          &#9474; &#9474; input:input25 "HDA ATI HDMI HDMI/DP,pcm=10"
          &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input26
          &#9474;   input:input26 "HDA ATI HDMI HDMI/DP,pcm=11"
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:06.0/0000:04:00.0/usb8
          &#9474; usb:usb8
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:06.0/0000:04:00.0/usb9
          &#9474; usb:usb9
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:07.0/0000:05:00.0/usb10
          &#9474; usb:usb10
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:07.0/0000:05:00.0/usb11
          &#9474; usb:usb11
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:09.0/0000:06:00.0/usb12
          &#9474; usb:usb12
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:09.0/0000:06:00.0/usb13
          &#9474; usb:usb13
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:12.0/usb4
          &#9474; usb:usb4
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:12.2/usb1
          &#9474; usb:usb1
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/sound/card2
          &#9474; &#9474; sound:card2 "Audio"
          &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.5/0003:0B05:17A3.0001/input/input2
          &#9474;   input:input2 "ASUSTeK Computer Inc. ROG ThunderBolt Audio"
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5
          &#9474; usb:usb5
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/0003:1A2C:2D43.0002/input/input3
          &#9474; &#9474; input:input3 "SEMICO USB Keyboard"
          &#9474; &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/0003:1A2C:2D43.0002/input/input3/input3::capslock
          &#9474; &#9474; &#9474; leds:input3::capslock
          &#9474; &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/0003:1A2C:2D43.0002/input/input3/input3::compose
          &#9474; &#9474; &#9474; leds:input3::compose
          &#9474; &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/0003:1A2C:2D43.0002/input/input3/input3::kana
          &#9474; &#9474; &#9474; leds:input3::kana
          &#9474; &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/0003:1A2C:2D43.0002/input/input3/input3::numlock
          &#9474; &#9474; &#9474; leds:input3::numlock
          &#9474; &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/0003:1A2C:2D43.0002/input/input3/input3::scrolllock
          &#9474; &#9474;   leds:input3::scrolllock
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.1/0003:1A2C:2D43.0003/input/input4
          &#9474; &#9474; input:input4 "SEMICO USB Keyboard Consumer Control"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.1/0003:1A2C:2D43.0003/input/input5
          &#9474; &#9474; input:input5 "SEMICO USB Keyboard System Control"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.1/0003:1A2C:2D43.0003/input/input7
          &#9474; &#9474; input:input7 "SEMICO USB Keyboard"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.0/0003:046D:C24A.0004/input/input8
          &#9474; &#9474; input:input8 "Logitech Gaming Mouse G600"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.1/0003:046D:C24A.0005/input/input10
          &#9474; &#9474; input:input10 "Logitech Gaming Mouse G600"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.1/0003:046D:C24A.0005/input/input9
          &#9474; &#9474; input:input9 "Logitech Gaming Mouse G600 Keyboard"
          &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5
          &#9474;   usb:5-5
          &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5.3/5-5.3:1.0/0003:1532:001F.0008/input/input15
          &#9474;   &#9474; input:input15 "Razer Razer Naga Epic"
          &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5.3/5-5.3:1.1/0003:1532:001F.0009/input/input16
          &#9474;   &#9474; input:input16 "Razer Razer Naga Epic"
          &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5.4/5-5.4:1.0/0003:04F3:0103.000A/input/input17
          &#9474;   &#9474; input:input17 "HID 04f3:0103"
          &#9474;   &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5.4/5-5.4:1.0/0003:04F3:0103.000A/input/input17/input17::capslock
          &#9474;   &#9474; &#9474; leds:input17::capslock
          &#9474;   &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5.4/5-5.4:1.0/0003:04F3:0103.000A/input/input17/input17::numlock
          &#9474;   &#9474; &#9474; leds:input17::numlock
          &#9474;   &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5.4/5-5.4:1.0/0003:04F3:0103.000A/input/input17/input17::scrolllock
          &#9474;   &#9474;   leds:input17::scrolllock
          &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5.4/5-5.4:1.1/0003:04F3:0103.000B/input/input18
          &#9474;   &#9474; input:input18 "HID 04f3:0103 Consumer Control"
          &#9474;   &#9492;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5.4/5-5.4:1.1/0003:04F3:0103.000B/input/input19
          &#9474;     input:input19 "HID 04f3:0103 System Control"
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.2/usb2
          &#9474; usb:usb2
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card0
          &#9474; sound:card0 "SB"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card0/input27
          &#9474; &#9474; input:input27 "HDA ATI SB Front Mic"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card0/input28
          &#9474; &#9474; input:input28 "HDA ATI SB Rear Mic"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card0/input29
          &#9474; &#9474; input:input29 "HDA ATI SB Line"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card0/input30
          &#9474; &#9474; input:input30 "HDA ATI SB Line Out Front"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card0/input31
          &#9474; &#9474; input:input31 "HDA ATI SB Line Out Surround"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card0/input32
          &#9474; &#9474; input:input32 "HDA ATI SB Line Out CLFE"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card0/input33
          &#9474; &#9474; input:input33 "HDA ATI SB Line Out Side"
          &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card0/input34
          &#9474;   input:input34 "HDA ATI SB Front Headphone"
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.4/0000:08:05.0/leds/rt2800pci-phy0::assoc
          &#9474; leds:rt2800pci-phy0::assoc
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.4/0000:08:05.0/leds/rt2800pci-phy0::quality
          &#9474; leds:rt2800pci-phy0::quality
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.4/0000:08:05.0/leds/rt2800pci-phy0::radio
          &#9474; leds:rt2800pci-phy0::radio
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.5/usb6
          &#9474; usb:usb6
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:16.0/usb7
          &#9474; usb:usb7
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:16.0/usb7/7-4/7-4:1.0/0003:4555:1031.0006/input/input11
          &#9474; &#9474; input:input11 "HID 4555:1031"
          &#9474; &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:16.0/usb7/7-4/7-4:1.0/0003:4555:1031.0006/input/input11/input11::capslock
          &#9474; &#9474; &#9474; leds:input11::capslock
          &#9474; &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:16.0/usb7/7-4/7-4:1.0/0003:4555:1031.0006/input/input11/input11::numlock
          &#9474; &#9474; &#9474; leds:input11::numlock
          &#9474; &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:16.0/usb7/7-4/7-4:1.0/0003:4555:1031.0006/input/input11/input11::scrolllock
          &#9474; &#9474;   leds:input11::scrolllock
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:16.0/usb7/7-4/7-4:1.1/0003:4555:1031.0007/input/input12
          &#9474; &#9474; input:input12 "HID 4555:1031 Mouse"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:16.0/usb7/7-4/7-4:1.1/0003:4555:1031.0007/input/input13
          &#9474; &#9474; input:input13 "HID 4555:1031 Consumer Control"
          &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:16.0/usb7/7-4/7-4:1.1/0003:4555:1031.0007/input/input14
          &#9474;   input:input14 "HID 4555:1031 System Control"
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:16.2/usb3
          &#9474; usb:usb3
          &#9500;&#9472;/sys/devices/platform/eeepc-wmi/input/input20
          &#9474; input:input20 "Eee PC WMI hotkeys"
          &#9500;&#9472;/sys/devices/virtual/misc/rfkill
          &#9474; misc:rfkill
          &#9492;&#9472;/sys/devices/virtual/misc/uinput
            misc:uinput
```

lspci

```
lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD9x0/RX980 Host Bridge (rev 02)
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD890S/RD990 I/O Memory Management Unit (IOMMU)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GFX port 0)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 0)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 1)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 2)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 3)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 4)
00:0d.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP2 Port 0)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] (rev e1)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]
02:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
03:00.0 Ethernet controller: Intel Corporation 82583V Gigabit Network Connection
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
06:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
07:00.0 Power PC: Freescale Semiconductor Inc MPC8308 (rev 10)
08:05.0 Network controller: Ralink corp. RT3062 Wireless 802.11n 2T/2R
```

Espero alguien me pueda guiar en como debo hacerlo paso a paso

---

### Post by ajgreeny on 2020-09-02
*Thread moved to **Centroamerica Team**.* which is more appropriate and a better fit.

The section posted to is English language only.

---

