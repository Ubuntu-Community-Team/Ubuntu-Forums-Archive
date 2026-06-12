---
title: "UDEVD is out of control"
date: 2005-10-15
forum: Desktop Environments
---

### Post by RussM on 2005-10-15
Hi;

I just installed Kubuntu Breezy on a my HP ZD7000 laptop, and found that udevd is constantly running about 30% of the processor time (using top).  It keeps the procoessor hot and the fan blowing like a hair dryer.

I can kill it, but it comes back immediately, and sets to making my system run like a sedated pig...the performance is worse that running the same installation under vmware.

USB seems to be working somewhat...it detects mice, but not my MS wireless optical keyboard/mouse.  It will also mount usb drives...although it fails to bring them up as smb:/sda1 in konquerer.

I've updated my bios.

I run it as a normal bootable install, as well as a virtual machine under VMWARE/XP, which I accomplish by swapping out xorg.conf files.  I do not have vmware tools installed.

This is really bumming me out...does anybody know how I might fix it?

Thanks

Russ

---

### Post by HermanAB on 2005-10-15
Hmmm, udevd is essential - don't kill it.  What you are seeing is a simptom of another problem.  

Is ACPI working?  Running 'acpi -t' will give you the temperature and battery state.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by RussM on 2005-10-15
Well, I made some progress...unplugging the radio for my MS Wireless Optical Desktop cured my udevd problems....but I WOULD like to be able to use my keyboard and mouse.    When I plug in my radio, I get this in the syslog:

Oct 15 14:43:10 localhost kernel: [4302100.843000] usb 1-1: device descriptor read/64, error -71
Oct 15 14:43:10 localhost kernel: [4302101.037000] hub 1-1:1.0: USB hub found
Oct 15 14:43:10 localhost kernel: [4302101.039000] hub 1-1:1.0: 7 ports detected
Oct 15 14:43:10 localhost usb.agent[6898]:      usbcore: already loaded
Oct 15 14:43:10 localhost kernel: [4302101.290000] usb 1-1.4: new full speed USB device using uhci_hcd and address 35
Oct 15 14:43:10 localhost kernel: [4302101.339000] hub 1-1.4:1.0: USB hub found
Oct 15 14:43:10 localhost kernel: [4302101.342000] hub 1-1.4:1.0: 4 ports detected
Oct 15 14:43:10 localhost kernel: [4302101.601000] usb 1-1.4.4: new low speed USB device using uhci_hcd and address 36
Oct 15 14:43:10 localhost usb.agent[6940]:      usbcore: already loaded
Oct 15 14:43:10 localhost kernel: [4302101.720000] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop 2.10] on usb-0000:00:1d.0-1.4.4
Oct 15 14:43:10 localhost kernel: [4302101.722000] drivers/usb/input/hid-core.c: ctrl urb status -71 received
Oct 15 14:43:10 localhost hal.hotplug[6992]: DEVPATH is not set (subsystem input)
Oct 15 14:43:10 localhost kernel: [4302101.774000] usbhid: probe of 1-1.4.4:1.1 failed with error -5
Oct 15 14:43:11 localhost input.agent[6993]:      evdev: already loaded
Oct 15 14:43:11 localhost input.agent[6999]:      evdev: already loaded
Oct 15 14:43:11 localhost kernel: [4302101.839000] usb 1-1.4.4: USB disconnect, address 36
Oct 15 14:43:11 localhost hal.hotplug[7072]: DEVPATH is not set (subsystem input)
Oct 15 14:43:11 localhost usb.agent[7026]:      usbhid: already loaded

---

### Post by SimoneDice on 2005-10-15
Were you able to figure this out?  I am running Breezy on my Dell Precision M60 laptop and my fan is running non-stop as well.  When I did the "acpi -t" I get the following output.

     Battery 1: charged, 100%, rate information unavailable.
     Thermal 1: ok, 37.0 degrees C

How does this compare to a normal thermal reading?  

I have heard of the fan running several times on this board, but there weren't any solutions that worked.  Were you ablet to figure it out?  

If not, did you post a bug report?

---

### Post by RussM on 2005-10-15
acpi -t gives me:
     Battery 1: charged, 100%
     Thermal 1: passive , 55.0 degrees C

When the fan isn't running.

I did manage to soothe udevd, so the fan is running normally, and the system is working very nicely now.  All I had to do was remove the microsoft keyboard.  I imagine other people with raging fan problems have a process run amok.

I sure wish I could make that keyboard work though.

---

### Post by infoburner on 2006-02-01
you should try using a usb to ps2 adapter. i had the exact same problem. udevd went crazy, nothing else happened. then when i used the ps2 adapter it worked fine.

---

