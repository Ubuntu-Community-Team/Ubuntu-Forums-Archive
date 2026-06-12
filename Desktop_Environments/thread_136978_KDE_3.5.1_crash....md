---
title: "KDE 3.5.1 crash..."
date: 2006-02-27
forum: Desktop Environments
---

### Post by KooT on 2006-02-27
Hello.
I have problem with KDE 3.5.1.
After upgrade and install xorg-driver-fglrx (i have ati radeon 9100 video card) my kde crash on start up - on dialog - "Setting up previous session"
I think its something wrong with fglrx driver becouse when i change it into 'ati' in xorg.conf its working ok - only i cant set up high refresh rate on my monitor.

Any idea what is wrong? And where can i find some kde logs to find out what is wrong?

Greetings from Poland ;)

---

### Post by ajgreeny on 2006-02-27
What happens if you change the session manager to start with an empty session instead of the default, which I think is "Restore previous session"?  If the problem is something running previously this may solve the crashes.

---

### Post by KooT on 2006-02-27
I have add new user and then startx, now its crash on 'setting up desktop'... :(

---

### Post by KooT on 2006-02-28
No other ideas? ;(

---

### Post by KooT on 2006-03-02
I found it in /var/log/daemon.log
```
 
Feb 28 18:01:47 localhost kdm_greet[8139]: Internal error: memory corruption detected
Feb 28 18:01:55 localhost kdm_greet[8786]: Can't open default user face
Feb 28 18:02:18 localhost kdm_greet[8786]: Internal error: memory corruption detected
Feb 28 18:02:20 localhost kdm_greet[8803]: Can't open default user face
Feb 28 18:02:47 localhost kdm_greet[8803]: Internal error: memory corruption detected
Feb 28 18:02:49 localhost kdm_greet[8820]: Can't open default user face
Feb 28 18:03:12 localhost kdm_greet[8820]: Internal error: memory corruption detected
Feb 28 18:03:15 localhost kdm_greet[8837]: Can't open default user face
Feb 28 18:03:19 localhost kdm_greet[8837]: Internal error: memory corruption detected

```

/var/log/kern.log 
```

Feb 28 18:03:02 localhost kernel: [4331263.456000] IPT INPUT packet died: IN=eth0 OUT= MAC=00:d0:09:e4:15:5f:00:30:4f:3b:49:50:08:00 SRC=221.8.179.98 DST=19
Feb 28 18:03:12 localhost kernel: [4331273.336000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Feb 28 18:03:12 localhost kernel: [4331273.336000] [fglrx] Have to use kernel AGP support to avoid conflicts.
Feb 28 18:03:12 localhost kernel: [4331273.336000] [fglrx] AGP detected, AgpState   = 0x1f000207 (hardware caps of chipset)
Feb 28 18:03:12 localhost kernel: [4331273.337000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Feb 28 18:03:12 localhost kernel: [4331273.337000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Feb 28 18:03:12 localhost kernel: [4331273.337000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Feb 28 18:03:12 localhost kernel: [4331273.337000] [fglrx] AGP enabled,  AgpCommand = 0x1f000304 (selected caps)
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] free  AGP = 54800384
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] max   AGP = 54800384
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] free  LFB = 49278976
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] max   LFB = 49278976
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] free  Inv = 0
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] max   Inv = 0
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] total Inv = 0
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] total TIM = 0
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] total FB  = 0
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] total AGP = 16384


```

and finaly /ver/log/Xorg.0.log

```


(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xd8d8b000
(II) fglrx(0): [drm] mapped SAREA 0xd8d8b000 to 0xb7b4e000
(II) fglrx(0): [drm] framebuffer handle = 0xc0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-10-k7
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xcfef0000
(II) fglrx(0): [agp] Mode=0x1f000207 bridge: 0x1039/0x0735
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000304
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000304)
(II) fglrx(0): [agp] graphics chipset has AGP v2.0
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xd8f01000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x00501000
(II) fglrx(0): Splitting WC range: base: 0xc0000000, size: 0x501000
(II) fglrx(0): Splitting WC range: base: 0xc0400000, size: 0x101000
(==) fglrx(0): Write-combining range (0xc0500000,0x1000)
(==) fglrx(0): Write-combining range (0xc0400000,0x101000)
(==) fglrx(0): Write-combining range (0xc0000000,0x501000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,1281)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 768)
(II) fglrx(0): Largest offscreen area available: 1024 x 505
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Solid Lines
        Dashed Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                24 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT


```

---

### Post by ErikDeBruijn on 2006-03-03
I had this problem (in Dapper Alpha 3, though) and I solved it by commenting out the last line (main()) of /usr/bin/displayconfig-restore

Your problem is probably different, but I found out how to fix it here:
~youruser/.xsessions-errors

If you look at that file, you might see syntax errors of some files, or configuration problems. If you fix those, you probably solve your problem!

Here's another good hint:
[http://lists.debian.org/debian-kde/2004/04/msg00337.html](http://lists.debian.org/debian-kde/2004/04/msg00337.html)

---

### Post by KooT on 2006-03-06
Thank You for response ;] 

Now kde starts ok but its crash when i try to run any programs...
Its strange to me... maybe its some kind of hardware problems... memory etc.. ;(

This is what i found in .xsession-errors 
```

Xsession: X session started for koot at nie mar  5 23:50:33 CET 2006
startkde: Starting up...
kbuildsycoca running...
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/kde3/kcm_keyboard.so: undefined symbol: init_keyboard_layout
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/kde3/kcm_kdnssd.so: undefined symbol: init_kdnssd
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/neko:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/neko:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/neko:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_media: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kbluetoothd: HciListener::HciListener()
kbluetoothd: WARNING: No usable bluetooth device found.
kbluetoothd: Using hci0 as default bluetooth device.
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: Nie ma takiego urz&#261;dzenia
kbluetoothd: TrayIcon::slotMruMenuUpdate
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: Nie ma takiego urz&#261;dzenia
kbluetoothd: Kbluetoothd: Error opening HCI socket
kbluetoothd: TrayIcon::slotMruMenuUpdate
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: Nie ma takiego urz&#261;dzenia
kio_system: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_trash: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kde-config: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_trash: WARNING: KLocale: trying to look up "" in catalog. Fix the program
Ignored duplicate item: Konqueror
Ignored duplicate item: Konqueror
Ignored duplicate item: Konqueror
Ignored duplicate item: Konqueror
Ignored duplicate item: KMail
Ignored duplicate item: Narz?dzie do zarz?dzania Portfelem
Ignored duplicate item: Konqueror
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: Nie ma takiego urz&#261;dzenia
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: Nie ma takiego urz&#261;dzenia
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: Nie ma takiego urz&#261;dzenia
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: Nie ma takiego urz&#261;dzenia
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: Nie ma takiego urz&#261;dzenia
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: Nie ma takiego urz&#261;dzenia
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: Nie ma takiego urz&#261;dzenia
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: Nie ma takiego urz&#261;dzenia
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: Nie ma takiego urz&#261;dzenia

```

---

