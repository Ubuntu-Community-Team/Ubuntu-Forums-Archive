---
title: "Screen goes black after splash"
date: 2008-12-26
forum: Desktop Environments
---

### Post by Globe_Abductee on 2008-12-26
Hi all, 

I'm having some problems with a new LCD monitor (Samsung SyncMaster T220) I bought a couple of weeks ago. 
When I boot using the default xorg.conf for Ubuntu 8.10 (which is as good as empty), I get an error saying "screens found, but none have a usable configuration. This brings me to a screen, where I can select "run ubuntu in low graphics mode, and some other options. When I choose this option, it restarts X, and my monitor works fine. It even uses its native resolution (1680*1050). 

I have tried several things to solve it myself, like installing the NVidia drivers, and then running nvidia-xconfig, which gives me a more complete xorg.conf, but when I boot after doing this, my screen goes black, and I can see my monitor continuously switching between analog and digital mode.

Some useful information:

This config makes X crash and gives the option menu:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

This gives me a blank screen, where I can here the sound of the login prompt:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "SyncMaster T220"
    UseModes       "Modes0"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Modes"
	Identifier "Modes0"
	### # 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
	Modeline "1680x1050" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync
	### # 720x400 59.55 Hz (CVT) hsync: 24.83 kHz; pclk: 22.25 MHz
	Modeline "720x400" 22.25 720 744 808 896 400 403 413 417 -hsync +vsync
	### # 256x341 59.09 Hz (CVT) hsync: 21.09 kHz; pclk: 6.75 MHz
	Modeline "256x341" 6.75 256 264 288 320 341 344 354 357 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
I've also tried this last one without the modes-section, with the same result.

xorg.0.log (only errors for brevity):
```

(EE) NV(0): No valid initial configuration found
(EE) Screen(s) found, but none have a usable configuration.

```


Output of lspci | grep 'VGA':
```

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)

```

I've also tried dpkg-reconfigure somewhere along the way, but that didn't help either.

I have no idea what else I can try, so I hope you guys (and girls) can help me out.

Thanks a lot!

---

### Post by higherspeed on 2008-12-27
I don't have any ideas to help you, but would like to report a similar problem.  I also have a T220, which worked fine when I first installed Ubuntu 8.10.  I have just updated everything using the update manager and now I find that once I get past the usplash screen everything goes nearly black, however there is some corruption in the upper half of the screen.

Booting in an older version of the kernel still works (2.6.27-7 rather than 2.6.27-9), so perhaps you could try that.

Although I actually think my problem is an fglrx problem and so not applicable to you, but perhaps they're somehow related.

```
Xorg.0.log.old:(EE) fglrx(0): [FB] Can not get FB MC address range.
Xorg.0.log.old:(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
Xorg.0.log.old:(EE) fglrx(0): XMM failed to open CMMQS connection.
```

Though the errors in my syslog are different.  I should note that I rebooted by pressing Ctrl-Alt-Backspace (in an attempt to restart the x-server).
```
Dec 27 10:47:45 dinsdale-desktop kernel: [ 2638.490944] compiz.real[1982] trap stack segment ip:41023f sp:7fff13a40800 error:0
Dec 27 10:47:45 dinsdale-desktop console-kit-daemon[5988]: WARNING: Unable to activate console: No such device or address
Dec 27 10:47:45 dinsdale-desktop init: tty4 main process (5374) killed by TERM signal
Dec 27 10:47:45 dinsdale-desktop init: tty5 main process (5375) killed by TERM signal
Dec 27 10:47:45 dinsdale-desktop init: tty2 main process (5378) killed by TERM signal
Dec 27 10:47:45 dinsdale-desktop init: tty3 main process (5380) killed by TERM signal
Dec 27 10:47:45 dinsdale-desktop init: tty6 main process (5382) killed by TERM signal
Dec 27 10:47:45 dinsdale-desktop init: tty1 main process (6457) killed by TERM signal
Dec 27 10:47:45 dinsdale-desktop bonobo-activation-server (jtg23-2283): could not associate with desktop session: Failed to connect to socket /tmp/dbus-zCFrHGq10o: Connection refused
Dec 27 10:47:48 dinsdale-desktop kernel: [ 2641.251942] ip6_tables: (C) 2000-2006 Netfilter Core Team
Dec 27 10:47:50 dinsdale-desktop bluetoothd[6147]: bridge pan0 removed
Dec 27 10:47:50 dinsdale-desktop bluetoothd[6147]: Stopping SDP server
Dec 27 10:47:50 dinsdale-desktop bluetoothd[6147]: Exit
Dec 27 10:47:50 dinsdale-desktop avahi-daemon[17878]: Got SIGTERM, quitting.
Dec 27 10:47:50 dinsdale-desktop avahi-daemon[17878]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.68.
Dec 27 10:47:50 dinsdale-desktop exiting on signal 15
```

Needless to say that I don't have a clue what's going on but decided to post on the offchance that it would be of any help.

---

### Post by TelmoCalhaco on 2008-12-27
I there same problem here , but when e connect do my LCD 32 with dual display , stays with display , to fix need to boot on safe mode and reconfigure the xserver

---

### Post by Globe_Abductee on 2008-12-27
I've given up for now, did some more reading, but no working solutions for now. I'll continue using vesa drivers for now, this at least let's me boot using the native resolution :)

---

### Post by Djzn.BR on 2010-06-23
I confirm this problem. Happens every now and then. Radeon HD 3200 IGP here.

---

