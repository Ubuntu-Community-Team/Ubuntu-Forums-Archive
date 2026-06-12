---
title: "Can't hear nothing..."
date: 2005-07-07
forum: Desktop Environments
---

### Post by Djeepy46234 on 2005-07-07
HiI just installed Ubuntu and I can't hear nothing. The sound is not working. When I play some music with some player (I tried 5 programs), I hear nothing and It's working on Windows.

And when I try to open Totem, I have this error message :

```
Resource busy or not available.
``` 

And it's closing.

Someone have an issue for this ?

---

### Post by bunced on 2005-07-07
What is your soundcard, please? It will help us to know this :D

---

### Post by Djeepy46234 on 2005-07-07
How am I suppose to know this .. ?

And BTW, I have this message with Kaffeine Player :

```
xine: cannot find input plugin for MRL [/media/sdb1/Music/Metal/Gamma Ray/03 - 1993 - Insanity And Genius - L/09 - Gamma Ray - Your Torn Is Over.mp3]
xine: input plugin cannot open MRL [/media/sdb1/Music/Metal/Gamma Ray/03 - 1993 - Insanity And Genius - L/09 - Gamma Ray - Your Torn Is Over.mp3]
input_file: File not found: >/media/sdb1/Music/Metal/Gamma Ray/03 - 1993 - Insanity And Genius - L/09 - Gamma Ray - Your Torn Is Over.mp3<
xine: found input plugin  : file input plugin
xine: cannot find input plugin for MRL []
xine: cannot find input plugin for MRL [/media/sdb1/Music/Metal/Gamma Ray/01 - 1989 - Heading For Tomorrow - L/09 - Gamma Ray - Heading For Tomorrow.mp3]
xine: input plugin cannot open MRL [/media/sdb1/Music/Metal/Gamma Ray/01 - 1989 - Heading For Tomorrow - L/09 - Gamma Ray - Heading For Tomorrow.mp3]
input_file: File not found: >/media/sdb1/Music/Metal/Gamma Ray/01 - 1989 - Heading For Tomorrow - L/09 - Gamma Ray - Heading For Tomorrow.mp3<
xine: found input plugin  : file input plugin
>>> Check if another program already uses PCM <<<
snd_pcm_open() failed:-2:Aucun fichier ou répertoire de ce type

```

---

### Post by Djeepy46234 on 2005-07-07
I need help please...

---

### Post by zoofields on 2005-07-08
To find out what sound card you have do

```
lspci
``` 

in terminal and tell us the output.

More importantly, however, what type of music are you trying to play?  Have you gone through the guide and installed all of the appropriate multimedia codecs?

---

### Post by Djeepy46234 on 2005-07-08
[QUOTE=zoofields]To find out what sound card you have do

```
lspci
``` 

in terminal and tell us the output.

More importantly, however, what type of music are you trying to play?  Have you gone through the guide and installed all of the appropriate multimedia codecs?[/QUOTE]
I have all the codecs, and for the music (MP3) and for Totem, it's only when i try to open the software ...

```
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev  04)
0000:00:02.0 VGA compatible controller: Intel Corp. 82915G Express Chipset Famil y Graphics Controller (rev 04)
0000:00:02.1 Display controller: Intel Corp. 82915G Express Chipset Family Graph ics Controller (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definiti on Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridg e (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contro ller (rev 03)
0000:02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev 80)
0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:02:05.0 Communication controller: Lucent Microelectronics V.92 56K WinModem  (rev 03)

```

---

