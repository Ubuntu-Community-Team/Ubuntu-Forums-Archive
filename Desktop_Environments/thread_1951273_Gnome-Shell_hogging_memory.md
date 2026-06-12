---
title: "Gnome-Shell hogging memory?"
date: 2012-04-02
forum: Desktop Environments
---

### Post by lokutus25 on 2012-04-02
My Ubuntu 11.10 witch gnome-shell happen to fill the swap memory slowly but inexorably.
I have 3Gb of fisical ram and 4Gb of ram.
> 
$ free 
             total       used       free     shared    buffers     cached
Mem:       2682032    2574436     107596          0      13528     253636
-/+ buffers/cache:    2307272     374760
Swap:      3905532      85604    3819928
$ uptime
 13:34:24 up  4:50,  1 user,  load average: 0.18, 0.15, 0.14


This is happening lately and If I leave the PC switched on but idle, the same happen anyway.
Checking who's using my ram, most of the processes are from the gnome environment.

> 
PID=2961 - Swap used: 1508 - (nautilus )
PID=2858 - Swap used: 1776 - (gnome-session )
PID=2963 - Swap used: 2148 - (tomboy )
PID=3008 - Swap used: 2196 - (e-addressbook-f )
PID=1326 - Swap used: 2224 - (colord )
PID=2918 - Swap used: 2644 - (gnome-settings- )
PID=3052 - Swap used: 2888 - (thunderbird-bin )
PID=2849 - Swap used: 3024 - (gnome-keyring-d )
PID=2962 - Swap used: 3112 - (nm-applet )
PID=3011 - Swap used: 3276 - (goa-daemon )
PID=2932 - Swap used: 7364 - (gnome-shell )
PID=2597 - Swap used: 7564 - (bash )
PID=2742 - Swap used: 17352 - (Xorg )


Does anyone noticed this behavior?

---

### Post by lokutus25 on 2012-04-02
I forgot to mention that I use a two monitor environment...

---

