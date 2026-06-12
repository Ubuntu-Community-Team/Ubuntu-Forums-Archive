---
title: "Ubuntu Gusty logs me off"
date: 2009-03-17
forum: General Help
---

### Post by james3302 on 2009-03-17
It's mainly when I hit the show desktop icon, sometimes when I minimize firefox. I have 3-4 tabs open i firefox at the time, and they have been the same tabs for the past couple of days. I think it's either been an update I received or its on of the websites I have pulled up. can someone pull up these websites and then try to use the show desktop button?

[http://www.chordbook.com/guitarchords.php](http://www.chordbook.com/guitarchords.php)
[http://www.cyberfret.com/scales/basic/page2.php](http://www.cyberfret.com/scales/basic/page2.php)
[http://www.cyberfret.com/styles/metal/metal-for-breakfast/volume-1/page3.php](http://www.cyberfret.com/styles/metal/metal-for-breakfast/volume-1/page3.php)

They are all just guitar websites, nothing bad.

---

### Post by fieroboom on 2009-03-17
> **james3302 said:**
> It's mainly when I hit the show desktop icon, sometimes when I minimize firefox. I have 3-4 tabs open i firefox at the time, and they have been the same tabs for the past couple of days. I think it's either been an update I received or its on of the websites I have pulled up. can someone pull up these websites and then try to use the show desktop button?

[http://www.chordbook.com/guitarchords.php](http://www.chordbook.com/guitarchords.php)
[http://www.cyberfret.com/scales/basic/page2.php](http://www.cyberfret.com/scales/basic/page2.php)
[http://www.cyberfret.com/styles/metal/metal-for-breakfast/volume-1/page3.php](http://www.cyberfret.com/styles/metal/metal-for-breakfast/volume-1/page3.php)

They are all just guitar websites, nothing bad.

It sounds like something is crashing your X server...

Try to make it crash again, and when it does, log back in, open a terminal, and run each of the following commands, copy the output, and paste it here.

```
tail /var/log/Xorg.0.log
tail /var/log/syslog
tail /var/log/dmesg
```

Also, in the future, when something goes wrong, a great place to start looking is log files, most of which will be located in /var/log. Have a look in that directory, and you'll see a bunch of log files to help you in your quest. You can start by listing the files there:

```
ls /var/log
```

:D
-Paul

---

### Post by james3302 on 2009-03-17
I was so excited that I finally made it fail again that I typed my username in wrong on the first login attempt, so ignore anything that says something about incorrect login. 


My list of log files in the /var/log folder
apport.log     daemon.log      kern.log  pycentral.log     wvdialconf.log
auth.log       dpkg.log        lpr.log   scrollkeeper.log  Xorg.0.log
bootstrap.log  fontconfig.log  mail.log  user.log


_tail/var/Xorg.0.log_
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) XAA: Evicting pixmaps

_tail /var/log/syslog_
Mar 17 13:29:13 james-desktop gdm[5185]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Mar 17 13:29:16 james-desktop kernel: [ 1478.714543] set status page addr 0x00033000
Mar 17 13:29:24 james-desktop gdm[5934]: WARNING: Couldn't authenticate user 
Mar 17 13:29:28 james-desktop hcid[5130]: Default passkey agent (:1.34, /org/bluez/passkey) registered
Mar 17 13:29:28 james-desktop hcid[5130]: Default authorization agent (:1.34, /org/bluez/auth) registered
Mar 17 13:29:29 james-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Mar 17 13:29:29 james-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Mar 17 13:29:47 james-desktop firmware_helper[6249]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:01.0' with driver 'bcm43xx'
Mar 17 13:29:47 james-desktop kernel: [ 1510.315295] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Mar 17 13:29:49 james-desktop NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 


_tail /var/log/dmesg_
[   29.700834] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   29.757878] bcm43xx driver
[   29.757949] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.757959] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   29.963708] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   29.963727] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   30.170915] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   30.462357] lp: driver loaded but no devices found
[   30.524058] Adding 979956k swap on /dev/sda2.  Priority:-1 extents:1 across:979956k
[   30.929824] EXT3 FS on sda3, internal journal

---

### Post by fieroboom on 2009-03-17
Wow, these threads fall through faster than freakin rain in the rain forest... I actually had to search to find this thread again!

Back to the issue... Here is what's happening, as I suspected:
```
tail /var/log/syslog
Mar 17 13:29:13 james-desktop gdm[5185]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Mar 17 13:29:16 james-desktop kernel: [ 1478.714543] set status page addr 0x00033000
```

But I'd like to see some more logging, because now that we've pinned it down a little, a quick google search for "WARNING: gdm_slave_xioerror_handler:"
returns a metric crapton of results, including [this one](http://ubuntuforums.org/showthread.php?t=96068) here on ubuntuforums, and several reports on [launchpad](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/212648)

So make it crash again, and this time, run these commands and copy/paste the results:
```
grep WARNING /var/log/syslog
grep EE /var/log/Xorg.0.log
grep EE /var/log/Xorg.0.log.old
```

Be sure to read everything on that launchpad site also, and feel free to report to it, but be prepared to provide the proper information they ask for... Review the method for [obtaining a backtrace](https://wiki.ubuntu.com/X/Backtracing) if you plan to report there.
:D
-Paul

---

### Post by james3302 on 2009-03-18
_grep WARNING /var/log/syslog_

Mar 17 09:21:17 james-desktop gdm[22045]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Mar 17 09:34:14 james-desktop gdm[23678]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Mar 17 13:29:13 james-desktop gdm[5185]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Mar 17 13:29:24 james-desktop gdm[5934]: WARNING: Couldn't authenticate user 
Mar 17 15:04:51 james-desktop gdm[5934]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Mar 17 23:56:38 james-desktop gdm[9288]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

_grep EE /var/log/Xorg.0.log_
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER


_grep EE /var/log/Xorg.0.log.old_
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER


Looks like the last two gave a generic response. That's supposed to be 
Xorg.[zero].log right???

---

