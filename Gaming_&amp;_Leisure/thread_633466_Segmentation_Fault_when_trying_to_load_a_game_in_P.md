---
title: "Segmentation Fault when trying to load a game in PCSX2"
date: 2007-12-06
forum: Gaming &amp; Leisure
---

### Post by Sarteck on 2007-12-06
I have Final Fantasy X (original copy, not ISO or backup), and I've been trying to get it to work in PCSX2.  Either me or my machine must be doing soemthing wrong, though, because everytime I try to load it, the 640x480 window appears for a second, a black screen with the words (in yellow) at the top saying "bilinear filtering - normal" appears on the window, and then it crashes.

I was reading on the NGEmu forums about something called "gdp" and "backtraces," but I don't rightly know how to use them. ^^;  So if someone needs that info, just tell me how to go about giving it to you.

I compiled my PCSX2 by [barius' guide](http://ubuntuforums.org/showthread.php?t=631979), and it installed just fine.  This is the output in my terminal after the game crashes:```
sarteck@auron:~/pcsx2/bin$ ./play.sh

ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.3
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: Disabling MRT depth writing
ZeroGS: Creating effects
ZeroGS: Creating extra effects
ZeroGS: using accurate shaders
ZeroGS: initialization successful
./play.sh: line 3: 21185 Segmentation fault      (core dumped) LD_LIBRARY_PATH="./" ./pcsx2
```

Also, not sure if it makes a difference, but everytime I run the PCSX2 script, I have to change my keyboard settings, because it (somehow) disables my keyboard repeat.  O.o  Not sure what that's all about...

---

### Post by barius on 2007-12-06
This sounds like your BIOS is not being loaded, or maybe the path to the game ISO is too long (yes, there is a limitation).  Can you start the BIOS without a game (Run->Execute, click open without selecting anything).

Do you have the console enabled?  (i think it's under tools->console, or maybe misc->console).  Enable it and run PCSX2 from the command line to watch the output, it may give more clues.

You may get better help from the PCSX2 forums.

> **Sarteck said:**
> Also, not sure if it makes a difference, but everytime I run the PCSX2 script, I have to change my keyboard settings, because it (somehow) disables my keyboard repeat.  O.o  Not sure what that's all about...

I've seen the same thing though I've never been sure if was the script or PCSX2 itself.  I'll play around some tonight and see if I can rule out the script or not.

---

### Post by acoustibop on 2007-12-06
If you want to run gdb, Sarteck, cd into your application folder, enter 'gdb <your application>' and then enter 'run' to start the application.  After your application crashes, enter 'bt' to print out a stack traceback.

---

### Post by Sarteck on 2007-12-07
Okay, it did give a lot more info.  :)  Thanks to you both.  I will post the output here, but I'll also be Googling to see if I can find my own answer (and if so, I'll post that here as well).  Again, thanks for the nudge.


After enabling the Console:```
sarteck@auron:~$ ./pcsx2/bin/play.sh

        F1 - save state
        (Shift +) F2 - cycle states
        F3 - load state
        F10 - dump performance counters
        F11 - save GS state
        F12 - dump hardware registers
PCSX2 v0.9.5 save ver: 7a30000f
EE pc offset: 0x2a8, PSX pc offset: 0x208
x86Init:
        CPU vender name =  AuthenticAMD
        FamilyID        =  3
        x86Family =  AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
        CPU speed =  1.049 Ghz
        x86PType  =  Standard OEM
        x86Flags  =  178bfbff
        x86EFlags =  ebd3fbff
Features:
        Detected MMX
        Detected SSE
        Detected SSE2
        Not Detected SSE3
 Extented AMD Features:
        Detected MMX2
        Detected 3DNOW
        Detected 3DNOW2
gsInit
waiting for gsOpen
EE Recompiler data reset
Bios Version 1.60



**************
rom2 NOT FOUND
**************





**************
erom NOT FOUND
**************


GIF reset
NTSC
Framelimiter rate updated (UpdateVSyncRate): 60 fps
ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.3
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: Disabling MRT depth writing
ZeroGS: Creating effects
ZeroGS: Creating extra effects
ZeroGS: using accurate shaders
ZeroGS: initialization successful
gsOpen done
Starting GS thread
MTGS thread unlocked
loadElfFile: cdrom0:\SLUS_203.12;1
loadElfFile: 4615960
ElfProgram different load addrs: paddr=0x02000000, vaddr=0x00000000
loadElfFile: cdrom0:\SLUS_203.12;1; CRC = BB3D833A
ZeroGS: Disabling MRT depth writing
FIX ME: Level 2 cpuException
Reset request
NTSC
Framelimiter rate updated (UpdateVSyncRate): 60 fps
NTSC
Framelimiter rate updated (UpdateVSyncRate): 60 fps
# Initialize memory (rev:3.63, ctm:393Mhz, cpuclk:295Mhz detected)
Write to 32bit count reg counter 5
Counter 5 count write 0
# Total accessable memory size: 32 MB (B:2:8:0) (363:2:7c30)
# TLB spad=0 kernel=1:12 default=13:30 extended=31:38
# Initialize Start.
NTSC
Framelimiter rate updated (UpdateVSyncRate): 60 fps
NTSC
Framelimiter rate updated (UpdateVSyncRate): 60 fps
# Initialize GS ...
# Initialize INTC ...
# Initialize TIMER ...
# Initialize DMAC ...
# Initialize VU1 ...
# Initialize VIF1 ...
# Initialize GIF ...
# Initialize VU0 ...
# Initialize VIF0 ...
# Initialize IPU ...
# Initialize FPU ...
./pcsx2/bin/play.sh: line 3:  1417 Segmentation fault      (core dumped) LD_LIBRARY_PATH="./" ./pcsx2

```So you are right, I suppose--I must be missing "rom2" and "erom" for my BIOS.

I know, I must seem like an idiot for not realizing it was most likely the BIOS, but I've never had this thing running before, so I didn't know what to expect.  ^^;  (And those guys at the NGEmu forums seem so mean in their responses to other people, I thought I'd try my luck here first.)

Studying for a mind-numbing anatomy practical right now, so I'll tinker with it later, probably tomorrow after the practical.  Thanks again to both of you.  :)

---

### Post by barius on 2007-12-07
No, missing rom2/erom is not an issue.

It looks to me like there may be a new bug in the SVN.  After updating to the newest version I also get a segmentation fault, but only after closing the emulator.  I don't have any problems starting it or playing a game.  Also, the keyboard repeat problem seems to be related to this bug as my repeat setting is also getting reset after the segmentation fault.

Did you try running the BIOS on it's own?  (Run->Execute, and don't select anything).  There's a good chance that part of your problem is trying to load the game from a CD, testing the BIOS without a game would answer this question.

EDIT: I was wrong, I do get this same problem with an older revision I guess I just didn't notice before.  If your problem is the same as mine, then you should still be able to play games though.  Test the BIOS, and if that works then rip an ISO of your game and try running it that way instead.

---

### Post by Sarteck on 2007-12-07
Nope, I'm not able to load into the BIOS at all.  I tried using the CDVD Null plugin, then Run -> Execute, and it still crashed on me.  Since it seems to crash after the FPU is initialized, what is loaded after the FPU?

---

### Post by acoustibop on 2007-12-07
I think cdrom0 points to /media/cdrom0, which is the mounted CD.  Many emulators need to use /dev/<whatever device> where <whatever device> is cdrom/cdrom1/dvd/dvd1 etc.instead.  Personally I prefer to use hda/hdb/hdc/hdd for a drive on the IDE channels; this points to a specific drive (channel 0 master/channel 0 slave/channel1 master/channel1 slave respectively) rather than the cdrom/dvd assignations, which I've found can change the actual device they point to sometimes.  So you'd have /dev/hda, /dev/hdb etc.

Edit: on second thoughts, since your print out says "cdrom0:\SLUS_203.12;1," it would appear to be identifying the CD correctly.  So maybe that's not it.

---

### Post by barius on 2007-12-07
Go to the PCSX2 forums and post your computer specs and the settings you're using.  You'll probably find more help there.  Also read the config guide on their site ([www.pcsx2.net](www.pcsx2.net)) as I'm 90% sure this is just a configuration thing.

Edit: I still think this related to loading the CD.  Don't use the CDVD Null plugin, it's not very compatible.  Use the Linuzapps ISO plugin then open the BIOS using Run->Execute and when asked just hit 'open' without selecting anything.

---

