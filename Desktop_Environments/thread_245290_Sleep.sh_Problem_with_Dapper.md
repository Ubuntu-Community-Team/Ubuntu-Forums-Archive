---
title: "Sleep.sh Problem with Dapper"
date: 2006-08-27
forum: Desktop Environments
---

### Post by gte999s on 2006-08-27
After adding both NVagp option and the force command after sleep.sh, I can now get my computer to suspend to ram and resume back tino Gnome 90% of the time. However it still randomly freezes 10% of the time and always freezes the other virtual consoles (Alt 1 through 6), even when the resume works.

This is on an nforce 3 motherboard and here is the output from sleep.sh on one of the times it sorta worked (with frozen consoles alt 1 - 6).

```

user@computer:~$ sudo /etc/acpi/sleep.sh force
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:11:09:d2:02:14
Sending on   LPF/eth0/00:11:09:d2:02:14
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.254.254 port 67
send_packet: Operation not permitted
ifdown: interface vmnet8 not configured
/etc/acpi/suspend.d/80-video-vesa-state.sh: line 11:  8602 Trace/breakpoint trap
   vbetool vbemode set 3
Allocated buffer at 0x11010 (base is 0x0)
ES: 0x1101 EBX: 0x0000
 * Shutting down ALSA...                                                 [ ok ] 
/etc/acpi/resume.d/15-video-post.sh: line 6:  8692 Segmentation fault      vbeto
ol post
/etc/acpi/resume.d/17-video-restore.sh: line 9:  8693 Trace/breakpoint trap   vb
etool vbestate restore <$VBESTATE
/etc/acpi/resume.d/17-video-restore.sh: line 9:  8694 Trace/breakpoint trap   vb
etool vbemode set $VBEMODE
ifup: interface eth0 already configured
Ignoring unknown interface vmnet8=vmnet8.
 * Setting up ALSA...                                                    [ ok ] 
/etc/acpi/resume.d/72-acpi-pain.sh: line 22: echo: write error: No such device
/etc/acpi/resume.d/72-acpi-pain.sh: line 23: echo: write error: No such device

```

Anyone else able to fix this problem? Any help would be greatly appreicated.

Thanks!

---

### Post by gte999s on 2006-08-28
Fixed.

Incase anyone else has this problem, this guy was able to fix it himself and lays it out really well in his thread:

[http://ubuntuforums.org/showthread.php?t=201960]("http://ubuntuforums.org/showthread.php?t=201960")

---

