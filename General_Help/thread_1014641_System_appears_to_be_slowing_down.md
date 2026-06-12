---
title: "System appears to be slowing down"
date: 2008-12-18
forum: General Help
---

### Post by bilijoe on 2008-12-18
I am running 8.04 (I thought I was running 8.04.1, but System Monitor tells me I'm running 8.04), on a DELL Optiplex GX270 with a 2.8GHz Hyperthreading Pentium 4, 4Gb RAM installed (using 3.5 as the P4 is only 32 bit), and plenty of free disk space (over 200Gb).

For the last couple of months I have been experiencing progressively slower and slower response to just about everything.  This is not dramatic.  If I had never known this machine to run faster, I wouldn't even think there was a problem (based on the speed alone).

Recently, I have been experiencing system freezes (yup, you heard me, a Linux system, frozen hard as a rock--I didn't believe it either, and waited over an hour for the system to sort itself out and continue, but no luck).  This happens most often when I have one or more Browser windows open (I use FireFox 3.0.5, installed from the Mozilla site), with multiple tabs in at least one window.  It has also happened when FireFox is not running; once when OpenOffice was running, and once when Gimp was running.  Usually when things freeze up the clock stops, as does the System Monitor Graph group (the little graphs SysMon will put in the panel).  Once, I got what appeared to be the same [type of] freeze, but the clock kept running and so did the little graphs.

Is there any kind of troubleshooting, or maintenance, or benchmarking tool that might shed some light on what's happening?  Does anyone have any idea what might be happening?  Is there a Plug-in manager somewhere in the system that I can use to disable some or all of the plug-in type additions to see if the culprit is in a plug-in?

I've been meaning to update my system to the current version, but haven't gotten around to it yet.  I almost always do a full "clean" [re]install when I update versions, though I agree with the sticky in this forum advising against routinely doing so; I guess it's just force of habit from being stuck in the Window$ world for far too long.  Given that this system seems to be hanging for no apparent reason, would you gurus out there recommend that I do a full install when I update, or just do an incremental update and see what happens? (I've been meaning to switch tactics there too, but so far have done full installs--like I said, habit.)

Any help, or advice to help me understand/figure out what's going on here would be greatly appreciated.

---

### Post by Polygon on 2008-12-18
check the system log, (system > administration > system log) and look through messages and kernel.log, see anything weird in there? like weird errors or anything out of the blue?

also, install anything recently? try a memtest86 ram test? just random things i thought of...

---

### Post by bilijoe on 2008-12-18
> **Polygon said:**
> check the system log, (system > administration > system log) and look through messages and kernel.log, see anything weird in there? like weird errors or anything out of the blue?

also, install anything recently? try a memtest86 ram test? just random things i thought of...I looked at the logs.  I don't really know what I'm looking for, but the only things that looked at all unusual to me were the following:

From kern.log
Dec 18 01:55:26 Lauren kernel: [   29.891520] agpgart: Detected an Intel 865 Chipset.
Dec 18 01:55:26 Lauren kernel: [   29.891691] agpgart: Detected 8060K stolen memory.
Dec 18 01:55:26 Lauren kernel: [   29.902590] agpgart: AGP aperture is 128M @ 0xf0000000
Dec 18 01:55:26 Lauren kernel: [   29.960616] intel_rng: FWH not detected
Dec 18 01:55:26 Lauren kernel: [   30.138964] iTCO_vendor_support: vendor-support=0
Dec 18 01:55:26 Lauren kernel: [   30.159996] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Dec 18 01:55:26 Lauren kernel: [   30.160119] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
Dec 18 01:55:26 Lauren kernel: [   30.160130] iTCO_wdt: No card detected

from user.log
Dec 18 01:32:25 Lauren dhcdbd: Started up.
Dec 18 01:32:29 Lauren dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec 18 01:32:35 Lauren dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec 18 01:32:35 Lauren dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Dec 18 01:32:35 Lauren dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Dec 18 01:33:19 Lauren pulseaudio[5755]: main.c: This program is not intended to be run as root (unless --system is specified).
Dec 18 01:55:27 Lauren dhcdbd: Started up.
Dec 18 01:55:29 Lauren dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec 18 01:55:32 Lauren dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec 18 01:55:32 Lauren dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Dec 18 01:55:32 Lauren dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu

I'm going to run a memtest next.

---

