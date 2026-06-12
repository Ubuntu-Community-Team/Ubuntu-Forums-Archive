---
title: "3G USB Stick has suddenly stopped working"
date: 2009-06-24
forum: General Help
---

### Post by zonky on 2009-06-24
I have a ZTE MFM 636 USB stick (On Telecom XT, NZ).

It was working for a couple of weeks, and has suddenly stopped being recognised.

I'm seeing this in my logs when the device is plugged in, and it's no longer being listed by network manager:

```
Jun 25 12:50:26 paulr-notebook nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if2_serial_usb_0, iface: (null)): iface not found
Jun 25 12:50:26 paulr-notebook NetworkManager: <info>  (ttyUSB2): found serial port (udev:  hal:GSM) 
Jun 25 12:50:26 paulr-notebook NetworkManager: <info>  (ttyUSB2): ignoring due to lack of probed mobile broadband capabilties 
Jun 25 12:50:26 paulr-notebook NetworkManager: <info>  (ttyUSB0): ignoring due to lack of mobile broadband capabilties 
Jun 25 12:50:26 paulr-notebook NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties 
Jun 25 12:50:26 paulr-notebook nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if3_serial_usb_0, iface: (null)): iface not found
Jun 25 12:50:26 paulr-notebook NetworkManager: <info>  (ttyUSB3): found serial port (udev:  hal:GSM) 
Jun 25 12:50:26 paulr-notebook NetworkManager: <info>  (ttyUSB3): ignoring due to lack of probed mobile broadband capabilties 
```


I can't absolutelty swear to this, but i believe it stopped working after the HAL update last week (i don't use this usb stick every day).

I configured this originally following instructions in this thread, in particular post 8: [http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934)

(I disabled the CD-Autorun using windows via the AT command).

Device is still running ok on a windows computer, so it's not a 3G network issue/Sim card issue.

---

### Post by zonky on 2009-06-24
I booted off the older kernel, and i've found that it works - (2.6.28.11)

```
Jun 25 13:09:05 paulr-notebook NetworkManager: <info>  (ttyUSB2): found serial port (udev:GSM  hal:GSM) 
Jun 25 13:09:05 paulr-notebook NetworkManager: <info>  (ttyUSB2): new Modem device (driver: 'option') 
Jun 25 13:09:05 paulr-notebook NetworkManager: <info>  (ttyUSB2): exported as /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if3_serial_usb_0 
Jun 25 13:09:09 paulr-notebook nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if2_scsi_host_0, iface: (null)): iface not found
Jun 25 13:09:09 paulr-notebook NetworkManager: <info>  (ttyUSB2): device state change: 1 -> 2 
Jun 25 13:09:10 paulr-notebook NetworkManager: <info>  (ttyUSB2): deactivating device (reason: 2). 
Jun 25 13:09:10 paulr-notebook NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf 
Jun 25 13:09:10 paulr-notebook NetworkManager: <info>  Policy set 'Auto X-Net' (wlan0) as default for routing and DNS. 
Jun 25 13:09:10 paulr-notebook NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jun 25 13:09:10 paulr-notebook NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Jun 25 13:09:10 paulr-notebook NetworkManager: <info>  (ttyUSB2): device state change: 2 -> 3 
Jun 25 13:09:11 paulr-notebook NetworkManager: <info>  (ttyUSB0): ignoring due to lack of mobile broadband capabilties 
Jun 25 13:09:11 paulr-notebook NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties 
```

So it's related to this?

---

### Post by geirha on 2009-06-24
The hal package has likely overwritten the file
/usr/share/hal/fdi/information/10freedesktop/10-modem.fdi which that post instructed you to edit, so check that file and see if your change has been reverted. Might be an idea to check all the other changes as well, but in general, it will not overwrite anything under /etc without asking you first.

---

### Post by zonky on 2009-06-24
> **geirha said:**
> The hal package has likely overwritten the file
/usr/share/hal/fdi/information/10freedesktop/10-modem.fdi which that post instructed you to edit, so check that file and see if your change has been reverted. Might be an idea to check all the other changes as well, but in general, it will not overwrite anything under /etc without asking you first.

Thanks for the help. I've checked the 10-modem.fdi, and that is still set correctly.

I just found a couple of posts with other people with similar issues with other 3G cards, and they're saying the problem disppears when they boot off an older kernel, so I tried doing the same thing.

I'm using 2.6.28-13-generic currently (latest in Jaunty?), and it is not working when i boot with this kernel.

However, when i boot with 2.6.28-11-generic, without any other changes to any /etc file, the stick works entirely as expected!

---

### Post by zonky on 2009-06-24
A bit of research suggests this is a likely cause:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002)

Although, I have no idea how to fix :(

---

### Post by zonky on 2009-06-24
Aha! Fixed.

The changes to the kernel in 2.6.28.13-generic around usbserial appear to mean that you no longer need to add a rule:

/etc/udev/rules.d/90-zte.rules

(as per the article i linked to above.)

so all i had to do to get this workign with this kernel is

>sudo rm /etc/udev/rules.d/90-zte.rules

A reboot, and now it works as before!

---

