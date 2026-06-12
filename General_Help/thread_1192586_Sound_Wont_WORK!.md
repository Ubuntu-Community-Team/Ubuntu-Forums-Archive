---
title: "Sound Wont WORK!"
date: 2009-06-20
forum: General Help
---

### Post by Spaceman7o on 2009-06-20
Ok so my sound wont work and i need help NOT VIDEO i get video fine its the sound maybe its the audio driver i dono but i need help.

---

### Post by Spaceman7o on 2009-06-20
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LF-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

---

### Post by Spaceman7o on 2009-06-20
dosent matter got it someone posted this Here's the upshot:

2. Configure libao applications to use PulseAudio:
Code:

$ echo "default_driver=pulse" >~/.libao

3. Perform the following steps to remove obsolete configuration files, ensure "libflashsupport" is not installed & you have the all the necessary packages up-to-date:
Code:

$ rm -r ~/.pulse ~/.asoundrc*
$ sudo apt-get update && sudo apt-get dist-upgrade
$ sudo apt-get remove libflashsupport
$ sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio

NOTE: Choose Yes to allow unsigned packages to be installed.

4. Go to System/Preferences/Sound. Set all "Sound playback" options to "Autodetect", and set "Sound capture" to "ALSA".

5. Reboot for changes to take effect! also check psm is up full sometimes you dont get sound till then!

---

### Post by Yellow Pasque on 2009-06-20
Please don't cross-post: [http://ubuntuforums.org/showthread.php?t=1192534](http://ubuntuforums.org/showthread.php?t=1192534)

---

