---
title: "Ubuntu 16.10: Gnome shell not working after dist-upgrade"
date: 2017-01-03
forum: Desktop Environments
---

### Post by stephenm002 on 2017-01-03
Hey all, I'm fairly new to linux.
When I do an apt-get update and apt-get dist-upgrade on a fresh install  of ubuntu gnome 16.10 I run into a problem with gnome-tweak-tool telling  me
```

WARNING : Shell not installed or running
WARNING : Shell not running
None
WARNING : Error detecting shell
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_group_shell_extensions.py", line 275, in __init__
    raise Exception("Shell not running or DBus service not available")
Exception: Shell not running or DBus service not available

```
I've confirmed before/after the upgrade and it seems to only occur after  the upgrade. I've formatted the partition and tried again with the same  results. I've tried to fix the problem with various fixes online (most  notably adding the gnome3 PPA repo, updating and trying to do an  upgrade/dist-upgrade, but this doesn't provide any new packages) but I  can't seem to fix it.
I've tried installing gnome and gnome-shell after adding the repo but that didn't fix the issue.
I've confirmed this with the extensions.gnome.org site (after enabling  the plugin) and it seems to confirm that I don't have gnome shell  installed.

The dist update has modified the following packages
```

The following NEW packages will be installed:
  libgspell-1-common libsnapd-glib1 linux-headers-4.8.0-32
  linux-headers-4.8.0-32-generic linux-image-4.8.0-32-generic
  linux-image-extra-4.8.0-32-generic linux-signed-image-4.8.0-32-generic
  snapd-login-service
The following packages will be upgraded:
  apport apport-gtk cups-browsed cups-filters cups-filters-core-drivers
  deja-dup deja-dup-backend-cloudfiles deja-dup-backend-s3 evolution
  evolution-common evolution-plugins file-roller firefox ghostscript
  ghostscript-x gnome-control-center gnome-control-center-data
  gnome-settings-daemon gnome-settings-daemon-schemas gnome-shell
  gnome-shell-common gnome-software gnome-software-common
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio iio-sensor-proxy im-config
  imagemagick imagemagick-6.q16 libavcodec57 libavformat57 libavutil55
  libcupsfilters1 libcurl3 libevolution libfontembed1 libgd3 libgme0 libgs9
  libgs9-common libgspell-1-1 libgstreamer-plugins-good1.0-0
  libmagickcore-6.q16-2-extra libnautilus-extension1a libpulse-mainloop-glib0
  libpulse0 libpulsedsp libswresample2 libswscale4 linux-firmware
  linux-generic linux-headers-generic linux-image-generic linux-signed-generic
  linux-signed-image-generic nautilus nautilus-data pulseaudio
  pulseaudio-module-bluetooth pulseaudio-utils python-cryptography
  python3-cryptography snapd unattended-upgrades xserver-xephyr xwayland

```

trying systemctl status dbus gives me
```

&#9679; dbus.service - D-Bus System Message Bus
   Loaded: loaded (/lib/systemd/system/dbus.service; static; vendor preset: enabled)
   Active: active (running) since Wed 2017-01-04 01:41:41 AWST; 30min ago
     Docs: man:dbus-daemon(1)
 Main PID: 733 (dbus-daemon)
    Tasks: 8 (limit: 4915)
   CGroup: /system.slice/dbus.service
           &#9500;&#9472; 733 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation
           &#9492;&#9472;1972 /usr/lib/x86_64-linux-gnu/fwupd/fwupd

Jan 04 01:45:29 Box dbus[733]: [system] Reloaded configuration
Jan 04 01:46:53 Box dbus[733]: [system] Reloaded configuration
Jan 04 01:47:13 Box dbus[733]: [system] Reloaded configuration
Jan 04 01:47:44 Box dbus[733]: [system] Reloaded configuration
Jan 04 01:50:41 Box dbus[733]: [system] Activating via systemd: service  name='org.freedesktop.hostname1'  unit='dbus-org.freedesktop.hostname1.service'
Jan 04 01:50:41 Box dbus[733]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jan 04 02:03:15 Box dbus[733]: [system] Activating via systemd: service  name='org.freedesktop.hostname1'  unit='dbus-org.freedesktop.hostname1.service'
Jan 04 02:03:15 Box dbus[733]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jan 04 02:11:20 Box dbus[733]: [system] Activating via systemd: service  name='org.freedesktop.hostname1'  unit='dbus-org.freedesktop.hostname1.service'
Jan 04 02:11:21 Box dbus[733]: [system] Successfully activated service 'org.freedesktop.hostname1'

```

dbus-monitor gives me
```

signal time=1483467180.999467 sender=org.freedesktop.DBus ->  destination=:1.34 serial=2 path=/org/freedesktop/DBus;  interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.34"
signal time=1483467180.999519 sender=org.freedesktop.DBus ->  destination=:1.34 serial=4 path=/org/freedesktop/DBus;  interface=org.freedesktop.DBus; member=NameLost
   string ":1.34"

```

I'm not sure how to proceed with figuring out how to fix this or prevent it from happening on a fresh install. Does anyone have any suggestions?

---

