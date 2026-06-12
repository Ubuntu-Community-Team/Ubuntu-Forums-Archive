---
title: "Unable to enumerate USB devices during boot"
date: 2009-01-02
forum: Desktop Environments
---

### Post by ubnewbie2 on 2009-01-02
During boot, ubuntu falls back to the text screen showing a message that Bluetooth is starting, then the following errors with usb appear slowly (shown below is the dmesg output)

This problem just started occurring on a previously working system (8.10), so it may be due to a change from one of the frequent daily updates, or, I suppose it might be a hardware problem that just occurred - only one time it happened, the usb mouse wasn't working, but unplugging it and reinserting it, fixed it, which makes me think it's some problem only during boot.

```
[   33.416016] usb 2-4: device descriptor read/64, error -110
[   33.632020] usb 2-4: new high speed USB device using ehci_hcd and address 4
[   48.744014] usb 2-4: device descriptor read/64, error -110
[   63.960014] usb 2-4: device descriptor read/64, error -110
[   64.176012] usb 2-4: new high speed USB device using ehci_hcd and address 5
[   74.584011] usb 2-4: device not accepting address 5, error -110
[   74.696012] usb 2-4: new high speed USB device using ehci_hcd and address 6
[   85.104019] usb 2-4: device not accepting address 6, error -110
[   85.104089] hub 2-0:1.0: unable to enumerate USB device on port 4
[   85.560013] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   85.773163] usb 1-1: configuration #1 chosen from 1 choice
[   86.080013] usb 1-4: new full speed USB device using ohci_hcd and address 3
[  101.256013] usb 1-4: device descriptor read/64, error -110
[  116.536013] usb 1-4: device descriptor read/64, error -110
[  116.816011] usb 1-4: new full speed USB device using ohci_hcd and address 4
[  131.992011] usb 1-4: device descriptor read/64, error -110
[  147.272011] usb 1-4: device descriptor read/64, error -110
[  147.552012] usb 1-4: new full speed USB device using ohci_hcd and address 5
[  157.960015] usb 1-4: device not accepting address 5, error -110
[  158.136013] usb 1-4: new full speed USB device using ohci_hcd and address 6
[  168.544012] usb 1-4: device not accepting address 6, error -110
[  168.544079] hub 1-0:1.0: unable to enumerate USB device on port 4

```

---

### Post by elli222 on 2009-01-03
Hello, exactly the same problem here.

It seems that the hub gets power from the BIOS, and works fine, but when Linux takes over, the power fails for about 1/2 a minute after it has fully booted. After the device receives power, (in this case, a USB mouse) it takes about 20 seconds until it functions.

Disabling ACPI kept the mouse powered up, but it failed to work properly.
My keyboard (PS2) works fine.

And here is my dmesg

```
[   64.868067] usb 2-5: device descriptor read/64, error -110
[   65.085804] usb 2-5: new high speed USB device using ehci_hcd and address 4
[   66.736027] eth0: no IPv6 routers present
[   75.493788] usb 2-5: device not accepting address 4, error -110
[   75.604032] usb 2-5: new high speed USB device using ehci_hcd and address 5
[   86.012302] usb 2-5: device not accepting address 5, error -110
[   86.012913] hub 2-0:1.0: unable to enumerate USB device on port 5
[   86.708295] usb 3-3: new full speed USB device using ohci_hcd and address 2
[   86.937152] usb 3-3: configuration #1 chosen from 1 choice
[   87.120295] usb 1-5: new full speed USB device using ohci_hcd and address 2
[  102.300286] usb 1-5: device descriptor read/64, error -110
[  117.597545] usb 1-5: device descriptor read/64, error -110
[  117.865550] usb 1-5: new full speed USB device using ohci_hcd and address 3
[  133.041525] usb 1-5: device descriptor read/64, error -110
[  148.320288] usb 1-5: device descriptor read/64, error -110
[  148.628666] usb 1-5: new full speed USB device using ohci_hcd and address 4
[  159.036292] usb 1-5: device not accepting address 4, error -110
[  159.212275] usb 1-5: new full speed USB device using ohci_hcd and address 5
[  169.636282] usb 1-5: device not accepting address 5, error -110
[  169.636312] hub 1-0:1.0: unable to enumerate USB device on port 5
[  169.636362] usbcore: registered new interface driver hiddev
[  169.643273] input: Logitech USB Gaming Mouse as /devices/pci0000:00/0000:00:04.0/usb3/3-3/3-3:1.0/input/input5
[  169.677652] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:04.0-3
[  169.690003] hiddev96hidraw1: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:04.0-3
[  169.690037] usbcore: registered new interface driver usbhid
[  169.690042] usbhid: v2.6:USB HID core driver
[  198.753282] usb 1-5: new full speed USB device using ohci_hcd and address 6
[  213.928039] usb 1-5: device descriptor read/64, error -110
[  229.208287] usb 1-5: device descriptor read/64, error -110
[  229.489550] usb 1-5: new full speed USB device using ohci_hcd and address 7
[  244.664585] usb 1-5: device descriptor read/64, error -110
[  259.944287] usb 1-5: device descriptor read/64, error -110
[  260.224303] usb 1-5: new full speed USB device using ohci_hcd and address 8
[  270.634611] usb 1-5: device not accepting address 8, error -110
[  270.808269] usb 1-5: new full speed USB device using ohci_hcd and address 9
[  281.216032] usb 1-5: device not accepting address 9, error -110
[  281.216323] hub 1-0:1.0: unable to enumerate USB device on port 5
```

