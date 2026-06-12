---
title: "[SOLVED] Help please!! xfce desktop is booting blank suddenly"
date: 2008-10-31
forum: Desktop Environments
---

### Post by perixx on 2008-10-31
I'm having big troubles with Xubuntu 8.04: 

it will boot to the desktop, but the screen stays just blank & blue - no icons, no taskbar, no context menu, just the (movable) mouse coursor!


Right before, I've installed the following updates:

```
xserver-xorg-video-intel(2:2.2.1-1ubuntu13.7) << from 13.6
apt (0.7.9ubuntu17.1) 
apt-utils (0.7.9ubuntu17.1) << from 17
``` 

Played a flashgame (somethingamiss) meanwhile and rebooted afterwards, then the system wouldn't boot up anymore.


When trying to log into a failsave gnome-session, I get 'gnome not found', which is maybe correct, since I'm using XFCE.
Things I tried to get this fixed so far:
> - sudo dpkg -phigh xserver-xorg
- sudo dpkg xserver-xorg
- removal of Ati fglrx driver via Envy in graph. terminal session 
- re-installation of xserver-xorg and all respective packages, via graphical terminal session/Synaptic
- re-installation of Ati via Envy on cli

What can I do now?


perixx

---

### Post by mali2297 on 2008-10-31
Go to a console with Ctrl+Alt+F1. Then type
```

sudo /etc/init.d/gdm stop
startxfce4

```
If you again come to a blank blue screen, switch back to the console with Ctrl+Alt+F1 and check if there are any error messages printed.

---

### Post by perixx on 2008-10-31
Hello mali2297!


I've tried what you said and got a plain grey X server pane. The error messages in the virtual terminal were:

> .
.
cailwriteATIRegister (60ec,100) = 100
unblank CRTC 0 success

**(nm-applet:4889): WARNING**: <WARN> 
nma_dbus_init(): could not acquire_service():
dbus_bu_acquire_service(): 'Connection "1.96" is not allowed for the service "org.freedesktop.NetworkManagerInfo" due to security policies in configuration file
.
.
CTRL+C >> BREAK

waiting for X server to shut down gnome-screensaver: Fatal IO error 11 (Resource temporarily not availible) on X server: 0.0

nm-applet: "      "              "          "

FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing

xinit: unexpected signal 2.... stands for endless repeating.

At the moment, I can only boot into blank screen, CTRL+ALT+BKSP escape into gdm-login screen and start a failsave terminal session (graphical).
Here I can run 'xfdesktop' > thunar > terminal > firefox ...
even more, but all windows are fixed without decoration and cover each other, so it makes no sense....

From what I can judge, gdm is working fine, while something during the xserver-initialization is broken. Btw., using 'vesa' instead of 'fglrx' for alternative video driver doesn't help anything!

I even removed 'clamav' and 'compiz' (which were dwelling on my system for quite some time now), for I thought I had read some error msg. about them during shutdown. No workie.

This time I'm really lost!


P.S.: this is the msg. I got when logging into terminal session via gdm previously (/var/crash/xorg-driver-fglrx.0.crash / .xsession-errors) -
> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=de_DE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-nKkDvt6536/agent.6536

** (update-notifier:6695): WARNING **: already running?


** (orage:6689): WARNING **: Default timezone set to floating. Do not use timezones when setting appointments, it does not make sense without proper local timezone.
** Message: Orage **: Benachrichtigungsliste: 0 Benachrichtigungen hinzugefÃ¼gt. 0 Ereignisse bearbeitet.
** Message: Orage **: 	0 Benachrichtigungen, von denen 0 aktiv sind, gefunden (0 wiederkehrende Benachrichtigungen wurden durchsucht).
x-session-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Thunar: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce-mcs-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.


perixx

---

### Post by perixx on 2008-10-31
Err...

omfg, what's this..?

/var/log/gdm/:0.log shows the following...

> This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux xyz 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 31 23:54:54 2008
(==) Using config file: "/etc/X11/xorg.conf"
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
NTSC NTSC-J PAL PAL-M 
CailReadATIRegister(7a04) = 0
CailReadATIRegister(7a5c) = 0
CailReadATIRegister(7a54) = 50f02

Is my X server totally outdated?? How come my Radeon Device isn't right... hm, perhaps because I tried to fiddle around with 'xfailsavedialog' meanwhile... darn.

perixx

---

### Post by perixx on 2008-10-31
hmm... perhaps I've found something helpful in /var/log/auth.log:

> xxxxx gdm[7941]: pam_unix(gdm-autologin:session): session closed for user xxxxx
Oct 31 23:19:37 xxxxx gdm[10471]: PAM unable to dlopen(/lib/security/pam_gnome_keyring.so)
Oct 31 23:19:37 xxxxx gdm[10471]: PAM [error: /lib/security/pam_gnome_keyring.so: cannot open shared object file: No such file or directory]
Oct 31 23:19:37 xxxxx gdm[10471]: PAM adding faulty module: /lib/security/pam_gnome_keyring.so
Oct 31 23:20:06 xxxxx gdm[10471]: pam_unix(gdm:session): session opened for user xxxxx by (uid=0)
looks like this is where the login procedure hands over to the X server, but can't get some vital encryption key?


