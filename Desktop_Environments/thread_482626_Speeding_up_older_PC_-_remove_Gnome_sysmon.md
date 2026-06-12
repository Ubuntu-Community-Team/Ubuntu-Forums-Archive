---
title: "Speeding up older PC - remove Gnome sysmon"
date: 2007-06-23
forum: Desktop Environments
---

### Post by NJC on 2007-06-23
My Mighty PIII/500Mhz is a bit of dog running Gnome ... I've recently tried the Xubuntu desktop and would recommend it to anyone running older hardware. And ... I have always used Gnome System Monitor because I'm interested to monitor CPU/RAM and network bandwidth. 

Under top, Gnome sysmon didn't seem to soak up much processing power. BUT Xorg was using ~30-40% at IDLE! Under Xubuntu top reported Xorg to use ~20% CPU at idle. So I canned Gnome System Monitor and now, under Xubuntu, Xorg soaks up <5% CPU.\\:D/

I haven't taken the time to understand Xorg's function but it appears video intensive (to older hardware). My MGA200 w/ 8 megs is overloaded.

SO ... I pass along this great revelation: If running older hardware AND using Gnome System Monitor but noticing laggy performance, stop the process and see if speed gains are noticed. Here's another thread of mine with a screenshot using Gnome Sysmon under Gnome Desktop:

[http://ubuntuforums.org/showthread.php?t=412364](http://ubuntuforums.org/showthread.php?t=412364)

---

### Post by kerry_s on 2007-06-23
you should go custom and ditch the desktops all together. then if you really want speed you should go custom-minimal-debian.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

with debian, you can use the same instructions.

[http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso)

i use a minimal debin+fluxbox on 450mhz 256ram my system loads fully in 37sec's. ;)

---

