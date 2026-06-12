---
title: "fai + cd rom not appearing"
date: 2006-08-04
forum: Desktop Environments
---

### Post by sleepkreep on 2006-08-04
Hello all.  I have setup mass installation of Dapper with FAI.  Everything works great with the exception that any disk I insert into cd cdrom drive will not appear on the desktop or file manager.  I can mount the drive just fine from the command line.  However, if I insert my 256MB usb key, it appears just fine.  I get the same behavior in KDE or GNOME.  I don't know where to begin on debugging this.

THINGS TO NOTE: I modified udev to assign all the removable media disk drives (cd-rom,thumb drive) and audio devices to the the users group.  Here's my /etc/udev/rules.d/40-permissions.rules:

# This file establishes permissions and ownership of devices according
# to Ubuntu policy.  See udev(8) for syntax.
#
# The names of the devices must not be set here, but in 20-names.rules;
# user-friendly symlinks (which need no permissions or ownership) should
# be set in 60-symlinks.rules.

# Block devices
SUBSYSTEM!="block", GOTO="block_end"
SYSFS{removable}!="1",			GROUP="users"
SYSFS{removable}=="1",			GROUP="floppy"
BUS=="usb",				GROUP="users"
BUS=="ieee1394",			GROUP="users"
LABEL="block_end"

# IDE devices
ENV{PHYSDEVBUS}!="ide", GOTO="ide_end"
KERNEL=="hd[a-z]|pcd[0-9]*", \
	IMPORT{program}="cdrom_id --export $tempnode"
ENV{ID_CDROM}=="?*",			GROUP="users"
KERNEL=="ht[0-9]*",			GROUP="tape"
KERNEL=="nht[0-9]*",			GROUP="tape"
LABEL="ide_end"

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "users", okay?
KERNEL=="raw1394",			GROUP="disk"
KERNEL=="dv1394*",			GROUP="users"
KERNEL=="video1394*",			GROUP="users"

# Packet CD devices, group under /dev/pktcdvd
KERNEL=="pktcdvd",			MODE="0644"
KERNEL=="pktcdvd[0-9]*",		GROUP="users"

# Printers and Parallel devices
SUBSYSTEM=="printer",			GROUP="lp"
SUBSYSTEM=="ppdev",			GROUP="lp"
SUBSYSTEM=="usb", KERNEL="lp[0-9]*",	GROUP="lp"
KERNEL=="pt[0-9]*",			GROUP="tape"
KERNEL=="pht[0-9]*",			GROUP="tape"

# SCSI devices
ENV{PHYSDEVBUS}!="scsi", GOTO="scsi_end"
SYSFS{type}=="1",			GROUP="tape"
SYSFS{type}=="5",			GROUP="users"
SYSFS{type}=="6",			GROUP="scanner"
SYSFS{type}=="3", SYSFS{vendor}=="HP",	GROUP="scanner"
LABEL="scsi_end"

# Serial devices
SUBSYSTEM=="tty",			GROUP="dialout"
SUBSYSTEM=="capi",			GROUP="dialout"
SUBSYSTEM=="slamr",			GROUP="dialout"
KERNEL=="ttyLTM[0-9]*",			GROUP="dialout", MODE="0660"

# Sound devices
SUBSYSTEM=="sound",			GROUP="users"

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",		MODE="0664"

# vc (virtual console) devices
SUBSYSTEM!="tty", GOTO="vc_end"
KERNEL=="console",			GROUP="root", MODE="0600"
KERNEL=="ptmx",				GROUP="root", MODE="0666"
KERNEL=="pty*",				GROUP="tty", MODE="0666"
KERNEL=="tty",				GROUP="root", MODE="0666"
KERNEL=="tty[0-9]*",			GROUP="root"
LABEL="vc_end"

# Video devices
SUBSYSTEM=="drm",			GROUP="users"
SUBSYSTEM=="dvb",			GROUP="users"
SUBSYSTEM=="graphics",			GROUP="users"
SUBSYSTEM=="video4linux",		GROUP="users"
KERNEL=="agpgart",			GROUP="users"
KERNEL=="nvidia*",			GROUP="users"

# Other devices, by name
KERNEL=="null",				MODE="0666"
KERNEL=="zero",				MODE="0666"
KERNEL=="full",				MODE="0666"
KERNEL=="random",			MODE="0666"
KERNEL=="urandom",			MODE="0666"
KERNEL=="mem",				GROUP="kmem", MODE="0640"
KERNEL=="kmem",				GROUP="kmem", MODE="0640"
KERNEL=="port",				GROUP="kmem", MODE="0640"
KERNEL=="nvram",			GROUP="nvram"
KERNEL=="rtc",				GROUP="users"
KERNEL=="inotify",			MODE="0666"
KERNEL=="js[0-9]*",			GROUP="users"

---

### Post by sleepkreep on 2006-08-06
Ah, found the problem.  I didn't have the dbus-1-utils package installed.

---

### Post by sleepkreep on 2006-08-09
Well, I spoke to soon.  Here's what happens.  I'm in KDE and I insert a cd into the cdrom.  It appears on the desktop and the media manager.  I click on the icon and the system mounts the drive and opens the cdrom in the file manager.  Then I eject the cdrom.  It unmounts cleanly but the icon doesn't disappear.  If I insert the CD into another cdrom drive it doesn't re-appear on the desktop.  I get very similar behavior in GNOME.  lshal shows that the CD is still in the cdrom even after it has been ejected, so it's obviously a hal issue.  I'm fairly certain it's not a udev issue but my udev permissions file is posted above.  What could possibly be going on?

---

