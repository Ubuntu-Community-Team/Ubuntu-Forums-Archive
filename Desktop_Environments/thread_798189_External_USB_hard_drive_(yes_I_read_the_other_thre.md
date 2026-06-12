---
title: "External USB hard drive (yes I read the other threads)"
date: 2008-05-18
forum: Desktop Environments
---

### Post by john.anderson on 2008-05-18
Note: I -think/hope- this is in the right forum. 

Here's my issues, and other problems.
In advance, I read the other threads, and tried all of those.

Problems:
Simpletech 160GB external USB harddrive doesn't mount and/or detect.
Using Hardy 8.04 default, up to date, as of today, 5/17/08

/etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=53426ed4-15a1-4e1c-aa25-5853f412280f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=552869a4-b609-4e61-bf30-a0ac3981e9ea none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

/etc/mtab:
```
/dev/sda7 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/john/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=john 0 0

```

lsusb:
```

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

fdisk -l
```

/dev/sda1   *           1        2318    18619303+  83  Linux
/dev/sda2            2319       24792   180522405    5  Extended
/dev/sda5            3648        3829     1461883+  82  Linux swap / Solaris
/dev/sda6            3830       24792   168385266   83  Linux
/dev/sda7            2319        3584    10169082   83  Linux
/dev/sda8            3585        3647      506016   82  Linux swap / Solaris

Note: Yes, the HD is partitioned all to heck and back. I was doing a test-drive of 8.04 before deciding if I wanted to fully switch. The problem being my external won't mount to let me back up my files to do a full reformat.

```

dmesg | tail -10
```
[   88.991819] [fglrx] enable ID = 0x00000005
[   88.991833] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   99.426435] eth0: no IPv6 routers present
[COLOR="Red"][  164.908854] usb 2-2: reset low speed USB device using ohci_hcd and address 2[/COLOR]
[COLOR="SeaGreen"][  178.857856] usb 2-2: USB disconnect, address 2
[  196.748470] usb 2-2: new low speed USB device using ohci_hcd and address 3
[  196.960715] usb 2-2: configuration #1 chosen from 1 choice
[  196.979056] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.1/usb2/2-2/2-2:1.0/input/input6
[  197.000478] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.1-2[/COLOR]
[COLOR="Red"][  216.446344] usb 2-2: reset low speed USB device using ohci_hcd and address 3[/COLOR]

The Red is where I plugged it in. The Green is where I plugged/unplugged my mouse.

```

The odd part: If I unplug the mouse, then plug the External in, I get -no- message from dmesg about it. These USB ports are side-by-side on the front of the machine. I have 2 on the back that work fine w/ the mouse, but get no messages in dmesg about the External.

dmesg (illustrating the point of the mouse/no dmesg)
```

[   88.991833] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   99.426435] eth0: no IPv6 routers present
[  164.908854] usb 2-2: reset low speed USB device using ohci_hcd and address 2
[  178.857856] usb 2-2: USB disconnect, address 2
[  196.748470] usb 2-2: new low speed USB device using ohci_hcd and address 3
[  196.960715] usb 2-2: configuration #1 chosen from 1 choice
[  196.979056] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.1/usb2/2-2/2-2:1.0/input/input6
[  197.000478] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.1-2
[  216.446344] usb 2-2: reset low speed USB device using ohci_hcd and address 3
[  953.220895] usb 2-2: USB disconnect, address 3

The Disconnect is where i unplug the mouse. Now i disconnect the external, wait a few seconds, plug it back in, wait a few seconds, then plug the mouse back in.

```

Next dmesg:

```

[  196.748470] usb 2-2: new low speed USB device using ohci_hcd and address 3
[  196.960715] usb 2-2: configuration #1 chosen from 1 choice
[  196.979056] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.1/usb2/2-2/2-2:1.0/input/input6
[  197.000478] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.1-2
[  216.446344] usb 2-2: reset low speed USB device using ohci_hcd and address 3
[  953.220895] usb 2-2: USB disconnect, address 3
[  970.722884] usb 2-2: new low speed USB device using ohci_hcd and address 4
[  970.937067] usb 2-2: configuration #1 chosen from 1 choice
[  970.993134] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.1/usb2/2-2/2-2:1.0/input/input7
[  971.022898] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:0

```


1) rebooting w/ it plugged in doesn't help.
2) modprobe -r ehci_hcd doesn't help. (modprobe -r ohci_hcd disables usb)

I'm out of ideas. Thanks in advance.

---

### Post by kirenpillay on 2008-10-30
I believe the problem is that Vista writes a lock file to the drive, which can only be unlocked/unmounted by the same user. So if you mounted the drive on Vista, you need to unmount on that same machine, and it should work after that on your linux machine (and other windows machines).

P.S.: Its amazing that this drive can't even be picked up with dmesg because of this! But mine is working now (whew)

---

