---
title: "Freeze when booting up, can start X server manually"
date: 2012-08-01
forum: Desktop Environments
---

### Post by jamyskis on 2012-08-01
I'm running Ubuntu 12.04 64-bit on a AMD Phenom X4 920 with 4GB RAM under RAID. I have a problem that I have been circumventing for the past six months or so (i.e. with Ubuntu 11.10 as well).

However, this is really starting to bug me. Whenever I boot the system, I'll briefly get a message that cryptswap cannot be mounted (disappears quickly enough), and then the Ubuntu boot splash screen just stays there. The PC doesn't lock up, but eventually all hard drive access ceases.

I can, however, switch to tty3, log in and startx manually. Works fine, no problems. There are no resolution problems, no ATI graphics driver problems.

If I try to run lightdm or gdm manually from the TTY without X started or from the Gnome Terminal (I tried in the hope of being able to copy it out), I get this:

```
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.66" (uid=1000 pid=2896 comm="start gdm ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
```

I've tried reconfiguring lightdm and gdm (separately installed) with dpkg-reconfigure, I've tried removing both and reinstalling them, I've tried removing both altogether and hoping that the TTY will at least appear. It doesn't - whatever I do, it gets stuck on the splash screen.

/var/log/syslog always has a very similar pattern at the end of each boot-up lockup:

```
Aug  1 13:32:49 jamyskis-ubuntu dbus[988]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Aug  1 13:32:49 jamyskis-ubuntu AptDaemon: INFO: Initializing daemon
Aug  1 13:32:49 jamyskis-ubuntu AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Aug  1 13:32:49 jamyskis-ubuntu dbus[988]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Aug  1 13:32:49 jamyskis-ubuntu AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Aug  1 13:32:49 jamyskis-ubuntu dbus[988]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Aug  1 13:32:49 jamyskis-ubuntu dbus[988]: [system] Successfully activated service 'org.freedesktop.hostname1'
Aug  1 13:32:50 jamyskis-ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/f2f0dd525d54475c8379f3ff1d5de2b4
Aug  1 13:32:50 jamyskis-ubuntu AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/f2f0dd525d54475c8379f3ff1d5de2b4
Aug  1 13:32:51 jamyskis-ubuntu AptDaemon.PackageKit: INFO: Get updates()
Aug  1 13:32:51 jamyskis-ubuntu AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/f2f0dd525d54475c8379f3ff1d5de2b4
Aug  1 13:38:49 jamyskis-ubuntu AptDaemon: INFO: Quitting due to inactivity
Aug  1 13:38:49 jamyskis-ubuntu AptDaemon: INFO: Quitting was requested

```

There's nothing there that seems suspicious though.

So I'm at a loss. Can anyone lend a hand?

---

### Post by Bobhuber on 2012-08-01
> **jamyskis said:**
> I'm running Ubuntu 12.04 64-bit on a AMD Phenom X4 920 with 4GB RAM under RAID. I have a problem that I have been circumventing for the past six months or so (i.e. with Ubuntu 11.10 as well).

However, this is really starting to bug me. Whenever I boot the system, I'll briefly get a message that cryptswap cannot be mounted (disappears quickly enough), and then the Ubuntu boot splash screen just stays there. The PC doesn't lock up, but eventually all hard drive access ceases.

I can, however, switch to tty3, log in and startx manually. Works fine, no problems. There are no resolution problems, no ATI graphics driver problems.

If I try to run lightdm or gdm manually from the TTY without X started or from the Gnome Terminal (I tried in the hope of being able to copy it out), I get this:

```
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.66" (uid=1000 pid=2896 comm="start gdm ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
```I've tried reconfiguring lightdm and gdm (separately installed) with dpkg-reconfigure, I've tried removing both and reinstalling them, I've tried removing both altogether and hoping that the TTY will at least appear. It doesn't - whatever I do, it gets stuck on the splash screen.

/var/log/syslog always has a very similar pattern at the end of each boot-up lockup:

```
Aug  1 13:32:49 jamyskis-ubuntu dbus[988]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Aug  1 13:32:49 jamyskis-ubuntu AptDaemon: INFO: Initializing daemon
Aug  1 13:32:49 jamyskis-ubuntu AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Aug  1 13:32:49 jamyskis-ubuntu dbus[988]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Aug  1 13:32:49 jamyskis-ubuntu AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Aug  1 13:32:49 jamyskis-ubuntu dbus[988]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Aug  1 13:32:49 jamyskis-ubuntu dbus[988]: [system] Successfully activated service 'org.freedesktop.hostname1'
Aug  1 13:32:50 jamyskis-ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/f2f0dd525d54475c8379f3ff1d5de2b4
Aug  1 13:32:50 jamyskis-ubuntu AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/f2f0dd525d54475c8379f3ff1d5de2b4
Aug  1 13:32:51 jamyskis-ubuntu AptDaemon.PackageKit: INFO: Get updates()
Aug  1 13:32:51 jamyskis-ubuntu AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/f2f0dd525d54475c8379f3ff1d5de2b4
Aug  1 13:38:49 jamyskis-ubuntu AptDaemon: INFO: Quitting due to inactivity
Aug  1 13:38:49 jamyskis-ubuntu AptDaemon: INFO: Quitting was requested

```There's nothing there that seems suspicious though.

So I'm at a loss. Can anyone lend a hand?
I've had the exactly same problem   before (without the raid setup) using propietary nvidia drivers and it always wound up pointing to a graphics driver problem.

---

### Post by jamyskis on 2012-08-02
> **Bobhuber said:**
> I've had the exactly same problem   before (without the raid setup) using propietary nvidia drivers and it always wound up pointing to a graphics driver problem.

Hmmm...I actually have proprietary ATI drivers, but it's worth a go. I'll uninstall them later and see if that works.

---

