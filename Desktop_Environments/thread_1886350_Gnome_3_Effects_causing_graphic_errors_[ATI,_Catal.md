---
title: "Gnome 3 Effects causing graphic errors [ATI, Catalyst]"
date: 2011-11-24
forum: Desktop Environments
---

### Post by geryzeck on 2011-11-24
Ubuntu 11.10 32bit

hey folks, 

due to the search function i know that there has already been a great discussion about all this gnome 3 graphic issue stuff.
but i guess my case i something different as i couldnt find any similar threads

i'm runnin a:
```
VGA compatible controller: ATI Technologies Inc Device 9806 (prog-if 00 
[VGA controller])
        Subsystem: Hewlett-Packard Company Device 3387
        Flags: bus master, fast devsel, latency 0, IRQ 43
        Memory at 80000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 4000 [size=256]
        Memory at 90300000 (32-bit, non-prefetchable) [size=256K]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <
?>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx, radeon
```as i really hate unity i prefered to install the gnome 3 stuff (kernel, shell etc.) and i'm really getting into it after a while but every time the systems makes use of the graphic effects like the notifier (notify-osd) or any other kind of graphic animation i'm getting massive pixel /graphic errors on the screen and sometimes even the whole shell crashes and automatically restarts.. kind of weird i dunno.

so i thought it might have something to do with ATI Catalyst Driver (i'm running the latest 11-11 version, released on 11-15-11)
but what other kind of driver can i use instead? i really would like to use gnome 3 without the graphic issues because its really annoying having your desktop crashed every 10 minutes..

i already tried this stuff but it wont work either..
[https://wiki.archlinux.org/index.php/GNOME#ATI_Catalyst_driver_creates_glitches_and_artifacts](https://wiki.archlinux.org/index.php/GNOME#ATI_Catalyst_driver_creates_glitches_and_artifacts)

any suggestions?

thank u so much:popcorn:


//edit:
alright, as i found out its because of the world famous shiddy ATI / AMD Driver Service
[HTML]http://ati.cchtml.com/show_bug.cgi?id=99[/HTML]seems like a whole bunch of people has the same issue.. well as experience tells me, they dont care anyway..
so i would like to know if anybody has an idea how i can change to another, working driver..

---

### Post by typhoon_tip on 2011-11-24
Definitely ATI problem, we are all in the same boat pal:
[http://ati.cchtml.com/show_bug.cgi?id=99](http://ati.cchtml.com/show_bug.cgi?id=99)

(long long page loll)

Hopefully it will be fixed in the 11.12 release that is due to be out in December, but as there's no feedback yet from AMD I don't really know...

---

### Post by geryzeck on 2011-11-25
alright dude.. i got it..
i hope these ati guys finally solve this problem next month.. 
seems to be an issue since 11-2 (omg, that's ten fukin months..) :evil:

but ain't there any other drivers for ati graphics on ubuntu? i mean common.. can't be possible that we are all depending on those atiamd guys..

what about this radeonhd and xf86-video-ati driver stuff?

any suggestion?

---

### Post by GERGE on 2011-11-25
The problem was much much worse in the beginning, they are solving it. Very slowly but they are solving.

---

