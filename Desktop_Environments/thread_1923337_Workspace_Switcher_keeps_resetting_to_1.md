---
title: "Workspace Switcher keeps resetting to 1"
date: 2012-02-10
forum: Desktop Environments
---

### Post by azurehoney on 2012-02-10
Any idea what might cause number of workspaces resetting to 1?
It happens every time I log in.

Using Xubuntu Oneiric Ocelot.

---

### Post by Toz on 2012-02-10
Does this mean that you can change the number of workspaces after you login? If so, check the permissions of ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml.

It can also possibly be a problem with the window manager. Are you running compwiz? If not, make sure that the xfwm4 window manager is running. Enter the following command in the terminal window to see if xfwm4 is running:
```
ps -ef | grep xfwm4 | grep -v grep
```

If not, try Alt+F2 then:
```
xfwm4 --replace
```

---

### Post by azurehoney on 2012-02-11
> **Toz said:**
> Does this mean that you can change the number of workspaces after you login? If so, check the permissions of ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml.
Yes I can change the number of workspaces after I log in and permissions via right-click show that I am allowed to read and write to this file.

> It can also possibly be a problem with the window manager. Are you running compwiz? If not, make sure that the xfwm4 window manager is running. Enter the following command in the terminal window to see if xfwm4 is running:
```
ps -ef | grep xfwm4 | grep -v grep
```If not, try Alt+F2 then:
```
xfwm4 --replace
```I am not running compiz
[FONT=Courier New]fakename 11749     1  0 18:19 ?        00:00:01 xfwm4[/FONT]

---

### Post by Toz on 2012-02-11
What does the following return?
```
cat ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml | grep workspace
```

Are you having problems logging out? I'm wondering if something is happening thats preventing the system from writing changes to that file. If you have a ~/.xsession-errors.old file, can you post it back? If not, logout, go to a virtual terminal (Ctrl+Alt+F1), login via the text prompt, rename the existing ~/.xsession-errors file to ~/.xsession-errors.BAK, go back to the GUI (Ctrl+Alt+F7), login again and post back that file.

Another thing to try would be to directly edit ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml while not logged in graphically (from tty1) and change the line: > <property name="workspace_count" type="int" value="1"/>
...to read:
```
<property name="workspace_count" type="int" value="4"/>
```
...then login to the GUI and see if you've got 4 workspaces.

---

### Post by azurehoney on 2012-02-12
> **Toz said:**
> What does the following return?
```
cat ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml | grep workspace
```
```
    <property name="workspace_count" type="int" value="2"/>
    <property name="workspace_names" type="empty"/>
    <property name="wrap_workspaces" type="empty"/>
    <property name="cycle_workspaces" type="bool" value="false"/>
    <property name="scroll_workspaces" type="bool" value="true"/>
    <property name="toggle_workspaces" type="bool" value="false"/>
```> 
Are you having problems logging out?no, I don't notice anything unusual

> I'm wondering if something is happening thats preventing the system from writing changes to that file. If you have a ~/.xsession-errors.old file, can you post it back? If not, logout, go to a virtual terminal (Ctrl+Alt+F1), login via the text prompt, rename the existing ~/.xsession-errors file to ~/.xsession-errors.BAK, go back to the GUI (Ctrl+Alt+F7), login again and post back that file.no .old file, but [here is my xsession-errors]("http://pastebin.com/1jexA4ta")

> Another thing to try would be to directly edit ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml while not logged in graphically (from tty1) and change the line:
...to read:
```
<property name="workspace_count" type="int" value="4"/>
```...then login to the GUI and see if you've got 4 workspaces.this helps, I now have 4 workspaces

---

### Post by Toz on 2012-02-12
According to your .xsession-errors file, it looks like xfce is crashing on logout:
> xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
...
xfce4-settings-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
The application 'xfce4-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

You also seem to have some kde stuff going on:
> dolphin(19921)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(19921)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(19921)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(19921)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(19921)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(19921)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kdeinit4: Fatal IO error: client killed
klauncher: Exiting on signal 15
kdeinit4: kded4 [kdeinit]: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

Not quite sure what the problem is, but I'm willing to be that on logout/shutdown, when xfce is supposed to save its settings, its crashing, preventing the settings from being saved. It might have something to do with the kde things that have been installed.

