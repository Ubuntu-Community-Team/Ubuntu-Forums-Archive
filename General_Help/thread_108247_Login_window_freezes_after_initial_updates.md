---
title: "Login window freezes after initial updates"
date: 2005-12-25
forum: General Help
---

### Post by jcc on 2005-12-25
I successfully installed breezy on an Inspiron 3800.  (I'm sorry, I don't know the video card, etc. right off the top of my head, but it seems many people have had no problem installing to variations of this model.)  I downloaded/installed the updates it detected (about 40).  It recommended a reboot because of the new kernel --  After the reboot, I freeze at the login screen.

Specifically, I get the graphical login screen and the drumroll sound.  For a very brief second, I see the cursor flashing and I can move the mouse.  Then, it's frozen -- keyboard and mouse do nothing, including attempting to get to an alternate terminal.

I'm willing to work though this and follow documentation online, but I don't know where to begin.  Please point me in the right direction.

---

### Post by zoiks on 2005-12-25
I don't know what the problem is, but try booting from a live CD (knoppix or ubuntu live) and examining the contents of /var/log/messages in the unbootable system, and see what is going on up to the point of failure.  There's an excellent chance this will tell you what's wrong.  Try posting the relevant lines here.  Also you might try looking at /var/log/Xorg.0.log.

---

### Post by jcc on 2005-12-25
ubuntu@ubuntu:/media/linux_part/var/log$ tail messages
Dec 25 13:06:55 localhost kernel: [4294724.564000] ACPI: Battery Slot [BAT0] (battery present)
Dec 25 13:06:55 localhost kernel: [4294724.565000] ACPI: Battery Slot [BAT1] (battery absent)
Dec 25 13:06:55 localhost kernel: [4294724.640000] ACPI: Lid Switch [LID]
Dec 25 13:06:55 localhost kernel: [4294724.640000] ACPI: Power Button (CM) [PBTN]
Dec 25 13:06:55 localhost kernel: [4294724.640000] ACPI: Sleep Button (CM) [SBTN]
Dec 25 13:06:55 localhost kernel: [4294725.436000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Dec 25 13:07:06 localhost hp: unable to open /var/run/hplip/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 75
Dec 25 13:07:06 localhost hpiod: 0.9.5 accepting connections at 1026...
Dec 25 13:07:13 localhost kernel: [4294745.498000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Dec 25 13:07:13 localhost kernel: [4294745.498000] apm: overridden by ACPI.
ubuntu@ubuntu:/media/linux_part/var/log$


ubuntu@ubuntu:/media/linux_part/var/log$ tail -20 Xorg.0.log
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad ALPS touchpad found
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
ubuntu@ubuntu:/media/linux_part/var/log$

---

