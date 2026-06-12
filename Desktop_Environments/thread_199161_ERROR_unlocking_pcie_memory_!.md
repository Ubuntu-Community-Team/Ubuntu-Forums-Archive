---
title: "*ERROR* unlocking pcie memory !"
date: 2006-06-18
forum: Desktop Environments
---

### Post by dcherryholmes on 2006-06-18
A few days ago I grabbed the newest kernel and ati drivers.  Prior to that everything was running like butter (Xgl/compiz).  Now things are rendering like a pig, although it seems like 3D acceleration and all the compiz features (aside from here-today-gone-tomorrow opacity in the window menu) are still running.  Anybody got any ideas?  I found a lot of error messages like these when I went poking around:

Jun 18 11:19:37 localhost kernel: [17187234.492000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Jun 18 11:19:37 localhost kernel: [17187234.492000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xee970300 for 1835008 bytes
Jun 18 11:19:37 localhost kernel: [17187234.576000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xaf69f000 for 1835008 bytes
Jun 18 11:19:37 localhost kernel: [17187234.584000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Jun 18 11:19:37 localhost kernel: [17187234.584000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xea84f8c0 for 1835008 bytes
Jun 18 11:19:37 localhost kernel: [17187234.700000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xaf34a000 for 1835008 bytes
Jun 18 11:19:37 localhost kernel: [17187234.708000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Jun 18 11:19:37 localhost kernel: [17187234.708000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xea84f9c0 for 1835008 bytes

---

### Post by benjaminwr on 2006-07-26
by looking at the kernel log I have found out that every time you use a compiz plugin it generates these three messages

Jul 27 00:45:36 localhost kernel: [17182032.880000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8384000 for 4915200 bytes
Jul 27 00:45:36 localhost kernel: [17182032.900000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Jul 27 00:45:36 localhost kernel: [17182032.900000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf327edc0 for 4915200 bytes

if generates them in groups of three on my computer... no idea why

---

### Post by Belyel on 2006-08-25
I'm running xgl with compiz on an ati chipset in my laptop and I get the same string of errors (enough that the terminal window won't display the beginning) when I use the command ```
dmesg
```.  However, when I switch back to standard gnome, I don't have any of the errors.  When running xgl everything is smooth, using kernel 2.6.15-26-686 and the latest ATI drivers, so i'm not too worried about it, but it would be nice to have a fix.

---

### Post by schorsch on 2006-09-17
According to this site [http://transgaming.org/forum/viewtopic.php?t=6341]("http://transgaming.org/forum/viewtopic.php?t=6341")
edit your /etc/X11/xorg.conf in the Section "Device" to look like this:

Section "Device"
   Identifier  "aticonfig-Device[0]"
   Driver      "fglrx"
   Option       "Capabilities" "0x00000800"
   Option       "UseFastTLS" "off"
   Option       "KernelModuleParm" "locked-userpages=0"
EndSection

I had no more error messages after this change and restarting the xserver.

---

### Post by vgeneral on 2006-09-21
> **schorsch said:**
> According to this site [http://transgaming.org/forum/viewtopic.php?t=6341]("http://transgaming.org/forum/viewtopic.php?t=6341")
edit your /etc/X11/xorg.conf in the Section "Device" to look like this:

Section "Device"
   Identifier  "aticonfig-Device[0]"
   Driver      "fglrx"
   Option       "Capabilities" "0x00000800"
   Option       "UseFastTLS" "off"
   Option       "KernelModuleParm" "locked-userpages=0"
EndSection

I had no more error messages after this change and restarting the xserver.

I tried this and I wasn't able to boot properly.  The system booted into a recovery mode where I was able to change the "Device" entries to what they were originally (see below).  

Section "Device"
        Identifier  "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"

Were the suggested "Device" entries suppose to replace the existing entries or added in addition to what was already in the file?

---

### Post by vgeneral on 2006-09-21
I resolved the issue i was experiencing.  The identifier was incorrect in my xorg.conf file.  I simply updated that value to the correct on and the system booted up fine.  I also checked the dmesg log for any fglrx errors and there were zero.

---

