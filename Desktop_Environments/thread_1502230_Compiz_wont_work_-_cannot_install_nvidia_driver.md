---
title: "Compiz wont work - cannot install nvidia driver"
date: 2010-06-05
forum: Desktop Environments
---

### Post by raigorodski on 2010-06-05
Hi Folks,

I cant run my compiz. After updating the nvidia driver (current) and rebooting, i got a menssage saying that X is not working properly. 


[B]Denis@denis-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GTX] (rev a2)[/B]

Follow xorg.conf log's:

[b](--) PCI:*(0:1:0:0) 10de:0612:1682:2373 nVidia Corporation G92 [GeForce 9800 GTX] rev 162, Mem @ 0xfc000000/16777216, 0xe0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log[/b]

And my xorg.conf:


[B]Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "LG"
	ModelName    "Flatron L196WTQ"
	HorizSync    30-83
	VertRefresh  56-75
	Option       "DPMS" "true"
EndSection

Section "Screen"
	Identifier      "Default Device"
	Option          "UseDisplayDevice"      "DFP-0"
	Device          "Configured Video Device"
	Monitor         "Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth           24
		Modes           "1440x900_60" "1920x1080_60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier "Configured Video Device"
	Boardname "GeForce 9800GTX"
	Busid "PCI:3:0:0"
	Option "ConnectedMonitor" "DFP-0"
	Option "IgnoreEDID" "TRUE"
	Option "UseEDID" "FALSE"
	Option "UseEDIDFreqs" "FALSE"
	Option "UseEDIDDpi" "FALSE"
	Option "ModeValidation" "NoEdidModes"
	Option "DPI" "96 x 96"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection[/B]

A little help please!!!

---

### Post by stderr on 2010-06-06
Which NVIDIA driver are you using? The one from the repositories or the latest binary driver from NVIDIA's site? 

If the binary driver, then most probably you installed a kernel update since, in which case the nvidia module needs recompiling for the new kernel. To do that, you can just run the NVIDIA installation script file again and reboot.

If it's from the repositories, then it may be a good idea to run a reinstall against the related nvidia-glx (or whatever they're called) packages to fire up DKMS.

---

### Post by denstorekalapojser on 2010-06-06
Open up Synaptic(System > Administration > Synaptic) search for nvidia-binary and find the X.org driver

---

### Post by wojox on 2010-06-06
Your xorg.conf looks kind of bare. Try running:

```
nvidia-xconfig
```

Which will save your current one and rebuild you a new one. Then configure it:

```
gksudo nvidia-settings
```

---

