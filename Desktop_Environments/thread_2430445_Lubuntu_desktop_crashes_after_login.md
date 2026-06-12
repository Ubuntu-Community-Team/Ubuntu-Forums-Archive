---
title: "Lubuntu desktop crashes after login"
date: 2019-11-01
forum: Desktop Environments
---

### Post by giacomofontanelli76 on 2019-11-01
Dear forum

I use Lubuntu 19.10, my kernel is 5.3.0-19-generic.

Each time I start the PC I get an error after login "Desktop crashed too many times. Its automatic start will be disabled until nex start.

you can find in attach the log error of xsession

```
X connection to :0 broken (explicit kill or server shutdown).
The X11 connection broke (error 1). Did the X11 server die?
The X11 connection broke (error 1). Did the X11 server die?
Gdk-Message: 23:08:48.356: dropbox: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.

Xsession: X session started for giacomo at ven 1 nov 2019, 23:09:04, CET
dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
dbus-update-activation-environment: setting DISPLAY=:0
dbus-update-activation-environment: setting XAUTHORITY=/home/giacomo/.Xauthority
localuser:giacomo being added to access control list
dbus-update-activation-environment: setting SHELL=/bin/bash
dbus-update-activation-environment: setting XDG_CONFIG_DIRS=/etc/xdg/xdg-Lubuntu:/etc/xdg
dbus-update-activation-environment: setting XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session6
dbus-update-activation-environment: setting LC_ADDRESS=it_IT.UTF-8
dbus-update-activation-environment: setting LC_NAME=it_IT.UTF-8
dbus-update-activation-environment: setting DESKTOP_SESSION=Lubuntu
dbus-update-activation-environment: setting LC_MONETARY=it_IT.UTF-8
dbus-update-activation-environment: setting PWD=/home/giacomo
dbus-update-activation-environment: setting XDG_SESSION_DESKTOP=
dbus-update-activation-environment: setting LOGNAME=giacomo
dbus-update-activation-environment: setting XDG_SESSION_TYPE=x11
dbus-update-activation-environment: setting GPG_AGENT_INFO=/run/user/1000/gnupg/S.gpg-agent:0:1
dbus-update-activation-environment: setting XAUTHORITY=/home/giacomo/.Xauthority
dbus-update-activation-environment: setting HOME=/home/giacomo
dbus-update-activation-environment: setting IM_CONFIG_PHASE=1
dbus-update-activation-environment: setting LC_PAPER=it_IT.UTF-8
dbus-update-activation-environment: setting LANG=it_IT.UTF-8
dbus-update-activation-environment: setting XDG_CURRENT_DESKTOP=
dbus-update-activation-environment: setting XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
dbus-update-activation-environment: setting XDG_SESSION_CLASS=user
dbus-update-activation-environment: setting LC_IDENTIFICATION=it_IT.UTF-8
dbus-update-activation-environment: setting USER=giacomo
dbus-update-activation-environment: setting DISPLAY=:0
dbus-update-activation-environment: setting SHLVL=1
dbus-update-activation-environment: setting LC_TELEPHONE=it_IT.UTF-8
dbus-update-activation-environment: setting LC_MEASUREMENT=it_IT.UTF-8
dbus-update-activation-environment: setting XDG_RUNTIME_DIR=/run/user/1000
dbus-update-activation-environment: setting LC_TIME=it_IT.UTF-8
dbus-update-activation-environment: setting XDG_DATA_DIRS=/usr/share/Lubuntu:/usr/local/share:/usr/share:/var/lib/snapd/desktop
dbus-update-activation-environment: setting PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
dbus-update-activation-environment: setting LC_NUMERIC=it_IT.UTF-8
dbus-update-activation-environment: setting _=/usr/bin/dbus-update-activation-environment
!: 1: Syntax error: Unterminated quoted string
Starting Dropbox...dropbox: locating interpreter
dropbox: logging to /tmp/dropbox-antifreeze-RFA8dJ
dropbox: initializing
dropbox: initializing python 3.7.2
dropbox: setting program path '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/dropbox'
dropbox: setting home path '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170'
dropbox: setting python path '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170:/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/python-packages-37.zip'
dropbox: python initialized
dropbox: running dropbox
dropbox: setting args
dropbox: applying overrides
dropbox: running main script
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/cryptography.hazmat.bindings._constant_time.cpython-37m-x86_64-linux-gnu.so'
(0x7ffc8e95afb0) Debug: systemd: "CanReboot" = "yes"
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/cryptography.hazmat.bindings._openssl.cpython-37m-x86_64-linux-gnu.so'
(0x7ffc8e95afb0) Debug: systemd: "CanPowerOff" = "yes"
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/cryptography.hazmat.bindings._padding.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/psutil._psutil_linux.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/psutil._psutil_posix.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/linuxffi.pthread._linuxffi_pthread.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/cpuid.compiled._cpuid.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/apex._apex.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/tornado.speedups.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/linuxffi.resolv.compiled._linuxffi_resolv.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/librsyncffi.compiled._librsyncffi.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/linuxffi.sys.compiled._linuxffi_sys.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/posixffi.libc._posixffi_libc.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/linuxffi.gnu.compiled._linuxffi_gnu.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/PyQt5.QtCore.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/PyQt5.QtGui.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/PyQt5.QtNetwork.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/PyQt5.QtWidgets.cpython-37m-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84.4.170/PyQt5.QtDBus.cpython-37m-x86_64-linux-gnu.so'
Dropbox isn't running!
Done!
Icon theme "elementary" not found.
Icon theme "elementary" not found.
libGL error: pci id for fd 30: 8086:1912, driver (null)
libGL error: No driver found
libGL error: failed to load driver: (null)
libGL error: pci id for fd 36: 8086:1912, driver (null)
dbus-daemon[1243]: Activating service name='org.a11y.atspi.Registry' requested by ':1.17' (uid=1000 pid=4226 comm="/home/giacomo/.dropbox-dist/dropbox-lnx.x86_64-84." label="unconfined")
dbus-daemon[1243]: Successfully activated service 'org.a11y.atspi.Registry'
SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
(0x7ffc8e95afb0) Warning: Icon theme "elementary" not found.




```

---

