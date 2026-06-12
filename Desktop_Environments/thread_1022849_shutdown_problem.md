---
title: "shutdown problem"
date: 2008-12-27
forum: Desktop Environments
---

### Post by damiens on 2008-12-27
I have a serious problem with ubuntu 8.10 shutdown.
On my PC it looks like it (i have disabled graphic interface to read messages):

The system is going down for halt NOW!
* Stopping GNOME Display Manager... [OK]
* Stopping web server apache2           [OK]
* Saved ALSA mixer settings detected; aumix will not touch mixer.

and that's it, it never finishes shutdown (I waited for 20 minutes before manually rebooting).

The problem occurs always at shutdown ( not if I restart).

I think it's a bug and I don't know what to do. Please help.

---

### Post by kerry_s on 2008-12-27
check in synaptic, make sure hal is installed.

---

### Post by iponeverything on 2008-12-27
> **damiens said:**
> I have a serious problem with ubuntu 8.10 shutdown.
On my PC it looks like it (i have disabled graphic interface to read messages):

The system is going down for halt NOW!
* Stopping GNOME Display Manager... [OK]
* Stopping web server apache2           [OK]
* Saved ALSA mixer settings detected; aumix will not touch mixer.

and that's it, it never finishes shutdown (I waited for 20 minutes before manually rebooting).

The problem occurs always at shutdown ( not if I restart).

I think it's a bug and I don't know what to do. Please help.
not sure if this your issue:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995)

---

### Post by damiens on 2009-01-07
Following the suggestion of kerry_s I verified that hal was installed.
I tried also uninstalling alsa sound packages but the problem persists.
I was never able to complete the shutdown. The system goes always in text mode with cursor blinking and power on. The only thing I can do is to to switch off manually.

The system is a desktop based on an AMD Sempron 3000+ 2 GHz with the following configuration:
Fast Ethernet VIA compatibile board,
C-Media AC97 sound support
NVidia GeForce FX 5700LE
Maxtor 6Y160P0 127 GB + 25 GB
IE1395N UCN615Q SCSI CdRom Device
Pioneer DVD-RW DVR-109

I would like to invest to understand the reason of the problem but I don't know if it's possible to log the shutdown process at a very detailed level.

Thanks for any suggestion or help in this direction.

---