This is one of the last remaining bug in my new setup.

Yes my mouse is a logitech G5 Laser gaming mouse which only contains drivers for windows
No, i dont have windows!

---

### Post by ubnewbie2 on 2009-01-03
I have discovered it may be something to do with the ASUS Expressgate.  This is a boot option on some ASUS motherboards that let's you boot very quickly to a small embedded version of linux (which sits in FLASH on the motherboard or on a USB key), instead of booting to the operating system on the hard drive.

My motherboard failed to find the Expressgate USB this morning, so I disabled the whole Expressgate thing, and Ubuntu booted absolutely normally.  If that continues, I will just leave Expressgate disabled.

---

### Post by Anlace on 2009-01-22
Greetings,

I am having the same error messages too, it began this morning on an installation of Kubuntu 8.1/KDE 4.1 that is about a week and a half old.

lsusb shows all my usb devices and they are all working correctly so this error doesn't seem to actually affect anything.  It has slowed boot up quite a bit, I would even say twice as long because the error message repeats many many times before boot up continues.

I am not using an ASUS motherboard, mine is XFX MB with the 780i nForce chipset.  I built this computer last July.

Any thoughts?

GL

---

### Post by JensOtto on 2009-02-27
Hi
I'm using 8.10 and I used not to have this problem. Now I have the exact same problem. In my case it all started after I have done som experiments with running Windows XP in VirtualBox and trying to get USB working in that setting. It sort of worked but I got this very annoying slow boot problem. So I'm suspecting a connection here.
Any help would be much appeciated.

/JensOtto

Update: Now it works again. I really don't know why it works again -- all I've done is to add new USB filters to the VirtualBox configuration and on the next boot everything went smooth and have done so for 5 or 6 boots. I will not call this "resolved" since I don't know exactly what coursed the problem and neither do I know what made it go away.

---

### Post by Nimaran on 2009-12-19
Any new updates on this thread? I have got this problem with a fresh install of 9.10 except my problem is that my USB device (in this case a wireless dongle) will not work at all. However, it is not the port because it works with other devices, and it is not the device, because it works on other systems?

---

### Post by Matt 6:27 on 2010-01-16
I too just started getting this error (unable to enumerate USB devices...).  lsusb dislcoses no errors and all peripherals appear to be working.  Before I even get to the point where USB ports are tested/detected, there is a long lag early on start up before the boot order shows on my screen (e.g., when it searches for IDE devices, then CD/DVD, then HD).  System profile is listed in my sig.  System is otherwise performing as usual.

---

### Post by Endomancer on 2010-02-05
I have had this problem too. It left me unable to boot from the hard drive but I was able to boot using a live disc, I ended up reinstalling and it has been working properly since then. Hopefully some one can come up with a better solution.
Also, Im running a GIGABYTE mother board so  obviously its not just an  ASUS problem

---

### Post by Endomancer on 2010-03-23
I got this problem again!!!!!!
was really hoping someone had come up with a better solution than my previous one by now

---

### Post by SpinUp on 2011-02-02
Sounds strange, but it's worth a shot to unplug and replug the computer.  See this thread:
[]("http://ubuntu-utah.ubuntuforums.org/showthread.php?p=10420343#post10420343")[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=10420343](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=10420343)

Edit: mine is an ASUS motherboard

---

### Post by NennokraH on 2011-03-12
I installed a lot of ubuntu 10.10 distributions: 32bit, 64bit, kubuntu 32bit, 64 bit.. in all I received the USB errors and the mouse was frozen for like 5 minutes.

I noticed also the splash screen (I have ASUS motherboard with splash screen) had some strange behavior as it was missing and showing only a short message: "Press DEL to enter setup or ESC to boot OS".

I checked all the software solutions none of them worked. After that I saw a thread (unfortunately I forgot which one) where the solution is simply shutdown and disconnect for a few seconds the power cord and reconnect it.

IT WORKED. (I have an UPS. I left the UPS power on. I plugged off the cable. I pressed the power source button to off and after on. I replugged the cable. Started the PC from power button. Now works perfect).

---

### Post by ectospasm on 2011-03-24
This is counterintuitive (meaning I don't know *why* this works) but unplugging the power cable to the Ubuntu machine for 5-10 minutes solved it for me.

---

