---
title: "trouble automounting removable drives"
date: 2005-04-12
forum: Desktop Environments
---

### Post by mattack on 2005-04-12
I just updated from Warty to Hoary.
Now my ipod, usb thumb drive and media reader don't auto mount when I plug them in.
Does anyone know how to get this to happen again?

there were some errors with the upgrade. here's what I wrote down:

Errors were encountered while processing:
postfix
at
mailx
mutt
anacron
postfix-tls
ubuntu-base
lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mattack on 2005-04-13
I figured out this is a hotplug issue. I fixed the errors posted above by installing a missing package.

When booting I get the following error:
```
mod probe fatal error inserting pciehp (/lib/modules/2.6.10-5-386/kernal/drivers/pci/hotplug/pciehp.ko) no such device
``` 

Anyone have suggestions? 
Would uninstalling hotplug (including the configs) and reinstalling fix this? 
I'm scared it will bork my network card...

Thanks.

---

### Post by mattack on 2005-04-14
okay so this error is PCIExpress related, which I do not have...
but how can I get my removable drives to auto mount like they did in Warty?

---

### Post by alastair on 2005-04-14
Log in - minus external devices.

Open a shell, and :

sudo tail -f /var/log/syslog

Plug in an external device. Anything printed?

It is also worth scanning the log file /var/log/syslog for boot time messages related to USB/1394 buses.

---

### Post by mattack on 2005-04-15
[QUOTE=alastair]Log in - minus external devices.

Open a shell, and :

sudo tail -f /var/log/syslog

Plug in an external device. Anything printed?

It is also worth scanning the log file /var/log/syslog for boot time messages related to USB/1394 buses.[/QUOTE]
 so I sudo tail -f /var/log/syslog

and this is what printed after I plugged in my USB jump drive:
```
Apr 15 13:48:36 localhost kernel: usb 1-2.4: new full speed USB device using uhci_hcd and address 5
Apr 15 13:48:36 localhost kernel: scsi2 : SCSI emulation for USB Mass Storage devices
Apr 15 13:48:36 localhost kernel: usb-storage: device found at 5
Apr 15 13:48:36 localhost kernel: usb-storage: waiting for device to settle before scanning
Apr 15 13:48:37 localhost usb.agent[370]:      usb-storage: already loaded
Apr 15 13:48:41 localhost kernel:   Vendor: LEXAR     Model: JUMPDRIVE SPORT   Rev: 2000
Apr 15 13:48:41 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Apr 15 13:48:41 localhost kernel: SCSI device sdb: 248928 512-byte hdwr sectors (127 MB)
Apr 15 13:48:41 localhost kernel: sdb: Write Protect is off
Apr 15 13:48:41 localhost kernel: sdb: Mode Sense: 43 00 00 00
Apr 15 13:48:41 localhost kernel: sdb: assuming drive cache: write through
Apr 15 13:48:41 localhost kernel: SCSI device sdb: 248928 512-byte hdwr sectors (127 MB)
Apr 15 13:48:41 localhost kernel: sdb: Write Protect is off
Apr 15 13:48:41 localhost kernel: sdb: Mode Sense: 43 00 00 00
Apr 15 13:48:41 localhost kernel: sdb: assuming drive cache: write through
Apr 15 13:48:41 localhost kernel:  /dev/scsi/host2/bus0/target0/lun0: p1
Apr 15 13:48:41 localhost kernel: Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
Apr 15 13:48:41 localhost udev[479]: PROGRAM execution of '/etc/udev/removable.sh sdb' failed
Apr 15 13:48:41 localhost udev[472]: creating device node '/dev/sdb'
Apr 15 13:48:41 localhost kernel: usb-storage: device scan complete
Apr 15 13:48:41 localhost scsi.agent[471]: disk at /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2.4/1-2.4:1.0/host2/target2:0:0/2:0:0:0
Apr 15 13:48:42 localhost udev[497]: PROGRAM execution of '/etc/udev/removable.sh sdb1' failed
Apr 15 13:48:42 localhost udev[496]: creating device node '/dev/sdb1'
```

