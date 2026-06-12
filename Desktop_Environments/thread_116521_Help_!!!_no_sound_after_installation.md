---
title: "Help !!! no sound after installation"
date: 2006-01-12
forum: Desktop Environments
---

### Post by Jhodytropical on 2006-01-12
Hi all,

 I have no sound ; no card detected ; after installing the breezy Badger. Can someone tell me what to do please ?

Thanks in advance.

---

### Post by Ampersand on 2006-01-12
Try running
```
sudo alsaconf
```

What sound card is it?

---

### Post by Jhodytropical on 2006-01-12
[QUOTE=Ampersand]Try running
```
sudo alsaconf
```

What sound card is it?[/QUOTE]


I am using a Creative CT2502. and when I type "sudo alsaconf" I get the message " command not found"

---

### Post by FarEast on 2006-01-13
Hi;) ,

> I am using a Creative CT2502. and when I type "sudo alsaconf"
> I get the message " command not found"

There is no information of 'Creative CT2502' on the web below.
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

So you have to know which sound chip is on your sound card.
Execute the command and check if information of it is output.

$ lspci

If there is no information then...

$ sudo apt-get install isapnptools
$ sudo pnpdump > isabus.txt
$ cat isabus.txt

cf. Current package of 'alsa-utils' from Ubuntu team does not
contain the script 'alsaconf' .

---

### Post by Jhodytropical on 2006-01-13
> **FarEast]Hi said:**
> http://www.alsa-project.org/alsa-doc/[/url]

So you have to know which sound chip is on your sound card.
Execute the command and check if information of it is output.

$ lspci

If there is no information then...

$ sudo apt-get install isapnptools
$ sudo pnpdump > isabus.txt
$ cat isabus.txt

cf. Current package of 'alsa-utils' from Ubuntu team does not
contain the script 'alsaconf' .


Thanks for your answer. Here's the output of the commands I hope that helps: 

1. jean@ubuntu:~$ lspci

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:0e.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 05)
0000:00:14.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200 AGP (rev 01)

2. jean@ubuntu:~$ sudo apt-get install isapnptools

Reading package lists... Done
Building dependency tree... Done
isapnptools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

3. jean@ubuntu:~$ sudo pnpdump > isabus.txt

4.   jean@ubuntu:~$  cat isabus.txt
# $Id: pnpdump_main.c,v 1.27 2001/04/30 21:54:53 fox Exp $
# Release isapnptools-1.26
#
# This is free software, see the sources for details.
# This software has NO WARRANTY, use at your OWN RISK
#
# For details of the output file format, see isapnp.conf(5)
#
# For latest information and FAQ on isapnp and pnpdump see:
# [http://www.roestock.demon.co.uk/isapnptools/](http://www.roestock.demon.co.uk/isapnptools/)
#
# Compiler flags:  -DREALTIME -DHAVE_PROC -DENABLE_PCI -DHAVE_SCHED_SETSCHEDULER -DHAVE_NANOSLEEP -DWANT_TO_VALIDATE
#
# Trying port address 0273
# Board 1 has serial identifier 4c 00 00 bf 35 49 00 8c 0e

# (DEBUG)
(READPORT 0x0273)
(ISOLATE PRESERVE)
(IDENTIFY *)
(VERBOSITY 2)
(CONFLICT (IO FATAL)(IRQ FATAL)(DMA FATAL)(MEM FATAL)) # or WARNING

# Card 1: (serial identifier 4c 00 00 bf 35 49 00 8c 0e)
# Vendor Id CTL0049, Serial Number 48949, checksum 0x4C.
# Version 1.0, Vendor version 1.0
# ANSI string -->Creative SB32 PnP<--
#
# Logical device id CTL0031
#     Device supports vendor reserved register @ 0x38
#     Device supports vendor reserved register @ 0x3b
#     Device supports vendor reserved register @ 0x3c
#     Device supports vendor reserved register @ 0x3d
#
# Edit the entries below to uncomment out the configuration required.
# Note that only the first value of any range is given, this may be changed if required
# Don't forget to uncomment the activate (ACT Y) when happy

