---
title: "Just need a little advice on SLI"
date: 2007-04-28
forum: Desktop Environments
---

### Post by SirShaggy on 2007-04-28
I just built a new PC in time for Feisty. I have just installed Kubuntu 7.04 on this system.

Foxconn C51XEM2AA- 8EKRS2H Socket AM2 NVIDIA nForce 590 SLI motherboard
AMD Athlon 64 x2 5600+ CPU
Corsair XMS2 Dominator 2GB Kit PC2-6400 RAM Kit
Western Digital Raptor 1500ADFD 150GB Hard Drive
SAMSUNG SpinPoint T Series HD501LJ 500GB 7200 RPM SATA 3.0Gb/s Hard Drive
Hauppauge WinTV PVR-350 TV/FM Tuner Card
Turtle Beach Riviera 5.1 sound card
2 XFX 7900GS XXX PCI-Ex16 256MB graphics cards
Seasonic M12-500 500W PSU
all in an older Rosewill case with my existing CD, DVD, Zip and Floppy drives.

shaggy@shaggy-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7900 GS (rev a1)
02:08.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
02:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:0a.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 7900 GS (rev a1)
shaggy@shaggy-desktop:~$ lsusb
Bus 002 Device 006: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 002 Device 004: ID 0409:005a NEC Corp.
Bus 002 Device 001: ID 0000:0000
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp.
Bus 002 Device 007: ID 050d:0002 Belkin Components
Bus 001 Device 005: ID 046d:c043 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0471:0328 Philips
shaggy@shaggy-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 67
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping        : 3
cpu MHz         : 3174.245
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 6353.30
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 67
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping        : 3
cpu MHz         : 3174.245
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 6348.48
clflush size    : 64

**_Anyway, I have 2 7900GS cards setup in SLI. How do I tell if SLI is working?_**
**_Here's my xorg.conf._**


          Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7900 GS]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7900 GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "4095x4095" "1680x1680" "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "4095x4095" "1680x1680" "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "4095x4095" "1680x1680" "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "4095x4095" "1680x1680" "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "4095x4095" "1680x1680" "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "4095x4095" "1680x1680" "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection 

I just don't see anything in there for SLI or accelerated graphics. I am using the nvidia-glx-new driver, do I need anything else? Any help appreciated.
Sorry, that was a lot longer than I expected it to be!
SirShaggy

---

### Post by MichiganMan on 2007-05-23
> **SirShaggy said:**
> I just built a new PC in time for Feisty. I have just installed Kubuntu 7.04 on this system.

I just don't see anything in there for SLI or accelerated graphics. I am using the nvidia-glx-new driver, do I need anything else? Any help appreciated.
Sorry, that was a lot longer than I expected it to be!
SirShaggy

Really surprised no one's helped you yet.  I just came across this info myself a day or so ago.

You want to use the nvidia-xconfig utility in Terminal to add the appropriate option to your xorg file, I didn't see it in yours.  Use nvidia-xconfig --advanced-help to figure out which command you want.  After you reboot, you can check for SLI by going to the Nvidia Settings (I'm doing this using the Nvidia driver installed by Envy) Go down to the GPU's. There should be two listed no matter if you're in SLI or not, but if you are, you should see SLI in the Graphic Card Information.

Another way to check is look for SLI Enabled, or something to that effect in the Xorg.0.log in System Log viewer.

[This ]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-w.html")has also been a helpful read for me.

---

### Post by SirShaggy on 2007-05-31
It took me a while to notice you responded, THANK YOU! I got the information and will try it out. I can follow what you said pretty easily, now if my hardware cooperates, I'll be in business! I'll post back later.
SirShaggy

---

