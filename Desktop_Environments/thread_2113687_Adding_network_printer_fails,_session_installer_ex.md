---
title: "Adding network printer fails, session installer experiences internal error"
date: 2013-02-08
forum: Desktop Environments
---

### Post by frankvw on 2013-02-08
I have a Samsung laser printer hanging off a Karmic server, which I'm trying to install on a laptop running Precise Pangolin. Standard procedure:
[LIST]
[*]Click "add printer" button
[*]Click "network"
[*]Enter server hostname and check "Search by Address"
[*]Printer is found, click 'Add' button-
[*]"Printer Added "popup appears in top right hand corner of screen.
[/LIST]
Printer is shown as "ready". So far so good. But when I click the "Print test page" button, jobs appear as "stopped" in the queue, the buttons to stop/start/pause jobs are grayed out, and an error message pops up marked "Session installer" telling me that "Ubuntu experienced an internal error". There's no further information about what went wrong, where and why. (Which I'm used to when running Windows but not Ubuntu.) In /var/log/syslog there's no info except a few lines suggesting that all went well:

```
Feb  8 09:51:58 HP-550 dbus[608]: [system] Activating service name='org.opensuse.CupsPkHelper.Mechanism' (using servicehelper)
Feb  8 09:51:58 HP-550 dbus[608]: [system] Successfully activated service 'org.opensuse.CupsPkHelper.Mechanism'

```
(repeated 4 times).

Suggestion on how to proceed, anyone? Tnx!

// FvW

---

