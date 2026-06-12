---
title: "suspend / resume"
date: 2007-05-10
forum: Desktop Environments
---

### Post by kornelix on 2007-05-10
I have a desktop system with an Intel D975XBX motherboard and nVidia
graphics card. I have gotten suspend/resume to work for the first time with 
Ubuntu 7.04. 

There seems to be no documentation on how to do this (except for some 
outdated stuff that does not work). After searching around and trying various 
things, I got the following combination to work:

file  /etc/default/acpi-support
```
    
   ACPI_SLEEP=true        
   ACPI_SLEEP_MODE=standby
   MODULES="agpgart"        
   SAVE_VBE_STATE=false        
   POST_VIDEO=false        
   USE_DPMS=false        

```file  /etc/X11/xorg.conf            
```
    
Section "Device"
    Driver       "nvidia"
      ...
    Option      "NvAGP"  "1"
EndSection

```This black magic works for me, and hopefully for some other folks out there in
Ubuntu land. I will watch this space in hopes someone more informed will
elucidate more.

I have another PC with an MSI motherboard that worked on the first try with 
default everything.

---

