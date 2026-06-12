---
title: "no sound after upgrade on Optiplex GX1"
date: 2009-07-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Paul_Di on 2009-07-18
[FONT=Arial]Installed Ubuntu 9.04 on Optiplex GX1 but get no sound. I had previously installed Kubuntu 8.04 and added snd-cs4236 to /etc/modules which made the sound work fine, but the same fix doesn't seem to work on the new Ubuntu version. Searched similar posts but no luck so far. Maybe this information may give a clue?

aplay -l :-
[/FONT] 	 	 [FONT=Arial]**** List of PLAYBACK Hardware Devices ****
card 0: CS4236B [CS4236B], device 0: WSS [CS4236B]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/FONT] [FONT=Arial]lspci :-
[/FONT] 	 	 [FONT=Arial]00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0d.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0d.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0d.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

Tried running alsaconf but it is not found.


[/FONT] [FONT=Arial]
[/FONT]

---

### Post by Paul_Di on 2009-07-20
Problem sorted after reference to [http://ubuntuforums.org/showthread.php?t=1140821&highlight=sound+gx1](http://ubuntuforums.org/showthread.php?t=1140821&highlight=sound+gx1) summarised as:-
1) Edit etc/modules to add snd-cs4236 (which alone works on Hardy)
2) System-Admin-Users and Groups-Unlock-Properties-User Priviledges, tick "Use audio devices".  It seems odd to me that this should be disabled by default.
3) Reboot (or maybe log out and back in).
3) System-Preferences-Sound-Devices, set boxes to OSS except Default Mixer Tracks, set it to CS4236B (Alsa mixer). 

Good luck!

---

