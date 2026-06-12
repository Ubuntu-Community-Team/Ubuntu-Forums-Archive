---
title: "Can't run gnome-system-monitor, can't file bug report."
date: 2019-03-20
forum: Desktop Environments
---

### Post by HankB on 2019-03-20
First time I tried to run this I got 
```
hbarta@karakum:~$ gnome-system-monitor 
You need to connect this snap to the gnome platform snap.

You can do this with those commands:
snap install gnome-3-26-1604
snap connect gnome-system-monitor:gnome-3-26-1604 gnome-3-26-1604

(the '3-26-1604' number defines the platform version and might change)
hbarta@karakum:~$ 
hbarta@karakum:~$ snap install gnome-3-26-1604
snap "gnome-3-26-1604" is already installed, see 'snap help refresh'
hbarta@karakum:~$ snap connect gnome-system-monitor:gnome-3-26-1604 gnome-3-26-1604
error: snap "gnome-system-monitor" has no plug named "gnome-3-26-1604"
hbarta@karakum:~$ 
```
I removed the snap and installed from the repo and it worked. I then purged that and reinstalled the snap to see if it would fix the issue (or file a bug report.) Following reinstall, I now see a different error.
```
hbarta@karakum:~$ gnome-system-monitor
Failed to register: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.76" (uid=1000 pid=5501 comm="gnome-system-monitor " label="snap.gnome-system-monitor.gnome-system-monitor (enforce)") interface="org.gtk.Actions" member="DescribeAll" error name="(unset)" requested_reply="0" destination="org.gnome.SystemMonitor" (uid=1000 pid=3975 comm="gnome-system-monitor " label="unconfined")
hbarta@karakum:~$ 
```
I tried to file a big report and got this.
[IMG]https://i.postimg.cc/SNNKXvTC/Screenshot-from-2019-03-20-08-25-36-crop.png[/IMG]
It would be really helpful if ubuntu-bug reported the URL it was unable to contact. I'm using secure DNS via Cloudflare and I have to provide exceptions for some questionably configured hosts.

Ubuntu 18.04.2 and up to date. (via apt update; apt upgrade.)

---

### Post by HankB on 2019-03-20
And now it works. (both.) gnome-system-monitor snap runs and before that happened I was able ti file a bug report.

---

