---
title: "Dell Optiplex 170L hanging..."
date: 2008-12-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cliff1983 on 2008-12-03
Dell Optiplex 170L
2.8GHz Celeron
1024MB Ram.
Ubuntu 8.04

Cache Memory

    * Type L2 cache
    * Installed Size 256.0 KB
    * Cache Per Processor 256 KB

Mainboard

    * Chipset type Intel 865GV
    * Data bus speed 533.0 MHz

RAM

    * Installed Size 256.0 MB / 2.0 GB (max)
    * Technology DDR SDRAM
    * Memory speed 333.0 MHz
    * Memory specification compliance PC2700
    * RAM form factor DIMM 184-pin
    * RAM features Two DDR channels

Graphics Controller

    * Type Integrated
    * Graphics Processor / Vendor Intel Extreme Graphics
    * Video Memory Dynamic Video Memory Technology 2.0



My problem is when i try to shut down for the day.  I connect to the internet through my buddies server at home to bypass Websense(this is at school).  When i log off his server at the end of the day(usually about 4 hours) and try to shut down, the computer hangs.  Keyboard does NOT respond, but the mouse does.  this is when i try clicking on the shutdown button at the top right of the screen.  Once it's locked up, the only way out is to unplug the tower.  My buddy that runs the server that i log into is in the same class as me and i'm running an exacty copy of his OS, but he doesn't have any issues with it.

Some help on this would be great.

Thanks in advance

---

### Post by andreasis on 2008-12-04
In order to begin identifying the problem, I would try two things first:

Ctrl+Alt+F2

sudo /etc/init.d/gdm stop
(to stop gnome display manager)

reboot
(to reboot, and then immediately afterwards, press Ctrl+Alt+F2 again, which should bring you away from the nice ubuntu shutdown visual, back to the console)

if everything works smoothly, it is a good sign.  if it doesn't note the error and research it and/or post it on here.

also, check your system log right after you attempt to shut down. If it mentions some errors that you cannot fix yourself, post the details on here.

As I understand it, you don't get as far as the ubuntu shutdown splash, so the problem most likely lies in one of the programs that are running in gnome.

Let's see what you're able to come up with

---

