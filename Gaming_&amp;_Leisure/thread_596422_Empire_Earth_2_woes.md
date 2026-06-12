---
title: "Empire Earth 2 woes"
date: 2007-10-29
forum: Gaming &amp; Leisure
---

### Post by constchar* on 2007-10-29
My Empire Earth 2 installation on Wine using 0.9.48 and EE 1.2 (CD cracked but it's a legitimate game otherwise)
crashes when loading a map, well not really, EE2 exits with a
debugging dialog.

I'm running Ubuntu "Gutsy Gibbon" 7.10.

Here's my Konsole log:
```

fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:win:EnumDisplayDevicesW ((null),0,0x12bf6f8,0x00000000), stub!
fixme:d3d8:ValidateVertexShader (0x3a5e3ec (nil) (nil) 1 0x12bf32c): stub
fixme:imm:ImmReleaseContext (0x10024, 0x12b060): stub
fixme:d3d8:ValidateVertexShader (0x6a46c64 (nil) (nil) 1 0x12bf344): stub
fixme:d3d8:ValidatePixelShader (0x6a4709c (nil) 1 0x12bf36c): stub
err:d3d:IWineD3DDeviceImpl_Reset Cannot change the back buffer format yet

```

EE2's debug dialog:
```

 EXCEPTION:    ACCESS VIOLATION
  0x7bc4033a
  0x7bc405ee
  0x7bc41768
  0x7e6c5d07
  0x00a182e8
  0x00000000
  0x009062e0
  0xb59d5c06
EAX:08ee0000h ESI:08fe0038h
EBX:7bc8591ch EDI:00100018h
ECX:ff706224h EBP:012bf948h
EDX:090e0058h ESP:012bf910h
EIP:7bc4033ah EID:00000000h
SS: 0000007bh CS: 00000073h

```

Anyone have any ideas or experiencing this and how do I fix it?

I should probably mention Source-based games like Counter-Strike: Source
all work perfect just like in Windows, except for Half-Life 2 which started
freezing up upon starting a new game in .48.

Thanks!

---

### Post by carlosjuero on 2007-10-29
> **constchar* said:**
> My Empire Earth 2 installation on Wine using 0.9.48 and EE 1.2 (CD cracked but it's a legitimate game otherwise)
crashes when loading a map, well not really, EE2 exits with a
debugging dialog.

I'm running Ubuntu "Gutsy Gibbon" 7.10.

Here's my Konsole log:
```

fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:win:EnumDisplayDevicesW ((null),0,0x12bf6f8,0x00000000), stub!
fixme:d3d8:ValidateVertexShader (0x3a5e3ec (nil) (nil) 1 0x12bf32c): stub
fixme:imm:ImmReleaseContext (0x10024, 0x12b060): stub
fixme:d3d8:ValidateVertexShader (0x6a46c64 (nil) (nil) 1 0x12bf344): stub
fixme:d3d8:ValidatePixelShader (0x6a4709c (nil) 1 0x12bf36c): stub
err:d3d:IWineD3DDeviceImpl_Reset Cannot change the back buffer format yet

```

EE2's debug dialog:
```

 EXCEPTION:    ACCESS VIOLATION
  0x7bc4033a
  0x7bc405ee
  0x7bc41768
  0x7e6c5d07
  0x00a182e8
  0x00000000
  0x009062e0
  0xb59d5c06
EAX:08ee0000h ESI:08fe0038h
EBX:7bc8591ch EDI:00100018h
ECX:ff706224h EBP:012bf948h
EDX:090e0058h ESP:012bf910h
EIP:7bc4033ah EID:00000000h
SS: 0000007bh CS: 00000073h

```

Anyone have any ideas or experiencing this and how do I fix it?

I should probably mention Source-based games like Counter-Strike: Source
all work perfect just like in Windows, except for Half-Life 2 which started
freezing up upon starting a new game in .48.

Thanks!

Seems like results with EE2 are mixed (I couldn't even get it installed); Here is the AppDB page for it:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4439](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4439)

---

### Post by constchar* on 2007-10-29
Seems most people have rather successful with it.
I initially suspected that the creep might be "err:d3d:IWineD3DDeviceImpl_Reset Cannot change the back buffer format yet"
causing the problem, that is Wine refusing to cooperate with EE2 since
this had been the first time I saw that message in paticular, but it
would not explain why other users would be able to run EE2 unless of
course they were running the proprietary Cedega version.

---

