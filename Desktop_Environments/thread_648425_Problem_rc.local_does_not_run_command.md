---
title: "Problem: rc.local does not run command"
date: 2007-12-23
forum: Desktop Environments
---

### Post by seventynine on 2007-12-23
Isn't a command supposed to run at startup, when put inside /etc/rc.local?

I put a command in /etc/rc.local, but it does not run at system start. However, it works fine if I run /etc/rc.local in the terminal manually.

My /etc/rc.local file:
> user@userpc:$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/bin/vncserver -geometry 800x600 -depth 24 -httpport 8002 :1    #Start VNC 12/23/2007

exit 0

I have /etc/rc.local in system startup:
> user@userpc:$ ls /etc/rc2.d
K08vmware                    S20apport         S50ntp
README                          S20hotkey-setup   S89anacron
S05vbesave                   S20makedev        S89atd
S10acpid                        S20nvidia-kernel  S89cron
S10powernowd.early    S20powernowd      S90binfmt-support
S10sysklogd                  S20privoxy        S90vmware
S10xserver-xorg-input-wacom     S20rsync          S98usplash
S11klogd                     S20samba          S99acpi-support
S12dbus                      S20tor            S99laptop-mode
S12hal                       S20xinetd         [COLOR="RoyalBlue"]S99rc.local[/COLOR]
S13gdm                       S22consolekit     S99rmnologin
S18portmap                   S24avahi-daemon   S99stop-readahead
S19cupsys                    S24dhcdbd
S20apmd                      S25bluetooth
user@userpc:/$ 

---

### Post by seventynine on 2007-12-30
Note to self or anyone who stumbles on it: found a solution:

> su username -c "/usr/bin/vncserver -geometry 800x600 -depth 24 -httpport 8002 :1"

---