### Post by deadflowr on 2017-01-03
Let's see if we can find out the current desktop in use.
Post the output, if any, for:
```
printenv | grep XDG_CURRENT_DESKTOP
```

---

### Post by stephenm002 on 2017-01-03
Thanks Deadflowr.

printenv | grep XDG_CURRENT_DESKTOP on root gives nothing
on normal user gives XDG_CURRENT_DESKTOP=GNOME

I'll also add that nividia-smi gives

```

+-----------------------------------------------------------------------------+
| NVIDIA-SMI 367.57                 Driver Version: 367.57                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 970M    Off  | 0000:01:00.0     Off |                  N/A |
| N/A   54C    P0    21W / 300W |    272MiB /  3016MiB |      1%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0      4693    G   /usr/lib/xorg/Xorg                             119MiB |
|    0      4879    G   /usr/bin/gnome-shell                           114MiB |
|    0     26841    G   /usr/lib/xorg/Xorg                              38MiB 

```

I think that indicates that I'm using gnome-shell.

I'll further add that my runnings processes (ps ax | grep gnome) gives me

```


stephen@Box:~$ ps ax | grep gnome
 1806 ?        Sl     0:00 /usr/lib/gnome-shell/gnome-shell-calendar-server
 1822 ?        Sl     0:00 /usr/lib/x86_64-linux-gnu/gnome-online-accounts/goa-daemon
 1833 ?        Sl     0:00 /usr/lib/x86_64-linux-gnu/gnome-online-accounts/goa-identity-service
 2005 ?        Sl     0:00 /usr/lib/evolution/evolution-calendar-factory-subprocess --factory contacts --bus-name org.gnome.evolution.dataserver.Subprocess.Backend.Calendarx1969x2 --own-path /org/gnome/evolution/dataserver/Subprocess/Backend/Calendar/1969/2
 2030 ?        Sl     0:00 /usr/lib/evolution/evolution-calendar-factory-subprocess --factory local --bus-name org.gnome.evolution.dataserver.Subprocess.Backend.Calendarx1969x3 --own-path /org/gnome/evolution/dataserver/Subprocess/Backend/Calendar/1969/3
 2058 ?        Sl     0:00 /usr/lib/evolution/evolution-addressbook-factory-subprocess --factory local --bus-name org.gnome.evolution.dataserver.Subprocess.Backend.AddressBookx2026x2 --own-path /org/gnome/evolution/dataserver/Subprocess/Backend/AddressBook/2026/2
 4683 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
 4691 tty2     Ssl+   0:00 /usr/lib/gdm3/gdm-x-session --run-script gnome-session --session=gnome
 4748 tty2     Sl+    0:00 /usr/lib/gnome-session/gnome-session-binary --session=gnome
 4830 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/im-launch gnome-session --session=gnome
 4860 ?        Sl     0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
 4879 tty2     Rl+    1:04 /usr/bin/gnome-shell
 4909 tty2     Sl+    0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 4941 tty2     SLl+   0:01 /usr/bin/gnome-software --gapplication-service
 4989 tty2     Sl+    0:00 /usr/lib/gnome-settings-daemon/gsd-printer
 5053 ?        Ssl    0:03 /usr/lib/gnome-terminal/gnome-terminal-server
 5214 pts/0    Tl     0:01 /usr/bin/python /usr/bin/gnome-tweak-tool
 5225 ?        Sl     0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
 5424 ?        Sl     0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
 7350 pts/1    S+     0:00 grep --color=auto gnome
22517 ?        Sl     0:00 /usr/lib/x86_64-linux-gnu/gnome-online-accounts/goa-daemon
22525 ?        Sl     0:00 /usr/lib/x86_64-linux-gnu/gnome-online-accounts/goa-identity-service
26837 tty1     Ssl+   0:00 /usr/lib/gdm3/gdm-x-session gnome-session --autostart /usr/share/gdm/greeter/autostart
26976 tty1     Sl+    0:00 /usr/lib/gnome-session/gnome-session-binary --autostart /usr/share/gdm/greeter/autostart
26986 ?        Sl     0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
27002 tty1     Sl+    0:05 /usr/bin/gnome-shell
27787 tty1     Sl+    0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon

```

Sorry if I'm giving too much information, I'm not sure what it is I need to be looking for.

---

### Post by deadflowr on 2017-01-03
Did you run gnome-tweak-tool as root (with sudo)?
No need.
Run as is without sudo.

---

### Post by stephenm002 on 2017-01-03
I did and that fixed that error!

I'm now getting 

```

** (gnome-tweak-tool:7906): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(gnome-tweak-tool:7906): Gtk-WARNING **: Attempting to read the recently used resources file at '/home/stephen/.local/share/recently-used.xbel', but the parser failed: Failed to open file '/home/stephen/.local/share/recently-used.xbel': Permission denied.


```

But it seems that gnome tweak tool is working, and by the looks of it those errors can be suppressed with export [NO_AT_BRIDGE=1]("http://computing.help.inf.ed.ac.uk/accessibility-bus")
I can't quite figure out why running gnome-tweak-tool with sudo/root would do that, is there an explanation that'd help me in the future?

---

