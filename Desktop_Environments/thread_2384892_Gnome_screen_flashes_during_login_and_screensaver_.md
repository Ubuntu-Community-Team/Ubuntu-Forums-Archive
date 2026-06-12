---
title: "Gnome screen flashes during login and screensaver error every boot"
date: 2018-02-13
forum: Desktop Environments
---

### Post by richard378 on 2018-02-13
Ubuntu 17.10.1 fresh installs.  Every login the screen flashes brief moments multiple times when the screen is blank, for unknown reason and the following error repeats multiple fresh installs.  Always the gnome screen errors.

Important logs include
15:38:43 gnome-session-b: Unrecoverable failure in required component org.gnome.Shell.desktop
15:38:43 gnome-session-b: Unrecoverable failure in required component org.gnome.Shell.desktop
15:38:43 gnome-session-b: CRITICAL: Unable to create a DBus proxy for GnomeScreensaver: Error calling StartServiceByName for org.gnome.ScreenSaver: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.ScreenSaver exited with status 1

journalctl -b includes
Feb 13 15:38:42 richard-Z97-HD3 dbus-daemon[934]: Activating service name='org.gnome.ScreenSaver'
Feb 13 15:38:43 richard-Z97-HD3 org.gnome.ScreenSaver[934]: Unable to init server: Could not connect: Connection refused
Feb 13 15:38:43 richard-Z97-HD3 gnome-screensav[942]: Cannot open display: 
Feb 13 15:38:43 richard-Z97-HD3 dbus-daemon[934]: Activated service 'org.gnome.ScreenSaver' failed: Process org.gnome.ScreenSaver exited with status 1
Feb 13 15:38:43 richard-Z97-HD3 gnome-session[936]: gnome-session-binary[936]: CRITICAL: Unable to create a DBus proxy for GnomeScreensaver: Error calling StartServiceByName for org.gnome.ScreenSaver: GDB
Feb 13 15:38:43 richard-Z97-HD3 gnome-session-binary[936]: CRITICAL: Unable to create a DBus proxy for GnomeScreensaver: Error calling StartServiceByName for org.gnome.ScreenSaver: GDBus.Error:org.freedes
Feb 13 15:38:43 richard-Z97-HD3 gnome-shell[944]: Can't initialize KMS backend: could not find drm kms device
Feb 13 15:38:43 richard-Z97-HD3 gnome-session[936]: gnome-session-binary[936]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Feb 13 15:38:43 richard-Z97-HD3 gnome-session-binary[936]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Feb 13 15:38:43 richard-Z97-HD3 gnome-session-binary[936]: Unrecoverable failure in required component org.gnome.Shell.desktop
Feb 13 15:38:43 richard-Z97-HD3 gdm-launch-environment][914]: pam_unix(gdm-launch-environment:session): session closed for user gdm
Feb 13 15:38:43 richard-Z97-HD3 gdm3[909]: GdmDisplay: display lasted 2.355488 seconds

How do I fix this error with gnome xorg.  I'm just starting to use Ubuntu duel boot and don't know how to debug this problem.  Xorg has changed recently and I am unfamiliar with the xorg that does not need the old config file and where to find the log files for Xorg.
I'm using NVIDIA-390 drivers.  It says there is a bus error and I am unsure what to do.

---

### Post by cruzer001 on 2018-02-14
> Xorg has changed recently and I am unfamiliar with the xorg

Are you sure your on xorg and not wayland?

```
echo $XDG_SESSION_TYPE
```

It can be change at the login screen, the gear in the upper right of the screen.

---

### Post by richard378 on 2018-02-16
I have a new install of Ubuntu 17.10.1 and there is not Wayland option with my install.

Yes I am running only X11 and don't think Wayland is installed.

echo $XDG_SESSION_TYPE
Responds as 
X11

---

### Post by cruzer001 on 2018-02-16
> I have a new install of Ubuntu 17.10.1 and there is not Wayland option with my install

Wayland is suppose to be the default install.  Maybe something has recently changed.  Anyhow your on xorg.

Back to the problem(s).

