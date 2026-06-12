---
title: "Repairing accidentally unpaired bluetooth 8bitdo controller"
date: 2019-09-29
forum: Gaming &amp; Leisure
---

### Post by stevedinn on 2019-09-29
I accidentally unpaired an 8bitdo SNES bluetooth controller from my lubuntu machine running RetroPie (where it was working fine). I went to re-pair it, but it never shows up as a device when I attempt to scan for new bluetooth devices. I'm sure I'm doing everything the same as I did it the first time. I've also tried *hard* removing the devices from /var/lib/bluetooth/ to make sure it wasn't a caching issue, but they still don't show up.

Anybody have any ideas?

Like I said, this was *just* working. Here is the output from "[FONT=courier new]sudo systemctl status bluetooth.service[/FONT]":

[FONT=courier new]&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2019-09-29 18:50:38 ADT; 42min ago
     Docs: man:bluetoothd(8)
 Main PID: 551 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 2115)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;551 /usr/lib/bluetooth/bluetoothd

Sep 29 18:50:37 arcee systemd[1]: Starting Bluetooth service...
Sep 29 18:50:37 arcee bluetoothd[551]: Bluetooth daemon 5.48
Sep 29 18:50:38 arcee systemd[1]: Started Bluetooth service.
Sep 29 18:50:38 arcee bluetoothd[551]: Starting SDP server
Sep 29 18:50:39 arcee bluetoothd[551]: Bluetooth management interface 1.14 initialized
Sep 29 18:50:39 arcee bluetoothd[551]: LEAdvertisingManager skipped, LE unavailable[/FONT]

Steve.

---

### Post by charlieg on 2019-10-01
Are you powering on the controller properly? IIRC you have to power it on in different ways to make it appear ready for pairing to various devices.

---