(CONFIGURE CTL0049/48949 (LD 0
#     ANSI string -->Audio<--

# Multiple choice time, choose one only !

#     Start dependent functions: priority preferred
#       IRQ 5.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 1.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 1))
#       Next DMA channel 5.
#             16 bit DMA only
#             Logical device is not a bus master
#             DMA may not execute in count by byte mode
#             DMA may execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 1 (CHANNEL 5))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0220
#             IO base alignment 1 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0330
#             Maximum IO base address 0x0330
#             IO base alignment 1 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0330))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0388
#             Maximum IO base address 0x0388
#             IO base alignment 1 bytes
#             Number of IO addresses required: 4
# (IO 2 (SIZE 4) (BASE 0x0388))

#       Start dependent functions: priority acceptable
#       IRQ 5, 7 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Next DMA channel 5, 6 or 7.
#             16 bit DMA only
#             Logical device is not a bus master
#             DMA may not execute in count by byte mode
#             DMA may execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 1 (CHANNEL 5))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0300
#             Maximum IO base address 0x0330
#             IO base alignment 48 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0300))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0388
#             Maximum IO base address 0x0388
#             IO base alignment 1 bytes
#             Number of IO addresses required: 4
# (IO 2 (SIZE 4) (BASE 0x0388))

#       Start dependent functions: priority acceptable
#       IRQ 5, 7 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Next DMA channel 5, 6 or 7.
#             16 bit DMA only
#             Logical device is not a bus master
#             DMA may not execute in count by byte mode
#             DMA may execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 1 (CHANNEL 5))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0300
#             Maximum IO base address 0x0330
#             IO base alignment 48 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0300))

#       Start dependent functions: priority functional
#       IRQ 5, 7 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Next DMA channel 5, 6 or 7.
#             16 bit DMA only
#             Logical device is not a bus master
#             DMA may not execute in count by byte mode
#             DMA may execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 1 (CHANNEL 5))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))

#       Start dependent functions: priority functional
#       IRQ 5, 7 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0300
#             Maximum IO base address 0x0330
#             IO base alignment 48 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0300))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0388
#             Maximum IO base address 0x0388
#             IO base alignment 1 bytes
#             Number of IO addresses required: 4
# (IO 2 (SIZE 4) (BASE 0x0388))

#       Start dependent functions: priority functional
#       IRQ 5, 7 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0300
#             Maximum IO base address 0x0330
#             IO base alignment 48 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0300))

#       Start dependent functions: priority functional
#       IRQ 5, 7, 10 or 11.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))

#     End dependent functions
 (NAME "CTL0049/48949[0]{Audio               }")
# (ACT Y)
))
#
# Logical device id PNPffff
#     Device supports vendor reserved register @ 0x38
#     Device supports vendor reserved register @ 0x3b
#     Device supports vendor reserved register @ 0x3c
#     Device supports vendor reserved register @ 0x3d
#
# Edit the entries below to uncomment out the configuration required.
# Note that only the first value of any range is given, this may be changed if required
# Don't forget to uncomment the activate (ACT Y) when happy

(CONFIGURE CTL0049/48949 (LD 1
#     ANSI string -->Reserved<--
#     Logical device decodes 16 bit IO address lines
#         Minimum IO base address 0x0100
#         Maximum IO base address 0x03f8
#         IO base alignment 8 bytes
#         Number of IO addresses required: 1
# (IO 0 (SIZE 1) (BASE 0x0100))
 (NAME "CTL0049/48949[1]{Reserved            }")
# (ACT Y)
))
#
# Logical device id CTL0021
#     Device supports vendor reserved register @ 0x38
#     Device supports vendor reserved register @ 0x3b
#     Device supports vendor reserved register @ 0x3c
#     Device supports vendor reserved register @ 0x3d
#
# Edit the entries below to uncomment out the configuration required.
# Note that only the first value of any range is given, this may be changed if required
# Don't forget to uncomment the activate (ACT Y) when happy

