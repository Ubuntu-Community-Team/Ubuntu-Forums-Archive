---
title: "VNC disconnect right after remote login after boot"
date: 2007-12-22
forum: Desktop Environments
---

### Post by benruza on 2007-12-22
I have one laptop and two server boxes all running Gutsy. I want to use VNC to remote login to the server boxes even after hard-reboot of the servers. I saw a post solution [http://ubuntuforums.org/showthread.php?t=265983]("http://ubuntuforums.org/showthread.php?t=265983")
And it worked. 

I can see the login screen of my server box in vncviewer. But once I login, my VNC session immediate dropped. I checked and double checked the "gdm.conf" file, and there is a line "KillInitClients=false".

See below for the error messages I got. The problem is very similar to a previous post [http://ubuntuforums.org/showthread.php?t=303554]("http://ubuntuforums.org/showthread.php?t=303554")  However, the KillInitClients setting is not the culprit. 

Anybody knows what's the problem of the dropped X session?

Benruza



22/12/2007 02:32:53 Using ZRLE encoding for client 192.168.1.13
22/12/2007 02:32:53 Pixel format for client 192.168.1.13:
22/12/2007 02:32:53   32 bpp, depth 24, little endian
22/12/2007 02:32:53   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
22/12/2007 02:32:53 no translation needed
22/12/2007 02:32:53 Enabling full-color cursor updates for client 192.168.1.13
22/12/2007 02:32:53 Enabling NewFBSize protocol extension for client 192.168.1.13
22/12/2007 02:32:53 Switching from ZRLE to hextile Encoding for client 192.168.1.13
22/12/2007 02:32:53 client 1 network rate 1251.9 KB/sec (20287.5 eff KB/sec)
22/12/2007 02:32:53 client 1 latency:  0.5 ms
22/12/2007 02:32:53 dt1: 0.3775, dt2: 0.0015 dt3: 0.0005 bytes: 474066
22/12/2007 02:32:53 link_rate: LR_LAN - 1 ms, 1251 KB/s
caught X11 error:
22/12/2007 02:33:02 deleted 50 tile_row polling images.
22/12/2007 02:33:02 Restored X server key autorepeat to: 1
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  145 (MIT-SHM)
  Minor opcode of failed request:  4 (X_ShmGetImage)
  Serial number of failed request:  3782
  Current serial number in output stream:  3784

---

### Post by benruza on 2008-01-04
Hello, anybody out there?

---

