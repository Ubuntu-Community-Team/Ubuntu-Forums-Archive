---
title: "Awesome installation failure"
date: 2012-09-25
forum: Desktop Environments
---

### Post by putstatic on 2012-09-25
Hi, UbuntuForums!

I ran into this problem a couple of days ago when trying to install the awesome desktop environment.

Basically, I think the installation failed about halfway through, and everything has pretty much gone haywire.
I've been able to resolve most of the errors but one still remains:

When I try to install anything with Ubuntu Software Center, the installation simply fails.
When I try to install anything with apt, it gives with the following error message:

```
/var/lib/dpkg/info/udev.postinst: 87: /var/lib/dpkg/info/udev.postinst: update-initramfs: not found
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of dmsetup:
 dmsetup depends on udev (>> 141-2); however:
  Package udev is not configured yet.
dpkg: error processing dmsetup (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of udisks:
 udisks depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing udisks (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on udev (>= 149); however:
  Package udev is not configured yet.
dpkg: error processing xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-input-evdev:
 xserver-xorg-input-evdev depends on xorg-input-abi-16; however:
  Package xorg-input-abi-16 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-16 is not configured yet.
 xserver-xorg-input-evdev depends on xserver-xorg-core (>= 2:1.11.2.902-1ubuntu1); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-input-evdev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-input-synaptics:
 xserver-xorg-input-synaptics depends on udev; however:
  Package udev is not configured yet.
 xserver-xorg-input-synaptics depends on xorg-input-abi-16; however:
  Package xorg-input-abi-16 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-16 is not configured yet.
 xserver-xorg-input-synaptics depends on xserver-xorg-core (>= 2:1.10.99.901); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-input-synaptics (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-input-vmmouse:
 xserver-xorg-input-vmmouse depends on xorg-input-abi-16; however:
  Package xorg-input-abi-16 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-16 is not configured yet.
 xserver-xorg-input-vmmouse depends on xserver-xorg-core (>= 2:1.10.99.901); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg-input-vmmouse depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing xserver-xorg-input-vmmouse (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-intel:
 xserver-xorg-video-intel depends on xorg-video-abi-11; however:
  Package xorg-video-abi-11 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-11 is not configured yet.
 xserver-xorg-video-intel depends on xserver-xorg-core (>= 2:1.10.99.901); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-intel (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-vmware:
 xserver-xorg-video-vmware depends on xorg-video-abi-11; however:
  Package xorg-video-abi-11 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-11 is not configured yet.
 xserver-xorg-video-vmware depends on xserver-xorg-core (>= 2:1.10.99.901); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-vmware (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on udev (>= 147~-5); however:
  Package udev is not configured yet.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on initramfs-tools (>= 0.85eubuntu12); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing console-setup (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 udev
 dmsetup
 network-manager
 udisks
 xserver-xorg-core
 xserver-xorg-input-evdev
 xserver-xorg-input-synaptics
 xserver-xorg-input-vmmouse
 xserver-xorg-video-intel
 xserver-xorg-video-vmware
 initramfs-tools
 apparmor
 console-setup
E: Sub-process /usr/bin/dpkg returned an error code (1)

```However, **the installation is still successful**.

I don't know what is causing it, honestly. Any idea? I'm running xubuntu.

Thanks!

---

### Post by drmrgd on 2012-09-25
What happens if you run:

```
sudo dpkg --configure -a
```

Instead of the '-a' part you can also just choose to configure udev:

```
sudo dpkg --configure udev
```

It might help us see why udev is not configuring and cascading the problem.

---

### Post by putstatic on 2012-09-25
```
omer@Omer:~$ sudo dpkg --configure udev
[sudo] password for omer: 
dpkg: dependency problems prevent configuration of udev:
 udev depends on initramfs-tools (>= 0.92bubuntu63); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 udev

```

---

### Post by putstatic on 2012-10-02
Bump.

---

