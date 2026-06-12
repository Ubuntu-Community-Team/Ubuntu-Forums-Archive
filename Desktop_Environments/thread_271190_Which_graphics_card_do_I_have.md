---
title: "Which graphics card do I have?"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Jordan Meeter on 2006-10-04
I'm following the steps at f and it gave me these options:> Drivers are typically named for the video card or chipset manufacturer, or
for a specific model or family of chipsets.
```

  1. apm     8. glint      15. newport    22. siliconmotion  29. vesa
  2. ark     9. i128       16. nsc        23. sis            30. vga
  3. ati     10. i740      17. nv         24. sisusb         31. via
  4. chips   11. i810      18. rendition  25. tdfx           32. vmware
  5. cirrus  12. imstt     19. s3         26. tga            33. voodoo
  6. cyrix   13. mga       20. s3virge    27. trident
  7. fbdev   14. neomagic  21. savage     28. tseng
[More]

```

Select the desired X server driver.


Here is my lspci - From this can you tell me what I should choose from the above list?> 0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
0000:01:08.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

---

### Post by someguyouknow on 2006-10-04
i am almost positive nv=nvidia
i am using it now

---

### Post by tturrisi on 2006-10-04
17

---

