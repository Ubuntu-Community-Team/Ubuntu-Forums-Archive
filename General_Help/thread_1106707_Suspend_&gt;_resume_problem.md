---
title: "Suspend &gt; resume problem"
date: 2009-03-26
forum: General Help
---

### Post by MadMax2 on 2009-03-26
On resume i get a coloured screen but no graphics.

I'm including the system log:

Mar 26 13:01:58 john-desktop syslogd 1.5.0#2ubuntu6: restart.
Mar 26 13:05:47 john-desktop syslogd 1.5.0#2ubuntu6: restart.
Mar 26 13:19:34 john-desktop -- MARK --
Mar 26 13:39:34 john-desktop -- MARK --
Mar 26 13:59:34 john-desktop -- MARK --
Mar 26 14:07:00 john-desktop kernel: [ 7668.085405] type=1505 audit(1238029620.172:5): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=9164
Mar 26 14:07:00 john-desktop kernel: [ 7668.622636] type=1505 audit(1238029620.708:6): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=9169
Mar 26 14:07:00 john-desktop kernel: [ 7668.624093] type=1505 audit(1238029620.712:7): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=9169
Mar 26 14:19:34 john-desktop -- MARK --
Mar 26 14:39:34 john-desktop -- MARK --
Mar 26 14:59:34 john-desktop -- MARK --
Mar 26 15:06:42 john-desktop kernel: [11250.586272] PM: Syncing filesystems ... done.
Mar 26 15:51:25 john-desktop kernel: [11250.588996] Freezing user space processes ... (elapsed 0.00 seconds) done.
Mar 26 15:51:25 john-desktop kernel: [11250.590240] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Mar 26 15:51:25 john-desktop kernel: [11250.590319] Suspending console(s) (use no_console_suspend to debug)
Mar 26 15:51:25 john-desktop kernel: [11250.636028] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Mar 26 15:51:25 john-desktop kernel: [11251.005557] sd 2:0:0:0: [sda] Stopping disk
Mar 26 15:51:25 john-desktop kernel: [11251.340552] parport_pc 00:07: disabled
Mar 26 15:51:25 john-desktop kernel: [11251.396287] ATI IXP AC97 controller 0000:00:14.5: PCI INT B disabled
Mar 26 15:51:25 john-desktop kernel: [11251.396598] ehci_hcd 0000:00:13.2: PCI INT A disabled
Mar 26 15:51:25 john-desktop kernel: [11251.412075] ohci_hcd 0000:00:13.1: PCI INT A disabled
Mar 26 15:51:25 john-desktop kernel: [11251.412128] ohci_hcd 0000:00:13.0: PCI INT A disabled
Mar 26 15:51:25 john-desktop kernel: [11251.412268] PM: suspend devices took 0.824 seconds
Mar 26 15:51:25 john-desktop kernel: [11251.412354] ACPI: Preparing to enter system sleep state S3
Mar 26 15:51:25 john-desktop kernel: [11251.412472] Disabling non-boot CPUs ...
Mar 26 15:51:25 john-desktop kernel: [11251.412472] ACPI: Waking up from system sleep state S3

Is that enough of the log?
Thanks for your help.

---

### Post by MadMax2 on 2009-03-26
PS
I used <space> to wake it.
Downloaded my copy of Ubuntu 8.10 without sum check or bit torrent.
I assume  bugs such as this are duly noted and worked on.

Is there a key work around?
Thanks MM2

---

