---
title: "ubuntu X server does not load correctly on boot"
date: 2019-07-04
forum: Desktop Environments
---

### Post by vanderaalle on 2019-07-04
[FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]Dear,[/FONT]
[FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]
[/FONT]
[FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]noob here. I have Ubuntu 18.04 on a fresh Dell XPS 13.[/FONT]
[FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]When I re/boot, most the time I reach login, I log in correctly, then a black screen appears, the mouse is active, but nothing more happens.[/FONT]
[FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]I solve, quite empirically, by alternating with wayland. Wayland seems ok, and after a switch typically (but not always) switching back to X server works.[/FONT]

By inspecting I get

lspci | grep VGA
->00:02.0 VGA compatible controller: Intel Corporation Device 3ea0
GUI dice
Intel® HD Graphics (Whiskey Lake 3x8 GT2)


sudo lshw -c video
->
*-display 
description: VGA compatible controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:158 memory:db000000-dbffffff memory:50000000-5fffffff ioport:3000(size=64) memory:c0000-dffff


Any idea?

thanks a lot

-a-

---

### Post by Claus7 on 2019-07-05
Hello,

check this out with the display manager problem: switching might solve your issue.
[https://ubuntuforums.org/showthread.php?t=2399714&p=13796083#post13796083](https://ubuntuforums.org/showthread.php?t=2399714&p=13796083#post13796083)

Regards!

---

### Post by vanderaalle on 2019-07-05
Thanks Claus, I had some troubles in following the discussion...
Anyway, I went here 
[URL="https://askubuntu.com/questions/829108/what-is-gdm3-kdm-lightdm-how-to-install-and-remove-them"]
https://askubuntu.com/questions/829108/what-is-gdm3-kdm-lightdm-how-to-install-and-remove-them[/URL]

and I was able to switch to lighdm

First login seems ok, fortunately.

Out of curiosity: is my issue a bug in gdm3?

Best

-a-

---

### Post by vanderaalle on 2019-07-05
BTW I had a random gigantic mouse pointer with lighdm, so I switched back to gdm3 at the moment, first login was fine

---

### Post by Claus7 on 2019-07-08
Hello,

> **vanderaalle said:**
> 
...
Out of curiosity: is my issue a bug in gdm3?

...

it seems that initial implementations of gdm3 caused some problems with some users. Reinstallation or purging completely and switching to lightdm seemed to solve problems related to login loops e.t.c. to many users. Nice that you have it up and running ok.

Regards!

---