found also the 'vault' between working and non-working status, after the update (/var/log/dpkg.log):

> 2008-10-31 17:24:13 startup archives unpack
2008-10-31 17:24:20 upgrade apt 0.7.9ubuntu17 0.7.9ubuntu17.1
2008-10-31 17:24:20 status half-configured apt 0.7.9ubuntu17
2008-10-31 17:24:20 status unpacked apt 0.7.9ubuntu17
2008-10-31 17:24:20 status half-installed apt 0.7.9ubuntu17
2008-10-31 17:24:21 status half-installed apt 0.7.9ubuntu17
2008-10-31 17:24:21 status unpacked apt 0.7.9ubuntu17.1
2008-10-31 17:24:21 status unpacked apt 0.7.9ubuntu17.1
2008-10-31 17:24:21 startup packages configure
2008-10-31 17:24:21 configure apt 0.7.9ubuntu17.1 0.7.9ubuntu17.1
.
.
10-31 17:24:24 status installed xserver-xorg-video-intel 2:2.2.1-1ubuntu13.7
2008-10-31 17:24:24 trigproc libc6 2.7-10ubuntu4 2.7-10ubuntu4
2008-10-31 17:24:24 status half-configured libc6 2.7-10ubuntu4
2008-10-31 17:24:24 status installed libc6 2.7-10ubuntu4
2008-10-31 21:01:21 startup packages purge
2008-10-31 21:01:21 status installed fglrx-amdcccle 2:8.522-0ubuntu1
2008-10-31 21:01:28 remove fglrx-amdcccle 2:8.522-0ubuntu1 2:8.522-0ubuntu1


/var/log/messages.0:
> [ 1322.428766] Inbound IN=ppp0 OUT= MAC= SRC=88.67.38.242 DST=88.67.14.41 LEN=52 TOS=0x00 PREC=0x00 TTL=61 ID=28796 DF PROTO=TCP SPT=20266 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
Oct 27 18:21:28 xxxxx kernel: [ 1339.028231] npviewer.bin[8790]: segfault at f5b3e030 rip f7932540 rsp ff8d43fc error 4
Oct 27 18:21:43 xxxxx kernel: [ 1351.030738] npviewer.bin[8839]: segfault at f5b03030 rip f78f7540 rsp ffc0270c error 4
Oct 27 18:22:18 xxxxx kernel: [ 1369.790746] npviewer.bin[8855]: segfault at f5abe030 rip f78b2540 rsp fff53b0c error 4
Oct 27 18:23:58 xxxxx kernel: [ 1430.206952] Inbound IN=ppp0 OUT= MAC= SRC=88.67.54.197 DST=88.67.14.41 LEN=52 TOS=0x00 PREC=0x00 TTL=62 ID=12245 DF PROTO=TCP SPT=14182 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
Oct 27 18:27:07 xxxxx kernel: [ 1527.113057] Inbound IN=ppp0 OUT= MAC= SRC=88.67.38.242 DST=88.67.14.41 LEN=52 TOS=0x00 PREC=0x00 TTL=61 ID=6163 DF PROTO=TCP SPT=38093 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
Oct 27 18:28:08 xxxxx kernel: [ 1557.573695] Inbound IN=ppp0 OUT= MAC= SRC=88.67.38.242 DST=88.67.14.41 LEN=52 TOS=0x00 PREC=0x00 TTL=61 ID=11568 DF PROTO=TCP SPT=41024 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
Oct 27 18:28:30 xxxxx kernel: [ 1569.124833] npviewer.bin[8895]: segfault at f5b4a030 rip f793e540 rsp ffd270ec error 4
Oct 27 18:30:00 xxxxx kernel: [ 1623.105359] npviewer.bin[8947]: segfault at 2033303a rip 2033303a rsp ffa6c3cc error 14
Oct 27 18:30:45 xxxxx kernel: [ 1655.235365] npviewer.bin[8996]: segfault at 2033303a rip 2033303a rsp ffda5f0c error 14




/var/log/syslog.0:
> Oct 31 16:43:36 xxxxx NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 31 16:43:36 xxxxx NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct 31 16:44:27 xxxxx kernel: [  201.942941] npviewer.bin[9393]: segfault at f5b57030 rip f794b540 rsp ff900cbc error 4


perixx

---

### Post by mali2297 on 2008-11-01
> **perixx said:**
> Err...

omfg, what's this..?

/var/log/gdm/:0.log shows the following...


Is my X server totally outdated?? How come my Radeon Device isn't right... hm, perhaps because I tried to fiddle around with 'xfailsavedialog' meanwhile... darn.

perixx

Post the content of /etc/X11/xorg.conf.

Also, remove the folder ~/.cache and move the Xfce settings in ~/.config to some backup location, and then try starting Xfce.

---

### Post by perixx on 2008-11-01
> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
This is my current xorg.conf's content. But the settings here can't be responsible for the (same) symptom than I had with my initial xorg.conf setup, which always worked fine.

perixx

---

### Post by perixx on 2008-11-01
HEUREKA!!

I've reverted to my xorg.conf's backup and deleted the ~/.cache folder, like you've told me - everything is up and running again, it was really that easy! I already thought about re-installing...

Thanks very much, mali2297!!!

perixx

---

