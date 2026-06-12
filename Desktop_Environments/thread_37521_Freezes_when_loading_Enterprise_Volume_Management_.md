---
title: "Freezes when loading Enterprise Volume Management System!"
date: 2005-05-27
forum: Desktop Environments
---

### Post by esh on 2005-05-27
Hi!

About every second time I start my computer, it freezes when trying to start "Enterprise Volume Management System", and I have to reboot. Can anyone tell me what's wrong..?
I'm using Ubuntu Hoary.

Thanks!

---

### Post by redbox on 2005-08-29
[QUOTE=esh]Hi!

About every second time I start my computer, it freezes when trying to start "Enterprise Volume Management System", and I have to reboot. Can anyone tell me what's wrong..?
I'm using Ubuntu Hoary.

Thanks![/QUOTE]

I get this problem too. It happens about 3 out of 4 times I reboot. Sometimes it will start after hanging for about 2 or 3 minutes but I have left it for upto an hour with nothing happening.

can evms be disabled?

:¬{

---

### Post by Ranime on 2005-10-22
I have the same problem too.

I figured there might be something wrong with /etc/evms.conf

If some body knows how to correct this, or if there is documentation or example evms.conf files, I would be very greatfull!!


My configuration:
AMD Athlon 3200+ (barton)
nforce2 ultra 400 mainboard
2x 256MB DDR400 memory
1x seagate 20GB | hda (w2k)
1x maxtor 80GB | hdb (linux)
1x Asus 16x DVD | hdc
1x BenQ 16x/8x Duallayer DVD rec. | hdd

nothing fancy...

(default by Ubuntu: )
/etc/evms.conf
```
# EVMS Configuration file

# This file is a useable sample.
# Its location should be /etc/evms.conf
# It contains the default values which will be used in the absence of a
# configuration file or the absence of a configuration option being set.

# Global engine section
engine {
	mode		= readwrite

	# Possible values for debug_level in order are: critical, serious,
	# error, warning, default, details, entry_exit, debug, extra, everything
	#
	# The default value is "default".  Only log entries designated at the
	# debug_level or at a more severe level than the debug_level will be
	# printed to the log.  Thus, a debug_level of "default" will also log
	# critical, serious, error, and warning messages.  "critical" will
	# produce the smallest log, and "everything" will produce the largest
	# log.

	debug_level	= default

	log_file	= /var/log/evms-engine.log

	# Include microseconds in the log timestamps.  Default is "no".

#	log_usec	= yes

	# Include process IDs in the timestamps for log entries.  Default is
	# "no", unless the Engine is running in a clustered environment, in
	# which case PIDs are always included, since the Engine will have
	# several threads running.

#	log_pid		= yes

	# The directory where EVMS puts its metadata backup files.

	metadata_backup_dir	= /var/evms/metadata_backups

	# Save a backup of the metadata after each successful save of a
	# configuration change

#	auto_metadata_backup	= yes
}

# Settings if the Engine is opened in daemon mode
daemon {
	debug_level	= default	# Same settings as available for
					# engine.debug_level

	log_file	= /var/log/evms-daemon.log

	# Include microseconds in the log timestamps.  Default is "no".

#	log_usec	= yes

	# Include process IDs in the timestamps for log entries.  Default is
	# "no", unless the Engine is running in a clustered environment, in
	# which case PIDs are always included, since the Engine will have
	# several threads running.

#	log_pid		= yes
}


# Clustering section

clustering {

	# The number of seconds the engine/daemon should wait for a valid
	# cluster membership to show up.
	
	membership_timeout = 10
}


# Activation section
#
# Use this section to tell EVMS which volumes and objects should be activated.

activate {

	# Names of volumes and objects that should be activated.
	#
	# Names can be specified using "*", "?", and "[...]" notations.
	
	include = [ * ]

	# Names of volumes and objects that should not be activated.
	#
	# Names can be specified using "*", "?", and "[...]" notations.
	
	exclude = [ ]
}


# Local disk manager section

# Use this section to tell EVMS where to look for devices and which devices to
# include or exclude on a system without sysfs (i.e., 2.4 kernels).

legacy_devices {

	# "scan" is the location of the dev node tree.

	scan = /dev

	# "directories" is any directories under the "scan" directory you want
	# searched recursively. On systems running devfs without devfsd, the
	# default settings will find all IDE and SCSI disks.

	directories = [ ide scsi dasd ]

	# "include" are the block devices found in the dev tree that you want
	# EVMS to use as disks.  By default, this will search for traditional
	# style device names (e.g., hda, sdb).  If you know the exact disks that
	# your system uses, you can specify them here to cut down on unnecessary
	# searching.
	#
	# If you are running devfs with devfsd, the default settings will find
	# the old-style names (eg. hda). If you wish to use the new-style names
	# (eg. ide/host0/bus0/target0/lun0/disc), simply remove "sd?" and "hd?"
	# from the list below. If you are running devfs without devfsd, the
	# new-style names will be used.
	#
	# Block device names can be specified using "*", "?", and "[...]"
	# notations.

	include = [ hd? sd? dasd? disc ]

	# "exclude" are the block devices found in the dev tree that you don't
	# want EVMS to use as disks.  Entries here will override any possible
	# matches from the "include" setting.  Thus, if you specify "hd?" in
	# "include", and "hdc" in "exclude", EVMS will examine all IDE disks
	# except hdc.
	#
	# Block device names can be specified using "*", "?", and "[...]"
	# notations.

	exclude = [ ]
}

# Use this section to tell EVMS where to look for devices and which devices to
# include or exclude on a system with sysfs (i.e., 2.5 and later kernels).  In
# order for this to work, sysfs must be mounted somewhere on your system.

sysfs_devices {

	# "include" are the block devices found in the [sysfs_mount_dir]/block/
	# directory that you want EVMS to use as disks.
	#
	# Block device names can be specified using "*", "?", and "[...]"
	# notations.

	include = [ * ]

	# "exclude" are the block devices found in the [sysfs_mount_dir]/block/
	# directory that you don't want EVMS to use as disks.  Entries here
	# will override any possible matches from the "include" setting.
	#
	# Block device names can be specified using "*", "?", and "[...]"
	# notations.

	exclude = [ ]
}


# Cluster Segment Manager (CSM) section

csm {

	# Set admin_mode to yes when you wish to force the CSM to discover
	# objects from all cluster containers, allowing you to perform
	# configuration and maintenance.  Setting admin_mode to yes will cause
	# the CSM to ignore container ownership which will allow you to
	# configure storage in a maintenance mode.
	#
	# The default is no.

#	admin_mode = yes
}


# Multipath section
#
# Use this section to tell EVMS which paths in a multipath device should be
# treated only as "backup" paths. These paths will be activated in the kernel
# in a separate priority-group, and will only be used when all of the "normal"
# paths have failed.
#
# Each entry in this section should be the name of a multipath device on your
# system. The value for each entry should be the names of the child objects
# which should be treated as "backup" paths. Child objects which should be
# treated as "active" paths should not be listed here.
#
# Do not use any wildcard characters in this section.

multipath {
#	md/md0 = [ hdc ]
#	mp/lvm/vg1-pv1 = [ hdd ]
}


# LVM2 plugin section.

lvm2 {
	# Should the LVM2 plugin prompt you for confirmation when it finds
	# LVM2 metadata on an object, but the object does not pass the
	# necessary size checks? If yes, it will ask you if the object is
	# really an LVM2 PV. If no, it will assume the object is not a PV.
	#
	# The default is yes.

        device_size_prompt = yes
}

```

---

### Post by foolosophy on 2005-12-31
I don't know about EVMS, but I do know how to disable it (I disabled it, since I don't use it).

sudo apt-get update
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

Scroll down to the process "evms" and using the spacebar remove the "X"'s from every runlevel in that line.
Press "q". And that's it.

source: [http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

---

### Post by Turin Turambar on 2006-01-28
Just use the "exclude" section of evms.conf. Put there the drive names you don't want evms to scan - like "hdc hdd" or something like that.

That should do it.

---

### Post by dmalopsy on 2006-03-08
I dont know what EVMS does but I tracked it down freezing when my CDROM drive was plugged in. So I unplugged it boot up, and did what "Turin Turambar" sugest and it works like a charm.
I think this is centric to Breezy, since I never had the problem with Warty or Hoary, until I upgraded to Breezy.

---

### Post by robdagg on 2007-07-05
One simple check to make. 

Make sure there is no CD in the CD drive.

This happened to me and took a while to realise the Ubuntu cd was in there and on removing it it boots fine! :p

---