Gnome screen saver is giving you grief so lets just remove it for now.
```
sudo apt purge gnome-screensaver
```
If this spits back a long list of packages to remove, please post the list and opp out of the removal.  17.10 packaging is set up differently than my 16.04 install and just not sure what to expect.

Also did you checksum the download?  If a DVD install, did you burn at low speed?

---

### Post by #&amp;thj^% on 2018-02-16
> I'm using NVIDIA-390 drivers. It says there is a bus error and I am unsure what to do. 

You will see no wayland option with the Nvidia blob installed! (They just don't play nice with each other)
If you want a wayland session then remove the Nvidia Driver! ;)
If you want:
```
sudo apt purge 'nvidia-*'
```

---

### Post by richard378 on 2018-02-16
Purge worked.  Thanks.  It stopped the screen from flashing.  It leaves a minor boot log error that is I guess expected unimportant:
Unrecoverable failure in required component org.gnome.Shell.desktop

And pulse audio is now complaining that DBUS cant be found in bluetooth service which I don't use.  No bluetooth installed.  Not important either.
 
I did a torrent download so the checksum should have been done automatically.  And it is on USB not specific burn speed.

And no I am not interested in Wayland manager, I am fine with using xorg.

It seems the gnome error is now the DBUS PCI on my CPU generating the error.:
It is a hardware driver problem now.

Feb 16 19:17:54 richard-Z97-HD3 systemd[1033]: Started D-Bus User Message Bus.
Feb 16 19:17:55 richard-Z97-HD3 ModemManager[847]: <info>  Couldn't check support for device at '/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0': not supported by any plugin
Feb 16 19:17:56 richard-Z97-HD3 gnome-shell[1049]: Can't initialize KMS backend: could not find drm kms device
Feb 16 19:17:56 richard-Z97-HD3 gnome-session[1043]: gnome-session-binary[1043]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Feb 16 19:17:56 richard-Z97-HD3 gnome-session-binary[1043]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Feb 16 19:17:56 richard-Z97-HD3 gnome-session-binary[1043]: Unrecoverable failure in required component org.gnome.Shell.desktop

Which was fixed with the following:
I added a kernel boot option pci=noaer according to the following bugzilla : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173)

which had the effect removed the Can't initialize KMS backend: could not find drm kms device:

Feb 16 20:22:51 richard-Z97-HD3 gnome-session[1022]: gnome-session-binary[1022]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Feb 16 20:22:51 richard-Z97-HD3 gnome-session-binary[1022]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Feb 16 20:22:51 richard-Z97-HD3 gnome-session-binary[1022]: Unrecoverable failure in required component org.gnome.Shell.desktop
Feb 16 20:22:51 richard-Z97-HD3 gdm-launch-environment][971]: pam_unix(gdm-launch-environment:session): session closed for user gdm

Then after reboot Can't initialize KMS backend: could not find drm kms device returned and is not a significant error.
But the PCI error I was getting is now gone.

It is solved for now.

---

### Post by richard378 on 2018-02-17
It a bug.

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1736011](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1736011)

The whole problem I have been having is a known bug.  Sorry to distub you all. I was slow finding the bug report.

---

### Post by cruzer001 on 2018-02-17
Good find :)

You can either run the open source driver or try removing gnome-screensaver till its fix.

):P

---

### Post by cruzer001 on 2018-02-19
> **1fallen said:**
> You will see no wayland option with the Nvidia blob installed! (They just don't play nice with each other)
If you want a wayland session then remove the Nvidia Driver!

There must be strange exceptions to the rule.  OP of this link is running Nvida driver and Wayland.

[https://ubuntuforums.org/showthread.php?t=2385264&p=13741312#post13741312](https://ubuntuforums.org/showthread.php?t=2385264&p=13741312#post13741312)

Wonder what the difference is.

---

### Post by #&amp;thj^% on 2018-02-19
> **cruzer001 said:**
> There must be strange exceptions to the rule.  
Wonder what the difference is.
This has been improving with time (Updates), I also run Nvidia on 18.04 with a PPA.
Maybe the 340 Driver is the exception here. I just don't know?
What I do know is I prefer the X11 session, til they get wayland polished.;)

---