(CONFIGURE CTL0049/48949 (LD 2
#     ANSI string -->WaveTable<--

# Multiple choice time, choose one only !

#     Start dependent functions: priority preferred
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0620
#             Maximum IO base address 0x0620
#             IO base alignment 1 bytes
#             Number of IO addresses required: 4
# (IO 0 (SIZE 4) (BASE 0x0620))

#       Start dependent functions: priority acceptable
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0620
#             Maximum IO base address 0x0680
#             IO base alignment 32 bytes
#             Number of IO addresses required: 4
# (IO 0 (SIZE 4) (BASE 0x0620))

#     End dependent functions
 (NAME "CTL0049/48949[2]{WaveTable           }")
# (ACT Y)
))
#
# Logical device id CTL7001
#     Device supports vendor reserved register @ 0x38
#     Device supports vendor reserved register @ 0x3b
#     Device supports vendor reserved register @ 0x3c
#     Device supports vendor reserved register @ 0x3d
#
# Edit the entries below to uncomment out the configuration required.
# Note that only the first value of any range is given, this may be changed if required
# Don't forget to uncomment the activate (ACT Y) when happy

(CONFIGURE CTL0049/48949 (LD 3
#     Compatible device id PNPb02f
#     ANSI string -->Game<--
#     Logical device decodes 16 bit IO address lines
#         Minimum IO base address 0x0200
#         Maximum IO base address 0x0200
#         IO base alignment 1 bytes
#         Number of IO addresses required: 8
# (IO 0 (SIZE 8) (BASE 0x0200))
 (NAME "CTL0049/48949[3]{Game                }")
# (ACT Y)
))
#
# Logical device id CTL0051
#     Device supports vendor reserved register @ 0x38
#     Device supports vendor reserved register @ 0x3b
#     Device supports vendor reserved register @ 0x3c
#     Device supports vendor reserved register @ 0x3d
#
# Edit the entries below to uncomment out the configuration required.
# Note that only the first value of any range is given, this may be changed if required
# Don't forget to uncomment the activate (ACT Y) when happy

(CONFIGURE CTL0049/48949 (LD 4
#     ANSI string -->StereoEnhance<--
#     Logical device decodes 16 bit IO address lines
#         Minimum IO base address 0x0100
#         Maximum IO base address 0x03f8
#         IO base alignment 8 bytes
#         Number of IO addresses required: 1
# (IO 0 (SIZE 1) (BASE 0x0100))
 (NAME "CTL0049/48949[4]{StereoEnhance       }")
# (ACT Y)
))
# End tag... Checksum 0x00 (OK)

# Returns all cards to the "Wait for Key" state
(WAITFORKEY)

===========================

 After all this I restarted the PC, still no sound. Any idea why ?

---

### Post by FarEast on 2006-01-13
Hi,

pnpdump just collected information of devices on ISA Bus.
Reading the information, we have to make out how to set up
the sound card.  It will take some time before I can give you
a suggestion.

regards;)

---

### Post by Jhodytropical on 2006-01-13
[QUOTE=FarEast]Hi,

pnpdump just collected information of devices on ISA Bus.
Reading the information, we have to make out how to set up
the sound card.  It will take some time before I can give you
a suggestion.

regards;)[/QUOTE]

Thanks,

 Any suggestion is welcome. I just want it to work and enjoy my music again.

---

### Post by FarEast on 2006-01-14
Hi Jhodytropical,

> Any suggestion is welcome. I just want it to work and enjoy my music [COLOR="Red"]again[/COLOR].

Do you mean that you could get sound on earlier version of Ubuntu?
If so, do you remember which module was loaded then?

According to the output from 'pnpdump' and the description in the web below, it seems that your sound chip can be driven by 'snd-sbawe'.

[http://www.alsa-project.org/alsa-doc/index.php?vendor=.%23vendor-Creative_Labs.1.1.1.1#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=.%23vendor-Creative_Labs.1.1.1.1#matrix)

First, please try below;) .
$ sudo modprobe snd-sbawe

Perhaps error messages will appear.  The issue was discussed recently in the thread below and Zimmer's suggestion(#6) was successful.

