---
title: "Kubuntu 10.04 USB Keeps disconnecting"
date: 2010-05-07
forum: Desktop Environments
---

### Post by mickle026 on 2010-05-07
I have this problem that wasn't there in kubuntu 9.04 with the usb ports.

I think its something broken when dolphin is closed down.  It 'seems' that the usb ports are not polled unless dolphin is open.

The scenario:

I use kubuntu as a server with samba shares and run host applications on the system, I like the kde desktop because I often have to visit the server to perform maintenance/alterations to my apps on it, although im pretty fine with bash I still like the ease of point and click.

Currently the samba shares are on a 1tb Toshiba external USB drive.  This is fine and works fine in this setup with kubuntu 9.04.  The problem is not with Samba, its with the usb port in kubuntu 10.04.

My problem is with kubuntu 10.04, if I close down dolphin file manager then the drive eventually disconnects and parks displaying its red light, but if I leave dolphin open but minimized it doesn't disconnect, keeping its blue light on (connected).  When it disconnects the shares are therefore not accessible.

I believe the usb stops being polled after closing dolphin and eventually the drive enters its not in use state and parks.  This is not helpful to me, I want it to be active to samba.

Any with any ideas how to stop the usb disconnecting would be very welcome to post them.  

many thanks!

* update

The usb ports is still shutting down when the external drive is being written to via samba when dolphin is not open.  So I assume the usb devices are only active when dolphin is? - weird!

---

### Post by Zorael on 2010-05-08
Curious. To begin with, is it supposed to disconnect after a period of inactivity, or is "the real wtf" that it's actually going to sleep while still connected to your machine?

My external usb disk spins down after some ~30 minutes of inactivity, sure, but it doesn't disconnect. Any subsequent read or write to it will make it spin up.

Is anything output to dmesg?
hdparm also has an argument to set the standby timeout, but again that usually just translates to spinning down.


(One *really* dirty workaround might be to create a Folder View widget and point it to the directory where you mounted the usb drive. If indeed Dolphin is keeping it awake, then the Folder View widget might do the same, without being in your face.)

---

