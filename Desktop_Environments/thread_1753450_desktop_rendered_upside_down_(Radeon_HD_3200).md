---
title: "desktop rendered upside down (Radeon HD 3200)"
date: 2011-05-09
forum: Desktop Environments
---

### Post by GraysonPeddie on 2011-05-09
When the desktop effects are turned on by default, my desktop is rendered upside down, although the task bar stays at the bottom, even though the favorites bar got cropped off by the panel. Here, I'll demonstrate:

[[IMG]http://img835.imageshack.us/img835/2508/desktopupsidedown.th.png[/IMG]](http://img835.imageshack.us/i/desktopupsidedown.png/)

Desktop is now rendered properly without desktop effects enabled, as a workaround. Removing .kde or renaming .kde to .kdebackup will not fix the problem. Same as for .config.

```
grayson@HTPC:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
04:06.0 Multimedia audio controller: Creative Labs SB X-Fi
04:07.0 Multimedia controller: Motorola DSP56361 Digital Signal Processor (rev 01)
grayson@HTPC:~$ lsmod
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  0 
lirc_imon              18155  0 
joydev                 17606  0 
rndis_wlan             37363  0 
snd_ctxfi             105792  2 
snd_echo3g             38836  2 
cfg80211              178528  1 rndis_wlan
snd_pcm                96625  2 snd_ctxfi,snd_echo3g
rc_imon_pad            12505  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_echo3g,snd_seq_midi
usbhid                 46956  0 
imon                   32345  0 
ir_lirc_codec          12898  0 
lirc_dev               19232  2 lirc_imon,ir_lirc_codec
psmouse                73535  0 
edac_core              53845  0 
ir_sony_decoder        12549  0 
k8temp                 13016  0 
edac_mce_amd           23464  0 
ir_jvc_decoder         12546  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ir_rc6_decoder         12546  0 
serio_raw              13166  0 
rndis_host             13801  1 rndis_wlan
cdc_ether              13208  1 rndis_host
ir_rc5_decoder         12546  0 
hid                    91020  1 usbhid
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12546  0 
usbnet                 26165  3 rndis_wlan,rndis_host,cdc_ether
snd_timer              29602  2 snd_pcm,snd_seq
rc_core                26918  9 rc_imon_pad,imon,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  15 snd_ctxfi,snd_echo3g,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_ctxfi,snd_echo3g,snd_pcm
sp5100_tco             13744  0 
i2c_piix4              13303  0 
shpchp                 37297  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
radeon                982197  2 
ttm                    76664  1 radeon
drm_kms_helper         42136  1 radeon
ahci                   25951  5 
r8169                  48022  0 
drm                   227495  4 radeon,ttm,drm_kms_helper
pata_jmicron           12747  0 
libahci                26642  1 ahci
i2c_algo_bit           13400  1 radeon
pata_atiixp            13165  0 
grayson@HTPC:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "dri2"
        Load  "glx"
        Load  "dbe"
        Load  "extmod"
        Load  "dri"
        Load  "record"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        #DisplaySize      710   400     # mm
        Identifier   "Monitor0"
        VendorName   "GSM"
        ModelName    "LG TV"
        HorizSync    31.0 - 82.0
        VertRefresh  57.0 - 63.0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "Dac8Bit"                   # [<bool>]
        #Option     "BusType"                   # [<str>]
        #Option     "CPPIOMode"                 # [<bool>]
        #Option     "CPusecTimeout"             # <i>
        #Option     "AGPMode"                   # <i>
        #Option     "AGPFastWrite"              # [<bool>]
        #Option     "AGPSize"                   # <i>
        #Option     "GARTSize"                  # <i>
        #Option     "RingSize"                  # <i>
        #Option     "BufferSize"                # <i>
        #Option     "EnableDepthMoves"          # [<bool>]
        #Option     "EnablePageFlip"            # [<bool>]
        #Option     "NoBackBuffer"              # [<bool>]
        #Option     "DMAForXv"                  # [<bool>]
        #Option     "FBTexPercent"              # <i>
        #Option     "DepthBits"                 # <i>
        #Option     "PCIAPERSize"               # <i>
        #Option     "AccelDFS"                  # [<bool>]
        #Option     "IgnoreEDID"                # [<bool>]
        #Option     "CustomEDID"                # [<str>]
        #Option     "DisplayPriority"           # [<str>]
        #Option     "PanelSize"                 # [<str>]
        #Option     "ForceMinDotClock"          # <freq>
        #Option     "ColorTiling"               # [<bool>]
        #Option     "VideoKey"                  # <i>
        #Option     "RageTheatreCrystal"        # <i>
        #Option     "RageTheatreTunerPort"      # <i>
        #Option     "RageTheatreCompositePort"  # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"                 # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"               # <i>
        #Option     "RenderAccel"               # [<bool>]
        #Option     "SubPixelOrder"             # [<str>]
        #Option     "ClockGating"               # [<bool>]
        #Option     "VGAAccess"                 # [<bool>]
        #Option     "ReverseDDC"                # [<bool>]
        #Option     "LVDSProbePLL"              # [<bool>]
        #Option     "AccelMethod"               # <str>
        #Option     "DRI"                       # [<bool>]
        #Option     "ConnectorTable"            # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"            # [<bool>]
        #Option     "TVDACLoadDetect"           # [<bool>]
        #Option     "ForceTVOut"                # [<bool>]
        #Option     "TVStandard"                # <str>
        #Option     "IgnoreLidStatus"           # [<bool>]
        #Option     "DefaultTVDACAdj"           # [<bool>]
        #Option     "Int10"                     # [<bool>]
        #Option     "EXAVSync"                  # [<bool>]
        #Option     "ATOMTVOut"                 # [<bool>]
        #Option     "R4xxATOM"                  # [<bool>]
        #Option     "ForceLowPowerMode"         # [<bool>]
        #Option     "DynamicPM"                 # [<bool>]
        #Option     "NewPLL"                    # [<bool>]
        #Option     "ZaphodHeads"               # <str>
        Identifier  "Card0"
        Driver      "radeon"
        BusID       "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

grayson@HTPC:~$ apt-cache policy xserver-xorg
xserver-xorg:
  Installed: 1:7.6+4ubuntu3
  Candidate: 1:7.6+4ubuntu3
  Version table:
 *** 1:7.6+4ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ natty/main amd64 Packages
        100 /var/lib/dpkg/status
grayson@HTPC:~$ apt-cache policy xserver-xorg-video-radeon
xserver-xorg-video-radeon:
  Installed: 1:6.14.99+git20110508.90abffbd-0ubuntu0sarvatt
  Candidate: 1:6.14.99+git20110508.90abffbd-0ubuntu0sarvatt
  Version table:
 *** 1:6.14.99+git20110508.90abffbd-0ubuntu0sarvatt 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ natty/main amd64 Packages
        100 /var/lib/dpkg/status
     1:6.14.0-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ natty/main amd64 Packages
grayson@HTPC:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00f1 Microsoft Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 006: ID 045e:0027 Microsoft Corp. SideWinder PnP GamePad
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0537:0602 Inventec Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
grayson@HTPC:~$
```

I currently have an ECS A780GM-A Ultra motherboard.

If xorg.conf were not generated, my monitor will report "no signal" (it's an LG 50PK950 50" Plasma). In Kubuntu 10.10, it does not need xorg.conf to function and my desktop does not get rendered upside down.

I am running Kubuntu 11.04 and this is with and without ppa:xorg-edgers/ppa.

By the way, I've a strange problem with my mouse. When I move my mouse, my mouse pointer appears; when I stop moving my mouse, it disappears. Plus, one thing I've just noticed, although unrelated to my mouse problems, is that when type in a URL in a Firefox's address bar, Even though I used to type fast, the insertion point stops after a few seconds. And somehow, I can't do Ctrl+W to close a tab unless I do Ctrl+Tab twice to switch to another tab and then do Ctrl+Tab once more to switch back and then either continue to type or close a tab. I'm using Firefox 4.0.1, if that helps. But then I could've started a new thread about my problems with my mouse and Firefox. Oh well. It just seems to me that Kubuntu 11.04 is causing more problems with my setup than it's worth, but I'm willing to keep my fingers crossed and get help for fixing my problems.

[size=4]Update as of 5/9/11 7:12 AM:[/size]

My problem above (except for the mouse and Firefox) must be very similar to [the bug filed in plasma-bugs](http://osdir.com/ml/plasma-bugs/2010-12/msg00663.html), although mine could be a driver issue, but that's in 11.04 and not 10.10. My bug could be marked as dupricate if filed in plasma-bugs.

---

### Post by GraysonPeddie on 2011-05-10
I thought I'd like to bump up my thread with a question: Other than my problems with my mouse and my issue with Firefox, do you think my thread qualifies as a bug report?

I'm hoping to get a response to my problem with kwin desktop effects rendering my desktop upside down.

---

