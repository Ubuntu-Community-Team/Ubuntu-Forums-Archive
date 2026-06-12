---
title: "GDM errors after login"
date: 2014-12-06
forum: Desktop Environments
---

### Post by rfugger on 2014-12-06
Just upgraded from 14.04 to 14.10.  After boot, I enter my password, but the system hangs on a blank login grey background.

I'm getting the following syslog errors that seem like they may be relevant:

```
Dec  6 14:41:05 lucifer kernel: [    0.166889] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
Dec  6 14:41:05 lucifer kernel: [    0.699592] tpm_tis 00:05: A TPM error (6) occurred attempting to read a pcr value
Dec  6 14:41:05 lucifer kernel: [    2.498244] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro
Dec  6 14:41:05 lucifer bluetoothd[520]: Failed to init deviceinfo plugin
Dec  6 14:41:05 lucifer bluetoothd[520]: Failed to init proximity plugin
Dec  6 14:41:05 lucifer bluetoothd[520]: Failed to init time plugin
Dec  6 14:41:05 lucifer bluetoothd[520]: Failed to init alert plugin
Dec  6 14:41:05 lucifer bluetoothd[520]: Failed to init thermometer plugin
Dec  6 14:41:05 lucifer bluetoothd[520]: Failed to init gatt_example plugin
Dec  6 14:41:06 lucifer failsafe: Failsafe of 120 seconds reached.
Dec  6 14:41:06 lucifer kernel: [    4.592548] init: Failed to spawn smbd main process: unable to execute: No such file or directory
Dec  6 14:41:06 lucifer kernel: [    4.632538] init: failsafe main process (631) killed by TERM signal
Dec  6 14:41:06 lucifer kernel: [    4.736639] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
Dec  6 14:41:07 lucifer NetworkManager[840]: <warn> failed to allocate link cache: (-26) Protocol mismatch
Dec  6 14:41:08 lucifer gdm-simple-slave[1481]: Failed to give slave programs access to the display. Trying to proceed.
Dec  6 14:41:13 lucifer NetworkManager[840]: <error> [1417905673.705109] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Dec  6 14:41:13 lucifer NetworkManager[840]: <warn> DNS: plugin dnsmasq update failed
Dec  6 14:41:14 lucifer gnome-session[1558]: WARNING: Error getting login monitor: -2
Dec  6 14:41:14 lucifer kernel: [   13.069896] init: Failed to spawn nmbd main process: unable to execute: No such file or directory
Dec  6 14:41:15 lucifer kernel: [   13.300808] audit: type=1400 audit(1417905675.102:30): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/etc/dconf/profile/gdm" pid=1986 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=112 ouid=0
Dec  6 14:41:21 lucifer gdm-launch-environment][1505]: GLib: Source ID 63 was not found when attempting to remove it
Dec  6 14:41:21 lucifer gdm-simple-slave[1481]: Failed to remove slave program access to the display. Trying to proceed.
Dec  6 14:41:21 lucifer gnome-session[2272]: WARNING: Error getting login monitor: -2
Dec  6 14:41:22 lucifer kernel: [   20.540764] traps: gnome-shell[2368] trap int3 ip:7fa5f610cd30 sp:7fffbb8f1520 error:0
Dec  6 14:41:22 lucifer gnome-session[2272]: WARNING: Application 'gnome-shell.desktop' killed by signal 5
Dec  6 14:41:22 lucifer kernel: [   20.815104] traps: gnome-shell[2398] trap int3 ip:7f45f6dbed30 sp:7fff9998ec10 error:0
Dec  6 14:41:22 lucifer gnome-session[2272]: WARNING: Application 'gnome-shell.desktop' killed by signal 5
Dec  6 14:41:22 lucifer gnome-session[2272]: WARNING: App 'gnome-shell.desktop' respawning too quickly
Dec  6 14:41:22 lucifer gnome-session[2272]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Dec  6 14:41:28 lucifer NetworkManager[840]: <info> (wlan1): IP6 addrconf timed out or failed.
Dec  6 14:44:40 lucifer wpa_supplicant[925]: nl80211: send_and_recv->nl_recvmsgs failed: -33

```

If I log in to another terminal (Ctrl-Alt-F1), I can run startx and get into gnome ok.  Any suggestions getting regular GDM login to work?  Thanks.

---

### Post by rfugger on 2014-12-06
Solved this by wiping the partition and installing fresh.  I'm guessing I had some kind of custom Xorg config stuff to get the screen resolution correct on my laptop for 14.04 and 14.10 was choking on it...

---