Other than the workspaces issue, have you noticed any other problems with xfce?

---

### Post by azurehoney on 2012-02-13
> **azurehoney said:**
> 
this helps, I now have 4 workspaces

Not anymore, workspaces have reset to 1 again.

> **Toz said:**
> 
Other than the workspaces issue, have you noticed any other problems with xfce?

No, I haven't noticed anything else.

---

### Post by Toz on 2012-02-13
Can you post back the results of:
```
ps -ef
```
...right after you login (to keep the list as small as possible) so that we can see what processes are running? Something is crashing your xfce on logout.

Was this a straight Xubuntu install or did you upgrade from another version of ubuntu (kubuntu?)? Are you running and other kde apps other than dolphin?

---

### Post by azurehoney on 2012-02-19
```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 10:39 ?        00:00:00 /sbin/init
root         2     0  0 10:39 ?        00:00:00 [kthreadd]
root         3     2  0 10:39 ?        00:00:03 [ksoftirqd/0]
root         6     2  0 10:39 ?        00:00:00 [migration/0]
root         7     2  0 10:39 ?        00:00:00 [cpuset]
root         8     2  0 10:39 ?        00:00:00 [khelper]
root         9     2  0 10:39 ?        00:00:00 [netns]
root        10     2  0 10:39 ?        00:00:00 [sync_supers]
root        11     2  0 10:39 ?        00:00:00 [bdi-default]
root        12     2  0 10:39 ?        00:00:00 [kintegrityd]
root        13     2  0 10:39 ?        00:00:00 [kblockd]
root        14     2  0 10:39 ?        00:00:00 [ata_sff]
root        15     2  0 10:39 ?        00:00:00 [khubd]
root        16     2  0 10:39 ?        00:00:00 [md]
root        37     2  0 10:39 ?        00:00:00 [khungtaskd]
root        38     2  0 10:39 ?        00:00:00 [kswapd0]
root        39     2  0 10:39 ?        00:00:00 [ksmd]
root        40     2  0 10:39 ?        00:00:00 [khugepaged]
root        41     2  0 10:39 ?        00:00:00 [fsnotify_mark]
root        42     2  0 10:39 ?        00:00:00 [ecryptfs-kthrea]
root        43     2  0 10:39 ?        00:00:00 [crypto]
root        51     2  0 10:39 ?        00:00:00 [kthrotld]
root       247     2  0 10:39 ?        00:00:00 [scsi_eh_0]
root       248     2  0 10:39 ?        00:00:00 [scsi_eh_1]
root       250     2  0 10:39 ?        00:00:00 [kworker/u:2]
root       251     2  0 10:39 ?        00:00:00 [scsi_eh_2]
root       252     2  0 10:39 ?        00:00:00 [scsi_eh_3]
root       253     2  0 10:39 ?        00:00:00 [kworker/u:3]
root       284     2  0 10:39 ?        00:00:00 [jbd2/sda1-8]
root       285     2  0 10:39 ?        00:00:00 [ext4-dio-unwrit]
root       336     1  0 10:39 ?        00:00:00 upstart-udev-bridge --daemon
root       343     1  0 10:39 ?        00:00:00 udevd --daemon
root       508   343  0 10:39 ?        00:00:00 udevd --daemon
root       509   343  0 10:39 ?        00:00:00 udevd --daemon
root       538     2  0 10:39 ?        00:00:00 [jbd2/sda3-8]
root       540     2  0 10:39 ?        00:00:00 [ext4-dio-unwrit]
root       696     2  0 10:39 ?        00:00:00 [edac-poller]
syslog     712     1  0 10:39 ?        00:00:01 rsyslogd -c5
103        716     1  0 10:39 ?        00:00:04 dbus-daemon --system --fork --ac
root       724     1  0 10:39 ?        00:00:00 /usr/sbin/modem-manager
root       726     1  0 10:39 ?        00:00:00 NetworkManager
avahi      729     1  0 10:39 ?        00:00:00 avahi-daemon: running [ylle-M61S
avahi      730   729  0 10:39 ?        00:00:00 avahi-daemon: chroot helper
root       740     1  0 10:39 ?        00:00:00 /usr/lib/policykit-1/polkitd
root       759     2  0 10:39 ?        00:00:00 [kpsmoused]
root       796   726  0 10:39 ?        00:00:00 /sbin/dhclient -d -4 -sf /usr/li
root       890     1  0 10:39 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       895     1  0 10:39 tty5     00:00:00 /sbin/getty -8 38400 tty5
root       906     1  0 10:39 tty2     00:00:00 /sbin/getty -8 38400 tty2
root       907     1  0 10:39 tty3     00:00:00 /sbin/getty -8 38400 tty3
root       911     1  0 10:39 tty6     00:00:00 /sbin/getty -8 38400 tty6
root       921     1  0 10:39 ?        00:00:00 acpid -c /etc/acpi/events -s /va
root       924     1  0 10:39 ?        00:00:00 cron
daemon     925     1  0 10:39 ?        00:00:00 atd
root       987     2  0 10:39 ?        00:00:00 [hd-audio0]
root      1008     1  0 10:39 ?        00:00:00 /usr/sbin/bluetoothd
root      1017     2  0 10:39 ?        00:00:00 [l2cap]
root      1021     2  0 10:39 ?        00:00:00 [krfcommd]
root      1028     1  0 10:39 ?        00:00:00 upstart-socket-bridge --daemon
root      1188     2  0 10:39 ?        00:00:00 [flush-8:0]
root      1237     1  0 10:39 tty1     00:00:00 /sbin/getty -8 38400 tty1
root      1242     2  0 10:39 ?        00:00:00 [hd-audio1]
root      1294     1  0 10:39 ?        00:00:00 /usr/sbin/cupsd -F
root      1298     1  0 10:39 ?        00:00:00 gdm-binary
root      1318     1  0 10:39 ?        00:00:00 /usr/sbin/console-kit-daemon --n
root      1409     1  0 10:39 ?        00:00:00 /usr/lib/upower/upowerd
colord    1462     1  0 10:39 ?        00:00:00 /usr/lib/x86_64-linux-gnu/colord
rtkit     1473     1  0 10:39 ?        00:00:00 /usr/lib/rtkit/rtkit-daemon
root      1479     1  0 10:39 ?        00:00:00 /usr/lib/accountsservice/account
root      1912     1  0 10:47 ?        00:00:00 /usr/lib/udisks/udisks-daemon
root      1913  1912  0 10:47 ?        00:00:01 udisks-daemon: polling /dev/sr0
root      4066     2  0 12:48 ?        00:00:02 [kworker/0:1]
root      4183     2  0 13:13 ?        00:00:00 [kworker/0:0]
root      4188     2  0 13:18 ?        00:00:00 [kworker/0:2]
fakename  4342     1  0 13:23 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
fakename  4465     1  0 13:23 ?        00:00:00 /usr/bin/pulseaudio --start --lo
root      4506     2  0 13:23 ?        00:00:00 [flush-ecryptfs-]
fakename  4590     1  0 13:23 ?        00:00:00 pcscd --auto-exit
root      4624  1298  0 13:24 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --
root      4626  4624  4 13:24 tty8     00:00:01 /usr/bin/Xorg :0 -br -verbose -a
root      4670  4624  0 13:24 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
fakename  4679     1  0 13:24 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
fakename  4684     1  0 13:24 ?        00:00:00 /usr/bin/gnome-keyring-daemon --
fakename  4701  4670  0 13:24 ?        00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -
fakename  4736  4701  0 13:24 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus
fakename  4739     1  0 13:24 ?        00:00:00 /usr/bin/dbus-launch --exit-with
fakename  4740     1  2 13:24 ?        00:00:00 //bin/dbus-daemon --fork --print
fakename  4748     1  0 13:24 ?        00:00:00 /usr/lib/xfce4/xfconf/xfconfd
fakename  4754  4701  0 13:24 ?        00:00:00 xscreensaver -no-splash
fakename  4756  4701  0 13:24 ?        00:00:00 xfce4-session
fakename  4761  4756  0 13:24 ?        00:00:00 xfwm4 --display :0.0 --sm-client
fakename  4763     1  0 13:24 ?        00:00:00 xfsettingsd --force
fakename  4764  4756  0 13:24 ?        00:00:00 Thunar --sm-client-id 252633cff-
fakename  4766     1  0 13:24 ?        00:00:00 /usr/lib/gvfs/gvfsd
fakename  4769  4756  7 13:24 ?        00:00:01 xfce4-panel --display :0.0 --sm-
fakename  4773  4756  4 13:24 ?        00:00:00 xfdesktop --display :0.0 --sm-cl
fakename  4776     1  0 13:24 ?        00:00:00 xfce4-power-manager --restart --
fakename  4779     1  0 13:24 ?        00:00:00 xfce4-settings-helper --display
fakename  4784  4769  0 13:24 ?        00:00:00 /usr/lib/xfce4/panel/wrapper /us
fakename  4791  4769  1 13:24 ?        00:00:00 /usr/lib/xfce4-indicator-plugin/
fakename  4797     1  1 13:24 ?        00:00:00 nm-applet
fakename  4803     1  1 13:24 ?        00:00:00 bluetooth-applet
fakename  4808     1  0 13:24 ?        00:00:00 /usr/lib/policykit-1-gnome/polki
fakename  4811  4769  1 13:24 ?        00:00:00 /usr/lib/xfce4/panel/wrapper /us
fakename  4813     1  1 13:24 ?        00:00:00 /usr/bin/python /usr/share/syste
fakename  4818     1  0 13:24 ?        00:00:00 update-notifier
fakename  4820     1  3 13:24 ?        00:00:00 /usr/bin/python /usr/bin/blueman
fakename  4822     1  0 13:24 ?        00:00:00 xfce4-volumed
fakename  4825     1  0 13:24 ?        00:00:00 /usr/lib/xfce4/notifyd/xfce4-not
fakename  4841  4769  1 13:24 ?        00:00:00 /usr/lib/xfce4/panel/wrapper /us
fakename  4845     1  0 13:24 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2
fakename  4851     1  0 13:24 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spaw
fakename  4856     1  0 13:24 ?        00:00:00 /usr/lib/indicator-sound/indicat
fakename  4860     1  0 13:24 ?        00:00:00 /usr/lib/indicator-application/i
fakename  4864     1  0 13:24 ?        00:00:00 /usr/lib/indicator-messages/indi
fakename  4870     1  0 13:24 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-mo
root      4878     2  0 13:24 ?        00:00:00 [flush-ecryptfs-]
fakename  4880     1  0 13:24 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-mo
fakename  4883     1  0 13:24 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volum
fakename  4889     1  0 13:24 ?        00:00:00 /usr/bin/obex-data-server --no-d
root      4892     1  1 13:24 ?        00:00:00 /usr/bin/python /usr/lib/blueman
fakename  4909     1  1 13:24 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/
fakename  4910  4909 18 13:24 ?        00:00:00 xfce4-terminal
fakename  4911  4910  0 13:24 ?        00:00:00 [xfce4-terminal] <defunct>
fakename  4912  4910 12 13:24 pts/0    00:00:00 bash
fakename  4968  4912  0 13:24 pts/0    00:00:00 ps -ef


```