I then removed the jumpdrive, plugged in the media reader with a card already inserted and got
```
Apr 15 13:54:24 localhost kernel: usb 1-2.3: new full speed USB device using uhci_hcd and address 6
Apr 15 13:54:24 localhost kernel: scsi3 : SCSI emulation for USB Mass Storage devices
Apr 15 13:54:24 localhost kernel: usb-storage: device found at 6
Apr 15 13:54:24 localhost kernel: usb-storage: waiting for device to settle before scanning
Apr 15 13:54:24 localhost usb.agent[2892]:      usb-storage: already loaded
Apr 15 13:54:29 localhost kernel:   Vendor: Generic   Model: USB Storage-SMC   Rev: 0217
Apr 15 13:54:29 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Apr 15 13:54:29 localhost kernel: SCSI device sda: 16001 512-byte hdwr sectors (8 MB)
Apr 15 13:54:29 localhost kernel: sda: Write Protect is off
Apr 15 13:54:29 localhost kernel: sda: Mode Sense: 00 00 00 00
Apr 15 13:54:29 localhost kernel: sda: assuming drive cache: write through
Apr 15 13:54:29 localhost kernel: SCSI device sda: 16001 512-byte hdwr sectors (8 MB)
Apr 15 13:54:29 localhost kernel: sda: Write Protect is off
Apr 15 13:54:29 localhost kernel: sda: Mode Sense: 00 00 00 00
Apr 15 13:54:29 localhost kernel: sda: assuming drive cache: write through
Apr 15 13:54:29 localhost kernel:  /dev/scsi/host3/bus0/target0/lun0: p1
Apr 15 13:54:29 localhost kernel: Attached scsi removable disk sda at scsi3, channel 0, id 0, lun 0
Apr 15 13:54:29 localhost kernel: usb-storage: device scan complete
Apr 15 13:54:30 localhost udev[2995]: PROGRAM execution of '/etc/udev/removable.sh sda' failed
Apr 15 13:54:30 localhost udev[2993]: creating device node '/dev/sda'
Apr 15 13:54:30 localhost scsi.agent[2992]: disk at /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2.3/1-2.3:1.0/host3/target3:0:0/3:0:0:0
Apr 15 13:54:30 localhost udev[3016]: PROGRAM execution of '/etc/udev/removable.sh sda1' failed
Apr 15 13:54:30 localhost udev[3015]: creating device node '/dev/sda1'

```

