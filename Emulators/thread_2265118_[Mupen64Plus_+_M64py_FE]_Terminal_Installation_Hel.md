---
title: "[Mupen64Plus + M64py FE] Terminal Installation Help"
date: 2015-02-12
forum: Emulators
---

### Post by z3r0d4t4 on 2015-02-12
Hello!

After perusing the forums for several hours looking for specific help in installing a console emulator for my kids (specifically Mupen64Plus on Ubuntu 14.04 LTS), I have come to the official conclusion that I truly am making this harder than it really needs to be. So here's the breakdown.


[LIST=1]
[*]Initially I reverted to using Wine to emulate the Windows-based N64 program that I am most familiar with -- Project64. The process of installing both the application and Project64 program via the virtual desktop was relatively easy thanks to Ubuntu's Software Center. However...when it came to loading the actual ROM inside of the emulator, graphics became an issue. So for the fun of it I opened the terminal to reveal my display driver. (**configuration: _driver=i915_ latency=0**) 
[/LIST]
  ```
z3r0d4t4@HomeStudio:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:eff00000-eff7ffff ioport:eff8(size=8) memory:d0000000-dfffffff memory:efec0000-efefffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:eff80000-efffffff
```

...then I remembered how much of a pain in the keister it was to get the third-party plugins for Project64 to run ROMs at acceptable levels on my machine without dumping too many important textures. You know...those awesome graphics that make games such as Majora's Mask unplayable up to a point unless they are enabled? The Lens of Truth, for example, shows otherwise hidden interactive objects that are needed to progress further into the story. Needless to say, I have abandoned Project64 Wine emulation and have moved onto what many users here on the forum recommend -- Mupen64Plus. So let's install it from the repository.

```
$ sudo apt-get install mupen64plus
```
successful install...and then to update the package list...
```
$ sudo apt-get update
```
successful update...and then to upgrade...not sure if this is necessary...but why not?
```
$ sudo apt-get upgrade
```
...booting the program...
```
z3r0d4t4@HomeStudio:~$ mupen64plus
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Mupen64Plus Console User-Interface Version 2.0.0

UI-Console: attached to core library 'Mupen64Plus Core' version 2.0.0
UI-Console:             Includes support for Dynamic Recompiler.
UI-Console:             Includes support for MIPS r4300 Debugger.
UI-Console Error: no ROM filepath given
z3r0d4t4@HomeStudio:~$
```
OK, so it isn't recognizing the path to the ROM probably because I didn't type it in...whoops! Let's try the "drag-and-drop" method:
```
z3r0d4t4@HomeStudio:~$ '/home/z3r0d4t4/Desktop/MajorasMask.n64'
```
No dice...the terminal freezes for a few seconds and then returns to command line. 

What do you guys/gals think? *I am also attempting to install the M64py front end so I can skip the Terminal*...but why? Here my D620's specs:

**System Information:**

Ubuntu 14.04 (trusty)
GNOME: 3.8.4 (Ubuntu 2014-03-17)
Kernel: 3.13.0-45-generic (#74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015)
OS Type: Linux
GCC Version: 4.8 (x86_64-linux-gnu)
Xorg Version: 1.15.1 (10 December 2014  06:15:52PM)

**CPU** **& Memory:**

Model:         Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz
Frequency:  1000.000 MHz
L2 Cache:    4096 KB
Memory: 2GB DDR2

---

### Post by deadflowr on 2015-02-13
I'm not if sure you've ran the mupen64plus command and then the path to file separately or not, but they are to be combined into one line
```
mupen64plus /path/to/file
```

That said, if you want to try it with m64py go for it.
It's drastically improved, IMHO, over the last couple of years.

The command line method, while robust when you learn what to do, can be quite trying and tiring for some.

I think the base of your system to should handle it well, but I haven't any idea how well the gpu would be, as graphics card can vary in terms of performance from one to another...
But from memory, like the command line, m64py should have some easy to set settings to adjust various graphical elements, which should help render things better.
 Of course, I do not know if any of this is actually helpful at all...

---

