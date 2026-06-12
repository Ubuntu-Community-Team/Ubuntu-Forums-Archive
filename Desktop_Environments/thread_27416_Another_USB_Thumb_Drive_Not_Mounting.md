---
title: "Another USB Thumb Drive Not Mounting"
date: 2005-04-16
forum: Desktop Environments
---

### Post by Morgoth on 2005-04-16
HI all.
     I am having a little trouble with my USB thumb drive.  I have successfully installed Kubuntu on both my laptop and desktop systems, however I cannot get my thumb drive to work on my desktop.  It works fine in the same computer on my Windows ( sigh, I know ) XP partition and it works great on the laptop, so I figure it can't be the usb port or the drive itself.  I think something got broken when I installed but I'm still fairly new when it comes to ripping around in the guts of Linux and am not sure where to even start looking.  
     I have tried to mount the drive manually, but got an error saying no device ( sda1...  or sdb1... ) and in fact there are no entries at all in /dev for sd"anything".
     When I insert the drive and do a dmesg, it shows the following errors:

     usb 4-6: new high speed USB device using ehci_hcd and address 2
     usb 4-6: device descriptor read/64, error -71
     usb 4-6: new high speed USB device using ehci_hcd and address 3
     usb 4-6: device descriptor read/64, error -71
     usb 4-6: new high speed USB device using ehci_hcd and address 4
     usb 4-6: device descriptor read/64, error -71
     usb 4-6: new high speed USB device using ehci_hcd and address 5
     usb 4-6: device descriptor read/64, error -71
     usb 4-6: device descriptor read/64, error -71
     usb 4-6: new high speed USB device using ehci_hcd and address 6
     usb 4-6: device descriptor read/64, error -71
     usb 4-6: device descriptor read/64, error -71

If anyone out there has seen this or has any insight into my problem I would greatly appreciate a reply.

---

### Post by robajz on 2005-06-03
Hi,

I found this [https://www.redhat.com/archives/fedora-list/2005-March/msg04036.html](https://www.redhat.com/archives/fedora-list/2005-March/msg04036.html)
... type, as root, modprobe -r ehci-hc ...

it's just workaround but worked for me, don't know why. May be next kernel release may fix it.

robajz

---

### Post by Morgoth on 2005-06-03
IT WORKS!! :)  
I cannot thank you enough Robajz ( first born ok? )
As you can tell I posted this 2 months ago and nothing.  I had just about given up trying to find a solution.  I know it's not a life-threatening situation, but it was inconvenient.

Once again thank you.
Morgoth

---

### Post by robajz on 2007-02-18
I'm glad it helped, Morgoth :-) you're welcome.

---

### Post by muskratmx on 2007-12-25
I know this is an old thread, but it fixed my problem sort of.

I have a laptop (IBM t41) In fact I have three of them. Two of which have no issues with the USB drives. they work fine in any and all linux distros installed. The thrid none of the USB drives will work with any Linux distro install, yet they work fine with windoz XP on the same box.

Until I found this thread I had just about given up. But now all the USB drives I have work fine after issuing the modprobe command given on this thread.

Only one small blip. I have to issue the command after each reboot when I want to use the USB drive. This is not a Ubuntu issue, Debian, Suse, and Slackware all do it. The strange thing is it's only with this one box. All three are supposed to be the same. But I guess there is some difference.

---