after plugging in my iPod, it prints 
```
Apr 15 13:58:39 localhost kernel: usb 1-2.1: new full speed USB device using uhci_hcd and address 7
Apr 15 13:58:39 localhost kernel: scsi4 : SCSI emulation for USB Mass Storage devices
Apr 15 13:58:39 localhost kernel: usb-storage: device found at 7
Apr 15 13:58:39 localhost kernel: usb-storage: waiting for device to settle before scanning
Apr 15 13:58:40 localhost usb.agent[4650]:      usb-storage: already loaded
Apr 15 13:58:44 localhost kernel:   Vendor: Apple     Model: iPod              Rev: 1.62
Apr 15 13:58:44 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Apr 15 13:58:44 localhost kernel: SCSI device sdb: 39063023 512-byte hdwr sectors (20000 MB)
Apr 15 13:58:44 localhost kernel: sdb: Write Protect is off
Apr 15 13:58:44 localhost kernel: sdb: Mode Sense: 64 00 00 08
Apr 15 13:58:44 localhost kernel: sdb: assuming drive cache: write through
Apr 15 13:58:44 localhost kernel: SCSI device sdb: 39063023 512-byte hdwr sectors (20000 MB)
Apr 15 13:58:44 localhost kernel: sdb: Write Protect is off
Apr 15 13:58:44 localhost kernel: sdb: Mode Sense: 64 00 00 08
Apr 15 13:58:44 localhost kernel: sdb: assuming drive cache: write through
Apr 15 13:58:45 localhost kernel:  /dev/scsi/host4/bus0/target0/lun0: p1 p2
Apr 15 13:58:45 localhost kernel: Attached scsi removable disk sdb at scsi4, channel 0, id 0, lun 0
Apr 15 13:58:45 localhost kernel: usb-storage: device scan complete
Apr 15 13:58:45 localhost scsi.agent[4770]: disk at /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2.1/1-2.1:1.0/host4/target4:0:0/4:0:0:0
Apr 15 13:58:45 localhost udev[4782]: PROGRAM execution of '/etc/udev/removable.sh sdb' failed
Apr 15 13:58:45 localhost udev[4773]: configured rule in '/etc/udev/rules.d/udev.rules' at line 68 applied, added symlink 'ipod'
Apr 15 13:58:45 localhost udev[4773]: configured rule in '/etc/udev/rules.d/udev.rules' at line 68 applied, 'sdb' becomes '%k'
Apr 15 13:58:45 localhost udev[4773]: creating device node '/dev/sdb'
Apr 15 13:58:45 localhost udev[4796]: PROGRAM execution of '/etc/udev/removable.sh sdb1' failed
Apr 15 13:58:45 localhost udev[4793]: configured rule in '/etc/udev/rules.d/udev.rules' at line 68 applied, added symlink 'ipod'
Apr 15 13:58:45 localhost udev[4793]: configured rule in '/etc/udev/rules.d/udev.rules' at line 68 applied, 'sdb1' becomes '%k'
Apr 15 13:58:45 localhost udev[4793]: creating device node '/dev/sdb1'
Apr 15 13:58:45 localhost udev[4795]: PROGRAM execution of '/etc/udev/removable.sh sdb2' failed
Apr 15 13:58:45 localhost udev[4794]: configured rule in '/etc/udev/rules.d/udev.rules' at line 68 applied, added symlink 'ipod'
Apr 15 13:58:45 localhost udev[4794]: configured rule in '/etc/udev/rules.d/udev.rules' at line 68 applied, 'sdb2' becomes '%k'
Apr 15 13:58:45 localhost udev[4794]: creating device node '/dev/sdb2'

```

here is my /etc/udev/rules.d/udev.rules
```
# There are a number of modifiers that are allowed to be used in some
# of the different fields. They provide the following subsitutions:
# %n - the "kernel number" of the device.
#      For example, 'sda3' has a "kernel number" of '3'
# %k - the kernel name for the device.
# %M - the kernel major number for the device
# %m - the kernel minor number for the device
# %b - the bus id for the device
# %c - the string returned by the PROGRAM. (Note, this doesn't work within
#      the PROGRAM field for the obvious reason.)
# %s{filename} - the content of a sysfs attribute.  
# %% - the '%' char itself.
#

# /dev/cdrom symlink
BUS="ide", KERNEL="hd[a-z]", PROGRAM="/etc/udev/cdsymlinks.sh %k", SYMLINK="%c{1} %c{2}"

# permissions for IDE CD devices
BUS="ide", KERNEL="*[!0-9]", PROGRAM="/bin/cat /proc/ide/%k/media", RESULT="cdrom*", NAME="%k", MODE="0660", GROUP="cdrom"

# permissions for IDE floppy devices
BUS="ide", KERNEL="*[!0-9]", PROGRAM="/bin/cat /proc/ide/%k/media", RESULT="floppy*", NAME="%k", MODE="0660", GROUP="floppy"

# permissions for SCSI sg devices
BUS="scsi", KERNEL="s[grt][0-9]*", SYSFS_type="5", NAME="%k", MODE="0660", GROUP="cdrom"

# put removable IDE/SCSI devices into group 'plugdev' instead of 'disk'
BUS="scsi", KERNEL="sd[a-z]*", PROGRAM="/etc/udev/removable.sh %k", RESULT="1", NAME="%k", MODE="0660", GROUP="plugdev"
BUS="ide", KERNEL="hd[a-z]*", PROGRAM="/etc/udev/removable.sh %k", RESULT="1", NAME="%k", MODE="0660", GROUP="plugdev"

# USB devices
BUS="usb", KERNEL="hiddev*",	NAME="usb/%k"
BUS="usb", KERNEL="auer*",	NAME="usb/%k"
BUS="usb", KERNEL="legousbtower*", NAME="usb/%k"
BUS="usb", KERNEL="dabusb*",	NAME="usb/%k"
BUS="usb", KERNEL="lp[0-9]*",	NAME="usb/%k"

# ALSA devices
KERNEL="controlC[0-9]*", NAME="snd/%k"
KERNEL="hw[CD0-9]*",	NAME="snd/%k"
KERNEL="pcm[CD0-9cp]*",	NAME="snd/%k"
KERNEL="midi[CD0-9]*",	NAME="snd/%k"
KERNEL="timer",		NAME="snd/%k"
KERNEL="seq",		NAME="snd/%k"

# input devices
KERNEL="mice",		NAME="input/%k"
KERNEL="mouse*",	NAME="input/%k"
KERNEL="event*",	NAME="input/%k"
KERNEL="js*",		NAME="input/%k"
KERNEL="ts*",		NAME="input/%k"

KERNEL="card*",		NAME="dri/card%n"
KERNEL="cdemu[0-9]*",	NAME="cdemu/%n"

KERNEL="tap*",		NAME="net/%k"
KERNEL="tun",		NAME="net/%k"

# CAPI devices
KERNEL="capi",		NAME="capi20", SYMLINK="isdn/capi20"
KERNEL="capi*",		NAME="capi/%n"

# dm devices (ignore them)
KERNEL="dm-[0-9]*",	NAME=""
KERNEL="device-mapper",	NAME="mapper/control"

#my custom ipod rule
BUS="scsi", SYSFS{model}="iPod", NAME="%k", SYMLINK="ipod"

```

