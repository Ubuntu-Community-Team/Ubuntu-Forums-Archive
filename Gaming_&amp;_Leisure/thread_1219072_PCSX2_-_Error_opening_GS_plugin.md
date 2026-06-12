---
title: "PCSX2 - Error opening GS plugin"
date: 2009-07-21
forum: Gaming &amp; Leisure
---

### Post by Raff1 on 2009-07-21
Hello! I am mucking about with the ps2 emulator pcsx2 without being able to run my .iso-file..

I get following error message when opening an ISO-file with Linuzappz Iso CDVD  0.7.0:

```
Error opening GS plugin
```

The terminal output is as follows:

```
_openfile /[path]/my_iso_ff12.ISO 0
detected blocksize = 2048
isoOpen: /[path]/my_iso_ff12.ISO ok
offset = 0
blockofs = 24
blocksize = 2048
blocks = 1976656
type = 2
ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.2
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: ******
ZeroGS: GS WARNING: Floating point render targets not supported, switching to 32bit
ZeroGS: *********
ZeroGS: Disabling MRT depth writing
```

The .iso I am trying to run is Final Fantasy XII, which I succeeded to run on a windows computer.

After a lot of searching this was the most relevant information I could find:

> Note: If you got an error message saying *error opening gs plugin* or something like that, most likely you’re trying to use ZeroGS Plugin and your vga card is not a pixel shader 2.0 Capable Card (ZeroGS require Pixel Shader 2.0 ++ Capable Card)


My graphics card:

```
lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

So is my VGA pixel shader 2.0 Capable? I have no idea how I can find that out. And if it is, are you able to see what is going wrong here? The swiching to 32 bits is not a big deal..?

I really hope you can help me out, I have spent the last two days trying to get this working now and haven't been able to find any relevant posts (I could figure out at least..).

Regards, Raff1

---