---

### Post by Toz on 2012-02-19
I notice a couple of things:

1. You don't have any kde libraries/services running on login (they must start when you run dolphin)
What happens when you login, immediately change desktop number and again immediately logout? As in post #4, save a copy of ~/.xession-errors from TTY1 and log back in. Is workspace number preserved? Post back contents of saved ~/.xsession-errors file.

2. You seem to be using gdm as desktop manager (instead if default lightdm)
Did you make a change to gdm instead of lightdm?

---

### Post by azurehoney on 2012-02-19
I am not sure why, but the problem has disappeared now.
> **Toz said:**
> I notice a couple of things:

1. You don't have any kde libraries/services running on login (they must start when you run dolphin)
What happens when you login, immediately change desktop number and again immediately logout?
[http://pastebin.com/dFfVA7VD](http://pastebin.com/dFfVA7VD)
> **Toz said:**
> 2. You seem to be using gdm as desktop manager (instead if default lightdm)
Did you make a change to gdm instead of lightdm?
Yes, lightdm buttons don't react to mouse clicks last time I tried to use it.

---

### Post by Toz on 2012-02-19
> **azurehoney said:**
> I am not sure why, but the problem has disappeared now.

Although good to hear, your log file is still showing crashes:
> xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
blueman-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
 
(bluetooth-applet:10056): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
 
 
(nm-applet:10052): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

You might be suffering from this bug: [https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/787934]("https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/787934"). You might want to add yourself to that list.

---