I tried to make a custom udev rule for the iPod before I upgraded to Hoary. I never got it to work correctly but I left it in there and would fiddle with it from time to time.
If I could get things to mount in the same place evey time that would be awesome, but I'll settle for things automounting...

---

### Post by alastair on 2005-04-15
Devices seem to get created, but you seem to get errors/warning like :

PROGRAM execution of '/etc/udev/removable.sh sdb2' failed

I have a "pure" Hoary install, and have no "/etc/udev/removable.sh" file.

My "/etc/udev/rules.d/udev.rules" file, references :

/etc/udev/scripts/removable.sh

So .... it looks to me like your udev configuration is odd/brojen/misconfigured.

Not sure what to do - I think I'd be tempted to reinstall/reconfigure udev to be pristine, if possible. Else, see if you have "/etc/udev/scripts/removable.sh" and replace occurrences of your "/etc/udev/removable.sh" with this. Have a look anyway.

---

### Post by mattack on 2005-04-16
[QUOTE=alastair]Devices seem to get created, but you seem to get errors/warning like :

PROGRAM execution of '/etc/udev/removable.sh sdb2' failed

I have a "pure" Hoary install, and have no "/etc/udev/removable.sh" file.

My "/etc/udev/rules.d/udev.rules" file, references :

/etc/udev/scripts/removable.sh

So .... it looks to me like your udev configuration is odd/brojen/misconfigured.

Not sure what to do - I think I'd be tempted to reinstall/reconfigure udev to be pristine, if possible. Else, see if you have "/etc/udev/scripts/removable.sh" and replace occurrences of your "/etc/udev/removable.sh" with this. Have a look anyway.[/QUOTE]

I had thought about reinstalling udev...
What I did was to edit /etc/udev/rules.d/udev.rules as you suggested, replacing "/etc/udev/removable.sh" with "/etc/udev/scripts/removable.sh" and that seems to work for my USB flash drive and the media reader. I haven't plugged in my iPod yet but it looks promising. 
Thanks. A lot.    :)

---

### Post by mattack on 2005-04-16
I plugged in my iPod and it mounts to /media/MATTACK every time!
sweet.  
Thanks again.

---