[http://ubuntuforums.org/showthread.php?t=103180&highlight=snd-sb16](http://ubuntuforums.org/showthread.php?t=103180&highlight=snd-sb16)

I am sure you will understand what it was: assigning IRQ 5 and 11 to ISA plug-and-play devices.  So you have to enter BIOS setting screen on boot.

I hope this helps.

---

### Post by Jhodytropical on 2006-01-15
> **FarEast]Hi Jhodytropical,

> Any suggestion is welcome. I just want it to work and enjoy my music [COLOR="Red"]again[/COLOR].

Do you mean that you could get sound on earlier version of Ubuntu?
If so, do you remember which module was loaded then?

According to the output from 'pnpdump' and the description in the web below, it seems that your sound chip can be driven by 'snd-sbawe'.

[http://www.alsa-project.org/alsa-doc/index.php?vendor=.%23vendor-Creative_Labs.1.1.1.1#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=.%23vendor-Creative_Labs.1.1.1.1#matrix)

First, please try below said:**
> http://ubuntuforums.org/showthread.php?t=103180&highlight=snd-sb16[/url]

I am sure you will understand what it was: assigning IRQ 5 and 11 to ISA plug-and-play devices.  So you have to enter BIOS setting screen on boot.

I hope this helps.

Thanks for the help that you are providing me with my sound system. 

The comannd "$ sudo modprobe snd-sbawe" seems to work but I still have one problem

 1. when I type it on the terminal  and then I go to "System-Preferences-Sound" in the default sound Card I can see "the sound blaster 16" . But if I reboot the PC it's not there anymore I have to redo it manually again. (I don't know how to start it automatically ... any suggestions ? )

And I also  notice when my MP3 files are playing at times there is a distortion that I don't seem to have on the Windows base PCs.

Any hints on how I can solve this 2 problems ?

---

### Post by FarEast on 2006-01-16
Hi Jhodytropical,

> I don't know how to start it automatically ... any suggestions ?

Add an item 'snd-sbawe' in /etc/modules .
Then the module is loaded automatically on boot.

> And I also notice when my MP3 files are playing at times there is a
> distortion that I don't seem to have on the Windows base PCs.

I have never used SB AWE on Linux.  So I am not sure whether you
are the case,  but some sound cards do not have the same capability
on Linux to that they have on Windows.  I have a loptop with a sound
chip(esssolo1) on ISA bus.  I cannot listen to mp3 files at all though I
can hear other system sounds:( .

---

### Post by Jhodytropical on 2006-01-16
[QUOTE=FarEast]Hi Jhodytropical,

> I don't know how to start it automatically ... any suggestions ?

Add an item 'snd-sbawe' in /etc/modules .
Then the module is loaded automatically on boot.

> And I also notice when my MP3 files are playing at times there is a
> distortion that I don't seem to have on the Windows base PCs.

I have never used SB AWE on Linux.  So I am not sure whether you
are the case,  but some sound cards do not have the same capability
on Linux to that they have on Windows.  I have a loptop with a sound
chip(esssolo1) on ISA bus.  I cannot listen to mp3 files at all though I
can hear other system sounds:( .[/QUOTE]

Thanks for your help!!!

 I am so impressed by Ubuntu that I decide to do a dual boot on my Laptop (Gateway 7326GZ- 3GHz, 512 RAM 80GB HD) my Wireless card which is a Broadcom BCM4306 and my Sound are not working . Maybe you can help also.

People like you make Linux worth trying and Windows worth avoiding

---

### Post by FarEast on 2006-01-16
Hi Jhodytropical,

> Thanks for your help!!!

You are welcome.  I love Linux world where people help each other:p .


> my Wireless card which is a Broadcom BCM4306 and my Sound are
> not working . Maybe you can help also.

I have found an article by a guy in my country.  He says that he could
get  BCM4306 to work, with ndiswrapper. 

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

### Post by FarEast on 2006-01-17
I forgot to write;) 
Now you can remove the package 'isapnptools' by executing:
```
$ sudo dpkg -r isapnptools
```

---

