---
title: "Getting &quot;dpkg --configure -a&quot; message"
date: 2009-01-25
forum: General Help
---

### Post by armaguy on 2009-01-25
SOLVED: See last post for a quick solution, but warning: it may not apply to you (change the culprit packages name) or not work at all (totally different workaround).

Yes, I know this is a know issue, but...

First, the error I'm getting. When trying to update using the Update Manager, here is what I get:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

After reading other threads about this, I found out that this problem is solved by a case by case approach, and it's either because apt-get was interrupted (power loss during download?) or there was a problem with a repository or a package, hence why I believe the problem is solved differently each time. For now it won't let me update (Update Manager) or use apt-get (same thing mostly) or anything else, and this makes me sad :( boo.

Onwards with syptoms:
If I do "sudo dpkg --configure -a", as suggested, I get:
```
toor@ubuntu:~$ sudo dpkg --configure -a
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
toor@ubuntu:~$
```

"Aborted" :(

Typing also "sudo apt-get upgrade" or "sudo apt-get update" after or before, as suggested in some post won't solve either.

Here's sudo apt-get upgrade's output:
```
toor@ubuntu:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
toor@ubuntu:~$
```

And here's sudo apt-get update's output:
```
toor@ubuntu:~$ sudo apt-get update
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid Release.gpg
Ign http://ca.archive.ubuntu.com intrepid/main Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid-updates Release.gpg
Hit http://ca.archive.ubuntu.com intrepid-updates/main Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid-updates/restricted Translation-en_CA
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_CA
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_CA
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com intrepid-security Release
Ign http://ca.archive.ubuntu.com intrepid-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid-updates/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid Release
Hit http://ca.archive.ubuntu.com intrepid-updates Release
Hit http://security.ubuntu.com intrepid-security/main Packages      
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://ca.archive.ubuntu.com intrepid/main Packages
Hit http://ca.archive.ubuntu.com intrepid/restricted Packages
Hit http://ca.archive.ubuntu.com intrepid/main Sources
Hit http://ca.archive.ubuntu.com intrepid/restricted Sources
Hit http://ca.archive.ubuntu.com intrepid/universe Packages
Hit http://ca.archive.ubuntu.com intrepid/universe Sources
Hit http://ca.archive.ubuntu.com intrepid/multiverse Packages
Hit http://ca.archive.ubuntu.com intrepid/multiverse Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/main Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/main Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/multiverse Sources
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
toor@ubuntu:~$ 
```

Yea, so I'm kinda in a loop heh? :P
Thanks to anyone who can help me figure out what's causing the problem! ^_^ You get :popcorn: if you solve :D
It's kinda my first step with ubuntu/linux at all and... HELL the terminal is FUN!

---

### Post by dcstar on 2009-01-25
> **armaguy said:**
> 
.........
Thanks to anyone who can help me figure out what's causing the problem! ^_^ You get :popcorn: if you solve :D
It's kinda my first step with ubuntu/linux at all and... HELL the terminal is FUN!

Remove any package giving an error with:

```
sudo apt-get remove package-name
sudo dpkg --configure -a
```

Then reinstall with:

```
sudo apt-get install package-name
```

---

### Post by armaguy on 2009-01-25
Thanks for the quick answer.

I understand, from the logs I provided above, than a package might cause trouble from here:
```
...
dpkg: error processing system-tools-backends (--configure):
...
```

I am guessing that 'system-tools-backends' is the cause of the problem, and so I will do as you said:
```
sudo apt-get remove system-tools-backends
sudo dpkg --configure -a
```

(The 'package-name' was to be replaced with the said packaged causing error, right?')
Thank you, will post as solved as soon as it is so!

EDIT:
WAIT, system-tools-backend seems to me like an important thing, am I right? I don't know the name of stuff and so far I've only been doing what I've been told, but this looks risky, to remove this package. Can I have confirmation?

reedit:
Oh well I'm a jackass and tried it anyway.

---

### Post by armaguy on 2009-01-25
After trying 'sudo apt-get remove system-tools-backends' I have been returned the same error:

```
toor@ubuntu:~$ sudo apt-get remove system-tools-backends
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
toor@ubuntu:~$ sudo dpkg --configure -a
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                        invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
toor@ubuntu:~$ 

```

---

### Post by Shazaam on 2009-01-25
Try this...
```
sudo apt-get install -f
```
Basically the same as choosing "Fix broken packages" in Synaptic.

---

### Post by armaguy on 2009-01-25
Same error:

```
toor@ubuntu:~$ sudo apt-get install -f
[sudo] password for toor: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
toor@ubuntu:~$
```

---

### Post by Ayuthia on 2009-01-25
Have you tried to stop system-tools-backend:
```
sudo /etc/init.d/system-tools-backend stop
sudo dpkg --configure -a
```
It looks like the system is having problems starting the system-tools-backend so it might already be running.

---

### Post by armaguy on 2009-01-25
Worked! Partly...

toor@ubuntu:~$ sudo /etc/init.d/system-tools-backends stop
 * Stopping System Tools Backends system-tools-backends                 [ OK ] 
toor@ubuntu:~$ sudo dpkg --configure -a
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Reloading system message bus config...                               [ OK ] 
 * Starting System Tools Backends system-tools-backends                 [ OK ] 

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
toor@ubuntu:~$

---

### Post by Ayuthia on 2009-01-25
You might try the steps in this link:
[http://techxplorer.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/](http://techxplorer.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/)

---

### Post by armaguy on 2009-01-26
According to this link, which provided some understanding help, typing the suggested command will list all problematic packages.
So I did, and the output was quite big. Does that mean that all the packages listed are not working correctly? If not, there seems to be a 2 letter code on the left column showing some kind of status, apparently 'ii' means working correctly (which is not being listed). I tried man dpkg to know what the other 2 letters code meant (iU, iW, rc) but no good.

Thanks for the link! I believe I'm close to a solution.

Here's 'sudo dpkg -l | grep -v ^ii' output:

```
toor@ubuntu:~$ sudo dpkg -l | grep -v ^ii
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                      Version                                 Description
+++-=========================================-=======================================-============================================
iU  cups                                      1.3.9-2ubuntu6.1                        Common UNIX Printing System(tm) - server
iU  cups-bsd                                  1.3.9-2ubuntu6.1                        Common UNIX Printing System(tm) - BSD comman
iW  cups-client                               1.3.9-2ubuntu6.1                        Common UNIX Printing System(tm) - client pro
iW  evolution                                 2.24.2-0ubuntu1                         groupware suite with mail client and organiz
iU  evolution-exchange                        2.24.2-0ubuntu1                         Exchange plugin for the Evolution groupware 
iU  evolution-plugins                         2.24.2-0ubuntu1                         standard plugins for Evolution
iW  f-spot                                    0.5.0.3-0ubuntu4                        personal photo management application
iU  gedit                                     2.24.2-0ubuntu1                         official text editor of the GNOME desktop en
iW  gedit-common                              2.24.2-0ubuntu1                         official text editor of the GNOME desktop en
iW  ghostscript                               8.63.dfsg.1-0ubuntu6.1                  The GPL Ghostscript PostScript/PDF interpret
iU  ghostscript-x                             8.63.dfsg.1-0ubuntu6.1                  The GPL Ghostscript PostScript/PDF interpret
iW  gnome-games                               1:2.24.1.1-0ubuntu1                     games for the GNOME desktop
iW  gnome-panel                               1:2.24.1-0ubuntu2.1                     launcher and docking facility for GNOME
iW  gnome-pilot                               2.0.15-2ubuntu4                         A GNOME applet for management of your Palm P
iW  gnome-power-manager                       2.24.0-0ubuntu8.1                       frontend for gnome-powermanager
iW  gnome-terminal                            2.24.1.1-0ubuntu1                       The GNOME 2 terminal emulator application
iU  libdeskbar-tracker                        0.6.6-1ubuntu5.1                        metadata database, indexer and search tool -
iW  libsmbclient                              2:3.2.3-1ubuntu3.4                      shared library that allows applications to t
iW  libsnmp-base                              5.4.1~dfsg-7.1ubuntu6.1                 SNMP (Simple Network Management Protocol) MI
iU  libsnmp15                                 5.4.1~dfsg-7.1ubuntu6.1                 SNMP (Simple Network Management Protocol) li
iW  libxml2-utils                             2.6.32.dfsg-4ubuntu1.1                  XML utilities
rc  myspell-en-us                             1:2.4.0-2ubuntu4                        English_american dictionary for myspell
iW  network-manager                           0.7~~svn20081018t105859-0ubuntu1.8.10.1 network management framework daemon
iU  network-manager-gnome                     0.7~~svn20081020t000444-0ubuntu1.8.10.1 network management framework (GNOME frontend
iW  ntpdate                                   1:4.2.4p4+dfsg-6ubuntu2.2               client for setting system time from NTP serv
iW  pm-utils                                  1.1.2.4-1ubuntu8                        utilities and scripts for power management
iW  poppler-utils                             0.8.7-1ubuntu0.1                        PDF utilitites (based on libpoppler)
iW  pulseaudio                                0.9.10-2ubuntu9.2                       PulseAudio sound server
iW  pulseaudio-esound-compat                  0.9.10-2ubuntu9.2                       PulseAudio ESD compatibility layer
iU  pulseaudio-module-x11                     0.9.10-2ubuntu9.2                       X11 module for PulseAudio sound server
iW  pulseaudio-utils                          0.9.10-2ubuntu9.2                       Command line tools for the PulseAudio sound 
iW  rhythmbox                                 0.11.6svn20081008-0ubuntu4.2            music player and organizer for GNOME
iW  samba-common                              2:3.2.3-1ubuntu3.4                      Samba common files used by both the server a
iU  smbclient                                 2:3.2.3-1ubuntu3.4                      a LanManager-like simple client for Unix
iW  system-tools-backends                     2.6.0-1ubuntu1.1                        System Tools to manage computer configuratio
iU  totem                                     2.24.3-0ubuntu1                         A simple media player for the GNOME desktop 
iW  totem-common                              2.24.3-0ubuntu1                         Data files for the Totem media player
iU  totem-gstreamer                           2.24.3-0ubuntu1                         A simple media player for the GNOME desktop 
iU  totem-mozilla                             2.24.3-0ubuntu1                         Totem Mozilla plugin
iU  totem-plugins                             2.24.3-0ubuntu1                         Plugins for the Totem media player
iW  tracker                                   0.6.6-1ubuntu5.1                        metadata database, indexer and search tool
iU  tracker-search-tool                       0.6.6-1ubuntu5.1                        metadata database, indexer and search tool -
iU  tracker-utils                             0.6.6-1ubuntu5.1                        metadata database, indexer and search tool -
iW  transmission-gtk                          1.34-0ubuntu2.2                         free, lightweight BitTorrent client (graphic
iW  vinagre                                   2.24.1-0ubuntu1.1                       VNC client for the GNOME Desktop
rc  wifi-radar                                1.9.9-1.1                               graphical utility for managing Wi-Fi profile
iW  xserver-xorg-input-evdev                  1:2.0.99+git20080912-0ubuntu6           X.Org X server -- evdev input driver
iU  xserver-xorg-video-ati                    1:6.9.0+git20081003.f9826a56-0ubuntu2.1 X.Org X server -- ATI display driver wrapper
iW  xserver-xorg-video-intel                  2:2.4.1-1ubuntu10.1                     X.Org X server -- Intel i8xx, i9xx display d
iW  xserver-xorg-video-radeon                 1:6.9.0+git20081003.f9826a56-0ubuntu2.1 X.Org X server -- ATI Radeon display drtoor@ubuntu:~$ 

```

---

### Post by armaguy on 2009-01-26
Since earlier it was said that 'system-tools-backends' was causing a problem I went on to remove it (sudo dpkg --purge remove system-tools-backends).

Output:```

toor@ubuntu:~$ sudo dpkg --purge remove system-tools-backends
dpkg - warning: ignoring request to remove remove which isn't installed.
dpkg: dependency problems prevent removal of system-tools-backends:
 gnome-system-tools depends on system-tools-backends.
 liboobs-1-4 depends on system-tools-backends (>= 2.5.4).
dpkg: error processing system-tools-backends (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 system-tools-backends
toor@ubuntu:~$
```

This seems like a bad idea to remove this package, as I think the gnome-system-tools are important for my machine to work correctly (?). Perhaps I could force it to bypass dependency check?

Or am I just wrong with the package?

Thanks for still being helpful!

---

### Post by armaguy on 2009-01-26
Woahm I tried 'sudo apt-get install wifi-radar', as I purged it just before using the above link to detect it (it was listed as not containing 'ii') and purged it.

That produced a tons of things as well as plenty of crash report from ubuntu.
Here is it, I don't expect anyone to read it fully, just get the main idea:
```
toor@ubuntu:~$ sudo apt-get install wifi-radar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  wifi-radar
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
49 not fully installed or removed.
Need to get 0B/39.8kB of archives.
After this operation, 238kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package wifi-radar.
(Reading database ... 130860 files and directories currently installed.)
Unpacking wifi-radar (from .../wifi-radar_1.9.9-1.1_all.deb) ...
Processing triggers for man-db ...
dpkg: error processing poppler-utils (--configure):
 package poppler-utils is already installed and configured
dpkg: error processing ghostscript (--configure):
 package ghostscript is already installed and configured
Setting up cups (1.3.9-2ubuntu6.1) ...
Installing new version of config file /etc/apparmor.d/usr.sbin.cupsd ...
Reloading AppArmor profiles : done.
 * Starting Common Unix Printing System: cupsd                                                                        [ OK ] 

dpkg: error processing cups-client (--configure):
 package cups-client is already installed and configured
dpkg: error processing evolution (--configure):
 package evolution is already installed and configured
Setting up evolution-exchange (2.24.2-0ubuntu1) ...
No apport report written because MaxReports is reached already

Setting up evolution-plugins (2.24.2-0ubuntu1) ...
dpkg: error processing f-spot (--configure):
 package f-spot is already installed and configured
dpkg: error processing gedit-common (--configure):
 package gedit-common is already installed and configured
Setting up gedit (2.24.2-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            ^[	
Setting up ghostscript-x (8.63.dfsg.1-0ubuntu6.1) ...
dpkg: error processing gnome-games (--configure):
 package gnome-games is already installed and configured
No apport report written because MaxReports is reached already
                                                              dpkg: error processing gnome-panel (--configure):
 package gnome-panel is already installed and configured
No apport report written because MaxReports is reached already
                                                              dpkg: error processing gnome-power-manager (--configure):
 package gnome-power-manager is already installed and configured
No apport report written because MaxReports is reached already
                                                              dpkg: error processing gnome-terminal (--configure):
 package gnome-terminal is already installed and configured
No apport report written because MaxReports is reached already
                                                              dpkg: error processing tracker (--configure):
 package tracker is already installed and configured
No apport report written because MaxReports is reached already
                                                              Setting up libdeskbar-tracker (0.6.6-1ubuntu5.1) ...

dpkg: error processing libsmbclient (--configure):
 package libsmbclient is already installed and configured
dpkg: error processing libsnmp-base (--configure):
 package libsnmp-base is already installed and configured
Setting up libsnmp15 (5.4.1~dfsg-7.1ubuntu6.1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already

dpkg: error processing libxml2-utils (--configure):
 package libxml2-utils is already installed and configured
No apport report written because MaxReports is reached already
                                                              dpkg: error processing network-manager (--configure):
 package network-manager is already installed and configured
No apport report written because MaxReports is reached already
                                                              Setting up network-manager-gnome (0.7~~svn20081020t000444-0ubuntu1.8.10.1) ...
Installing new version of config file /etc/xdg/autostart/nm-applet.desktop ...

dpkg: error processing ntpdate (--configure):
 package ntpdate is already installed and configured
No apport report written because MaxReports is reached already
                                                              dpkg: error processing pm-utils (--configure):
 package pm-utils is already installed and configured
No apport report written because MaxReports is reached already
                                                              dpkg: error processing pulseaudio (--configure):
 package pulseaudio is already installed and configured
No apport report written because MaxReports is reached already
                                                              dpkg: error processing pulseaudio-esound-compat (--configure):
 package pulseaudio-esound-compat is already installed and configured
No apport report written because MaxReports is reached already
                                                              dpkg: error processing pulseaudio-utils (--configure):
 package pulseaudio-utils is already installed and configured
No apport report written because MaxReports is reached already
                                                              Setting up pulseaudio-module-x11 (0.9.10-2ubuntu9.2) ...
dpkg: error processing rhythmbox (--configure):
 package rhythmbox is already installed and configured
No apport report written because MaxReports is reached already
                                                              dpkg: error processing samba-common (--configure):
 package samba-common is already installed and configured
Setting up smbclient (2:3.2.3-1ubuntu3.4) ...
No apport report written because MaxReports is reached already
                                                              dpkg: error processing system-tools-backends (--configure):
 package system-tools-backends is already installed and configured
dpkg: error processing totem-common (--configure):
 package totem-common is already installed and configured
Setting up totem-gstreamer (2.24.3-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already

Setting up totem-plugins (2.24.3-0ubuntu1) ...

Setting up totem (2.24.3-0ubuntu1) ...
Setting up totem-mozilla (2.24.3-0ubuntu1) ...
Setting up tracker-search-tool (0.6.6-1ubuntu5.1) ...

Setting up tracker-utils (0.6.6-1ubuntu5.1) ...
dpkg: error processing transmission-gtk (--configure):
 package transmission-gtk is already installed and configured
dpkg: error processing vinagre (--configure):
 package vinagre is already installed and configured
dpkg: error processing xserver-xorg-input-evdev (--configure):
 package xserver-xorg-input-evdev is already installed and configured
dpkg: error processing xserver-xorg-video-radeon (--configure):
 package xserver-xorg-video-radeon is already installed and configured
Setting up xserver-xorg-video-ati (1:6.9.0+git20081003.f9826a56-0ubuntu2.1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                                                                                                           dpkg: error processing xserver-xorg-video-intel (--configure):
 package xserver-xorg-video-intel is already installed and configured
No apport report written because MaxReports is reached already
                                                              dpkg: error processing xterm (--configure):
 package xterm is not ready for configuration
 cannot configure (current status `triggers-awaited')
No apport report written because MaxReports is reached already
                                                              Setting up cups-bsd (1.3.9-2ubuntu6.1) ...

dpkg: error processing gnome-pilot (--configure):
 package gnome-pilot is already installed and configured
Setting up wifi-radar (1.9.9-1.1) ...
No apport report written because MaxReports is reached already
                                                               * Starting wifi-radar daemon...                               
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
^[[BErrors were encountered while processing:
 poppler-utils
 ghostscript
 cups-client
 evolution
 f-spot
 gedit-common
 gnome-games
 gnome-panel
 gnome-power-manager
 gnome-terminal
 tracker
 libsmbclient
 libsnmp-base
 libxml2-utils
 network-manager
 ntpdate
 pm-utils
 pulseaudio
 pulseaudio-esound-compat
 pulseaudio-utils
 rhythmbox
 samba-common
 system-tools-backends
 totem-common
 transmission-gtk
 vinagre
 xserver-xorg-input-evdev
 xserver-xorg-video-radeon
 xserver-xorg-video-intel
 xterm
 gnome-pilot
E: Sub-process /usr/bin/dpkg returned an error code (1)
toor@ubuntu:~$ 

```

EDIT:
Now
toor@ubuntu:~$ sudo dpkg -l | grep -v ^ii
produces a far less huger output.

iW  cups                                      1.3.9-2ubuntu6.1                        Common UNIX Printing System(tm) - server
rc  myspell-en-us                             1:2.4.0-2ubuntu4                        English_american dictionary for myspell
pi  system-tools-backends                     2.6.0-1ubuntu1.1                        System Tools to manage computer configuratio
iW  xterm                                     235-1ubuntu1.1                          X terminal emulator

---

### Post by armaguy on 2009-01-26
After reading a bit in man pages of dpkg, I wanted to use dpkg --configure -a, which was in fact what was suggested before. I did and.. no answer! :D
Of course, no news is good news on unix system -which is great.

I ran sudo apt-get update, no bad news or error!

Unfortunatly, sudo apt-get upgrade produced:
```
toor@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  xserver-xorg-video-intel
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 421kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com intrepid-updates/main xserver-xorg-video-intel 2:2.4.1-1ubuntu10.3 [421kB]
Fetched 421kB in 8s (52.5kB/s)                                                                                              
(Reading database ... 130878 files and directories currently installed.)
Preparing to replace xserver-xorg-video-intel 2:2.4.1-1ubuntu10.1 (using .../xserver-xorg-video-intel_2%3a2.4.1-1ubuntu10.3_i386.deb) ...
Unpacking replacement xserver-xorg-video-intel ...
Processing triggers for man-db ...
dpkg: error processing cups (--configure):
 package cups is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing xterm (--configure):
 package xterm is not ready for configuration
 cannot configure (current status `triggers-awaited')
Setting up xserver-xorg-video-intel (2:2.4.1-1ubuntu10.3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cups
 xterm
E: Sub-process /usr/bin/dpkg returned an error code (1)
toor@ubuntu:~$ 

```
I'm getting crash report error after.


Yes, I've been talking to myself for a while, but in hopes that if anyone somehow get the same problem they'll run into this.

---

### Post by Ayuthia on 2009-01-26
> **armaguy said:**
> According to this link, which provided some understanding help, typing the suggested command will list all problematic packages.
So I did, and the output was quite big. Does that mean that all the packages listed are not working correctly? If not, there seems to be a 2 letter code on the left column showing some kind of status, apparently 'ii' means working correctly (which is not being listed). I tried man dpkg to know what the other 2 letters code meant (iU, iW, rc) but no good.

From what I am reading from the man pages and the info that you have posted, the iU and iW are bad errors (based on the top of the dpkg -l info-- uppercase=bad).  It looks like iU means that the package has been unpacked but not configured.  iW looks like the package awaits trigger processing by another package.

From the errors that you received when you tried to install wifi-radar, the system says that those packages (the iU and iW) have already been configured, but dpkg does not think so.  

You might try to see if dpkg-reconfigure can fix some of them.

---

### Post by armaguy on 2009-01-26
SOLVED

Here's how I did:
From the last post I submitted, I saw that cups and xterm were causing trouble. So..

sudo apt-get remove cups

Then sudo apt-get install konsole (so i could get rid of xterm temporarily)

Then sudo apt-get remove xterm.

Then I just apt-get installed all the depencies that I uninstalled in the previous steps (they are showed). Now everything works fine for now.

Thanks you for the big support. I'll also thanks a friend of mine who was passing by and suggested me to use 'apt-get remove' because I was trying to remove cups and xterm using dpkg, which would not let me remove it because of dependencies. apt-get solved it!

Many thanks to the ubuntu forums, indeed these are invaluable.
Even if I flooded them with outputs from my terminal..

---

### Post by armaguy on 2009-01-26
Pretty much solved it (see last posts). It helped me a lot to find out what packages were causing trouble. Thanks for the link!

---

### Post by ChiaGod on 2009-02-05
> **armaguy said:**
> SOLVED

Here's how I did:
From the last post I submitted, I saw that cups and xterm were causing trouble. So..

sudo apt-get remove cups


Thanks! The same worked for me! 
1. Removed the three packages that were mentioned in the synaptic errors.
2. Used apt-get remove to remove them one by one. 
3. Kept tabs of what additional packages were auto-removed by apt-get. 
4. Reinstalled them all a few at a time.

Helps to open a text editor and copy and paste all the "Removing xxx" lines that apt-get remove spits out.  This is to ensure you don't miss re-installing anything critical.

---

### Post by mcmunt on 2009-02-11
Thanks for the info armaguy as I had the same problem for the *libxine1-bin* install. Each time I ran apt-get the following was spat out in the output,

```
dpkg: error processing libxine1-bin (--configure):
 package libxine1-bin is not ready for configuration
 cannot configure (current status `triggers-awaited')
```

Removing it (fail), wait a min, run 'sudo dpkg --configure -a' and then remove it again (pass). Reinstall just libxine1-bin (pass) and then the rest of the dependencies that the removal got too.

---

