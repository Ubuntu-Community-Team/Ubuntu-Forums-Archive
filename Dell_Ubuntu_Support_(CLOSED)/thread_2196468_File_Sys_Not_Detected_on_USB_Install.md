---
title: "File Sys Not Detected on USB Install"
date: 2013-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tk007LwZFJW5ej on 2013-12-29
I'm trying to install 12.04 x64 on the second HD of a Dell XPS 17 laptop from USB. I made the USB with the Startup Disk Creator utility. I get the error 

```
Unable to find a medium containing a live file system.
```

if I try to install or check for errors.

The checksum matches. I've changed my boot order to boot order is USB, HD1, HD2, CD drive (there are other options after that, not sure if that matters). My SATA configuration was already set to AHCI in BIOS when I went to try changing it. Tried all the usb ports; the one I've been using is the only one that works at all (the others boot to blank screen). Made sure no other USB devices were plugged in. I've tried setting all the boot options at once, as well as edd=on by itself, as well as edd=on and acpi=off.

What else can I try?

---

