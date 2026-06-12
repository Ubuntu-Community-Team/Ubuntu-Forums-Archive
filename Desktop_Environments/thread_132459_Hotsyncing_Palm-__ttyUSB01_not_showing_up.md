---
title: "Hotsyncing Palm-  ttyUSB0/1 not showing up"
date: 2006-02-18
forum: Desktop Environments
---

### Post by danyul on 2006-02-18
Hi all,

I've been trying to get a Treo to sync with _anything_ under (K)ubuntu.  My understanding is that /dev/ttyUSB0 and/or /dev/ttyUSB1 should be created upon my pressing the hotsync button.


Now, when I press the hotsync button, /var/log/messages says:

Feb 18 11:35:38 localhost kernel: [4860846.097000] usb 2-2: new full speed USB device using ohci_hcd and address 14
Feb 18 11:35:38 localhost kernel: [4860846.210000] visor 2-2:1.0: Handspring Visor / Palm OS converter detected
Feb 18 11:35:38 localhost kernel: [4860846.213000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Feb 18 11:35:38 localhost kernel: [4860846.219000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Feb 18 11:35:38 localhost usb.agent[14462]:      visor: already loaded

And lsusb says:

Bus 003 Device 002: ID 0d49:7010 Maxtor
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 014: ID 0830:0061 Palm, Inc.
Bus 002 Device 002: ID 0a48:3239 I/O Interconnect
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 045e:0023 Microsoft Corp. Trackball Optical
Bus 001 Device 001: ID 0000:0000

And dmesg says:
[4860846.097000] usb 2-2: new full speed USB device using ohci_hcd and address 14
[4860846.210000] visor 2-2:1.0: Handspring Visor / Palm OS converter detected
[4860846.213000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
[4860846.219000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB1


However, despite what dmesg tells me,  there doesn't appear to actually be a /dev/ttyUSB0 or /dev/ttyUSB1 created.  I've tried syncing with gpilot, kpilot, jpilot, all to no avail- it just acts like there's nothing connected, even if I press the Hotsync button first.  I've tried this with a Treo and also a friend's T3.  I'm using KDE, but I think I had a similar problem under Gnome.  I'm running Kubuntu 5.10 now.   I've found several forum posts of people with similar problems, but nothing really fixed my issue. Does anyone have any ideas?  Thanks very much.

Best,
Dan

---

### Post by danyul on 2006-02-18
OK after much headbanging, I figured out that I had to remove custom udev rules in /etc/udev/rules.d/  . I can't remember if they were there originally or whether they were something I had done in an attempt to get my palm to sync. I found the following post educational, even though it turns out I probably didn't need to do what the poster did in order to get things to work:

[http://mail.kde.org/pipermail/kdepim-users/2006-January/006346.html](http://mail.kde.org/pipermail/kdepim-users/2006-January/006346.html)

I also had to chmod my /dev/ttyUSB0, /dev/ttyUSB1 and/or dev/pilot to 666 in order to get it to work and not tell me that it "Cannot accept Pilot (Connection timed out)".  

The syncing works most of the time now- I'm not sure, but it seems I still occasionally have to do the chmodding in order to get it to work, as the ttyUSB*'s are not persistent, but for now I'm happy to have it working.

Now I have my web-based AirSet calendar ( [http://airset.com/](http://airset.com/) ) syncing with Kontact syncing with my Treo.  How awesome is that?  [And to add to the coolness, I have a Basecamp ([http://basecamphq.com](http://basecamphq.com)) account syncing with Airset .  These are all very cool tools/toys. ]

Cheers,
Dan

---

