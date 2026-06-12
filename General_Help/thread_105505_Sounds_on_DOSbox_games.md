---
title: "Sounds on DOSbox games"
date: 2005-12-18
forum: General Help
---

### Post by offby1 on 2005-12-18
I'm trying to get some old, old games working in DOSbox -- System Shock being the current one, but most of the old Origin games are on the list.  However, I am unable to get reasonable performance from both the sound and the game itself.  I'm running these on a P4 3.00 GHz with the following CV:

Kernel: ```
# uname -a
Linux deadbox 2.6.12-9-686-smp #1 SMP Mon Oct 10 13:36:57 BST 2005 i686 GNU/Linux

```
```
# lspci:
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.2 RAID bus controller: Intel Corp. 82801EB (ICH5R) SATA (cc=RAID) (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)
0000:02:07.0 FireWire (IEEE 1394): Lucent Microelectronics FW323 (rev 61)
0000:02:08.0 Ethernet controller: Intel Corp. 82562EZ 10/100 Ethernet Controller (rev 01)
```

dosboxrc:  Basically exactly the sample one that ships w/ dosbox, except:  ```
# gunzip -c /usr/share/doc/dosbox/dosbox.conf.example.gz | diff -u - /home/offline/.dosboxrc
--- -   2005-12-18 13:04:58.135025000 -0700
+++ /home/offline/.dosboxrc     2005-12-18 10:13:47.000000000 -0700
@@ -36,7 +36,7 @@
 language=
 machine=vga
 captures=capture
-memsize=16
+memsize=64

 [render]
 # frameskip -- How many frames dosbox skips before drawing one.
@@ -55,8 +55,8 @@
 # cycleup   -- Amount of cycles to increase/decrease with keycombo.
 # cycledown    Setting it lower than 100 will be a percentage.

-core=normal
-cycles=3000
+core=full
+cycles=12000
 cycleup=500
 cycledown=20

@@ -71,7 +71,7 @@

 nosound=false
 rate=22050
-blocksize=2048
+blocksize=4096
 prebuffer=10

 [midi]
@@ -85,7 +85,7 @@
 mpu401=true
 intelligent=true
 device=default
-config=
+config=62:0

 [sblaster]
 #==== Got completely rewritten in 0.63 ====
@@ -165,4 +165,7 @@
 [autoexec]
 # Lines in this section will be run at startup.

+mount -t cdrom d /home/offline/games/CD
+mount -t dir c /home/offline/games/installed_dos
+c:
```

I've got a sequencer set up (so I get midi) and I've tried both with and without ESD running, getting the same issue over and over again.  The sound plays for ~ 3/4 second, pauses for ~1/4 second, continues...  This is especially jarring in the intro.

Has anyone got any ideas as to what I can do to increase performance on this game?  A couple of potential issues that might be causing it (from what little I know) are: 
a) I still cannot get the ATI drivers to work correctly with my video card.  For some reason, it is not capable of using AGP.  This is... irritating :) 
b) I am using an SMP kernel with a HyperThreaded CPU.  It's possible that a non-SMP kernel would work better, which I'm going to try Real Soon Now.

Any other ideas would be grand.  Thanks.

---

### Post by joflow on 2005-12-18
How did you get dosbox installed?  Is it in the repo?  I'd love to play Ultima 8 in linux.

---

### Post by offby1 on 2005-12-18
I *think* it's in the repos -- I did just do apt-get install dosbox.  I imagine it's in multiverse, though

---

### Post by jobezone on 2006-01-14
> The sound plays for ~ 3/4 second, pauses for ~1/4 second, continues... 
That happens with me when I have the CPU cycles too high (with other games). Too low, and the game will become slow :/ Try lowering them nevertheless with the shortcut Ctrl+F11 inside dosbox(and increasing with Ctrl+F12), and see if you can find the perfect balance. Do this not in full screen, so you can see the current cycles in the dosbox window titlebar.
If you can't, you can allways disable sound, or increase the frameskip. Or increase the priority of dosbox (inside dosbox.conf)...Or some other way I don't know off...

---

