---
title: "Pulseview error: Failed to get product string descriptor: LIBUSB_ERROR_TIMEOUT"
date: 2019-03-11
forum: Debian
---

### Post by x3ua on 2019-03-11
I'm using Debian Buster.

```

$ uname -a
Linux env 4.19.0-2-amd64 #1 SMP Debian 4.19.16-1 (2019-01-17) x86_64 GNU/Linux

```

```

$ pulseview
sr: chronovu-la: Failed to get product string descriptor: LIBUSB_ERROR_TIMEOUT.
sr: dreamsourcelab-dslogic: Failed to get manufacturer string descriptor: LIBUSB_ERROR_TIMEOUT.

```

```

$ sigrok-cli --scan
sr: resource: Failed to open resource 'dreamsourcelab-dslogic-plus-fx2.fw' (use loglevel 5/spew for details).
sr: dreamsourcelab-dslogic: Firmware upload failed for device 1.16 (logical), name dreamsourcelab-dslogic-plus-fx2.fw.
sr: testo: Failed to get manufacturer string descriptor: LIBUSB_ERROR_TIMEOUT.
sr: testo: Failed to get product string descriptor: LIBUSB_ERROR_TIMEOUT.
The following devices were found:
demo - Demo device with 12 channels: D0 D1 D2 D3 D4 D5 D6 D7 A0 A1 A2 A3
dreamsourcelab-dslogic - DreamSourceLab DSLogic Plus with 16 channels: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15

```

```

$ apt info pulseview
Package: pulseview
Version: 0.4.1-1+b1
Priority: optional
Section: electronics
Source: pulseview (0.4.1-1)
Maintainer: Debian Electronics Packaging Team <pkg-electronics-devel@alioth-lists.debian.net>
Installed-Size: 2,166 kB
Depends: libboost-filesystem1.67.0, libboost-serialization1.67.0, libboost-system1.67.0, libc6 (>= 2.27), libgcc1 (>= 1:3.0), libglib2.0-0 (>= 2.28.0), libglibmm-2.4-1v5 (>= 2.54.0), libqt5core5a (>= 5.11.0~rc1), libqt5gui5 (>= 5.2.0), libqt5svg5 (>= 5.6.0~beta), libqt5widgets5 (>= 5.11.0~rc1), libsigc++-2.0-0v5 (>= 2.10.0-2.1), libsigrok4, libsigrokcxx4, libsigrokdecode4, libstdc++6 (>= 6)
Homepage: http://sigrok.org/wiki/PulseView
Tag: uitoolkit::qt
Download-Size: 627 kB
APT-Manual-Installed: yes
APT-Sources: http://ftp.fi.debian.org/debian buster/main amd64 Packages
Description: sigrok logic analyzer, oscilloscope, and MSO GUI
 PulseView is a GUI for sigrok that supports logic analyzers, oscilloscopes,
 and MSOs.
 .
 It can acquire samples from a supported device and display them,
 load and display captures from existing sigrok *.sr files, as well
 as run protocol decoders and display their annotations.

```

---

