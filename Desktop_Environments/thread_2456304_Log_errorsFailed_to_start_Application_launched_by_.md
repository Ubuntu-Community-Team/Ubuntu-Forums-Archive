---
title: "Log errors:Failed to start Application launched by gnome-session-binary"
date: 2021-01-08
forum: Desktop Environments
---

### Post by apg6xswhjc on 2021-01-08
I'm on 20.10 (upgraded from 20.04 etc) and have noticed some errors I hadn't seen before.

I've extracted the following from the log, with the preceding 10 lines of log from each occurence.

```

Jan 09 10:07:19 myUbuntu systemd[1949]: Finished Start gnome-keyring for the Secrets Service, and PKCS #11.
Jan 09 10:07:19 myUbuntu systemd[1949]: Reached target Session services which should run early before the graphical session is brought up.
Jan 09 10:07:19 myUbuntu systemd[1949]: Reached target Tasks to be run before GNOME Session starts.
Jan 09 10:07:19 myUbuntu systemd[1949]: Starting GNOME Session Manager (session: ubuntu)...
Jan 09 10:07:19 myUbuntu gnome-session[2182]: gnome-session-binary[2182]: WARNING: Could not parse desktop file gnome-software-service.desktop or it references a not found TryExec binary
Jan 09 10:07:19 myUbuntu gnome-session-binary[2182]: WARNING: Could not parse desktop file gnome-software-service.desktop or it references a not found TryExec binary
Jan 09 10:07:19 myUbuntu gnome-keyring-daemon[1964]: The Secret Service was already initialized
Jan 09 10:07:19 myUbuntu gnome-keyring-daemon[1964]: The PKCS#11 component was already initialized
Jan 09 10:07:19 myUbuntu systemd[1949]: app-gnome-gnome\x2dkeyring\x2dpkcs11-2189.scope: Failed to add PIDs to scope's control group: No such process
Jan 09 10:07:19 myUbuntu systemd[1949]: app-gnome-gnome\x2dkeyring\x2dpkcs11-2189.scope: Failed with result 'resources'.
Jan 09 10:07:19 myUbuntu systemd[1949]: Failed to start Application launched by gnome-session-binary.
Jan 09 10:07:19 myUbuntu systemd[1949]: app-gnome-gnome\x2dkeyring\x2dsecrets-2188.scope: Failed to add PIDs to scope's control group: No such process
Jan 09 10:07:19 myUbuntu systemd[1949]: app-gnome-gnome\x2dkeyring\x2dsecrets-2188.scope: Failed with result 'resources'.
Jan 09 10:07:19 myUbuntu systemd[1949]: Failed to start Application launched by gnome-session-binary.
--
Jan 09 10:07:21 myUbuntu gnome-session-binary[2182]: GnomeDesktop-WARNING: Could not create transient scope for PID 2366: GDBus.Error:org.freedesktop.DBus.Error.UnixProcessIdUnknown: Process with ID 2366 does not exist.
Jan 09 10:07:21 myUbuntu gnome-session[2182]: gnome-session-binary[2182]: GnomeDesktop-WARNING: Could not create transient scope for PID 2366: GDBus.Error:org.freedesktop.DBus.Error.UnixProcessIdUnknown: Process with ID 2366 does not exist.
Jan 09 10:07:21 myUbuntu systemd[1949]: Started GNOME color management service.
Jan 09 10:07:21 myUbuntu systemd[1949]: Started GNOME date & time service.
Jan 09 10:07:21 myUbuntu systemd[1949]: Started Application launched by gnome-session-binary.
Jan 09 10:07:21 myUbuntu systemd[1949]: Started Application launched by gnome-session-binary.
Jan 09 10:07:21 myUbuntu systemd[1949]: Started Application launched by gnome-session-binary.
Jan 09 10:07:21 myUbuntu systemd[1949]: Started Application launched by gnome-session-binary.
Jan 09 10:07:21 myUbuntu systemd[1949]: app-gnome-user\x2ddirs\x2dupdate\x2dgtk-2392.scope: Failed to add PIDs to scope's control group: No such process
Jan 09 10:07:21 myUbuntu systemd[1949]: app-gnome-user\x2ddirs\x2dupdate\x2dgtk-2392.scope: Failed with result 'resources'.
Jan 09 10:07:21 myUbuntu systemd[1949]: Failed to start Application launched by gnome-session-binary.

```

I've searched, but have failed to find any possible troubleshooting steps or possible solutions :(

Thanks in advance for any help

---

### Post by dino99 on 2021-01-09
Mine works; have some warnings (yellow lines) but not errors (red lines from 'journalctl -b' output.

Be sure to only use 'hirsute' entries inside /etc/apt/sources.list
Avoid non genuine source (ppa, ...); deactivate if needed and downgrade package .
Then clean the system via autoremove/autoclean; and update again and reboot.

---

### Post by apg6xswhjc on 2021-01-09
I may have misled you. I upgraded months ago, so have already rebooted autoclean/autoremoved etc. I only noticed them in the past few days.

The system boots and works AFAICT, but I dont' know why these errors show, why they happen or how to fix them.

---

