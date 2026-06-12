---
title: "How to run script on X startup"
date: 2009-07-07
forum: Desktop Environments
---

### Post by Ekeluo on 2009-07-07
Really just want the kdm alternative to this command. Basically, i want to execute /usr/local/bin/fixmtrr.sh EVERYTIME I login, at the same stage as in the line for GDM below (around or before X is started).

```
$ sudo ln -s /usr/local/bin/fixmtrr.sh /etc/gdm/PostLogin/Default
```

Any help is welcome

---

### Post by Ekeluo on 2009-07-07
What the script does is reassign/reallocate memory blocks for my intel gma 900 integrated graphics, so it has to run every time X starts. Hope this makes it more precise.

---

### Post by exploder on 2009-07-07
Here is how to run the script in Kubuntu.

Code: Select all
sudo wget [http://launchpadlibrarian.net/26193373/fixmtrr.sh](http://launchpadlibrarian.net/26193373/fixmtrr.sh) -O /usr/local/bin/fixmtrr.sh

Code: Select all
sudo chmod +x /usr/local/bin/fixmtrr.sh



This will download the fixmttr.sh in your bin folder so that you can run it from anywhere just typing fixmttr.sh in the konsole and second code will make it executable.

To create a symbolic link to autostart, enter these code in the konsole.
Code: Select all
sudo ln -s /usr/local/bin/fixmtrr.sh /home/<user>/.kde/Autostart


The Optimal fix and this script work the best for resolving the Intel issue in Kubuntu. The safe method was buggy on my system.

Edit: I copied this directly from my notes.

---

### Post by Ekeluo on 2009-08-05
Strange. I'm running a Compaq A900 now with 2gb ram & X3100, gl960 I believe, (see below). The settings seem ok without the fixmtrr script. I ran the script manually in a terminal and it did the allocating thing. Then I ran it again and it said it had been run already. I think this means it does not run on X startup. X was active for over 5 hrs before I ran it and no slow down, so I guess it works fine without. No tearing too. Definite step up from the gma 900.


```
chukwuogor@chukwuogor-laptop:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 2301
	Region 0: Memory at 91000000 (64-bit, non-prefetchable) [size=1M]
	Region 2: Memory at 80000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 30d0 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at 91100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>


```

---

### Post by bukzor on 2011-02-06
I'm pretty sure the correct (desktop-independant) way to do this is to put your commands in "~/.xsessionrc".

```
echo /usr/local/bin/fixmtrr.sh >> ~/.xsessionrc
```

---

