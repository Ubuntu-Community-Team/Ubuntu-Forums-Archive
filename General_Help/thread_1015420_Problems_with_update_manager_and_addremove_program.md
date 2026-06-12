---
title: "Problems with update manager and add/remove programs"
date: 2008-12-18
forum: General Help
---

### Post by charlescarroll1 on 2008-12-18
I just did a fresh install of Ubuntu 8.10 and I am having problems with both Update Manager and the Add/Remove Applications.  

In Update Manager I am trying to install 192 updates and at first, it would lag and it would say it would take several hours to download.  Now when I try to install the updates I get an error message 

"E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory"

Also, when I try to install VLC from the Add/Remove Applications, I get the same exact error.  I have restarted, and I am still having the same problems.  I am wondering if this is a temporary problem because I was able to download and install some applications last night.  

Is anyone else experiencing the same issues?  Any suggestions would be appreciated.

---

### Post by taurus on 2008-12-18
Sounds like something (adept!) is running in the background.  Open a terminal and post the output of this command.  Make sure you don't have add/remove, update-manager, or synaptic running.

```
ps -A
```

---

### Post by charlescarroll1 on 2008-12-18
Okay, heres what I see.
[HTML]sysop@sysop-laptop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   46 ?        00:00:00 kintegrityd/0
   48 ?        00:00:00 kblockd/0
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  134 ?        00:00:00 cqueue
  138 ?        00:00:00 kseriod
  179 ?        00:00:00 pdflush
  180 ?        00:00:00 pdflush
  181 ?        00:00:00 kswapd0
  223 ?        00:00:00 aio/0
 1176 ?        00:00:00 ksuspend_usbd
 1177 ?        00:00:00 khubd
 1191 ?        00:00:00 ata/0
 1197 ?        00:00:00 ata_aux
 1215 ?        00:00:00 scsi_eh_0
 1216 ?        00:00:00 scsi_eh_1
 1217 ?        00:00:00 scsi_eh_2
 1218 ?        00:00:00 scsi_eh_3
 1990 ?        00:00:01 scsi_eh_4
 1993 ?        00:00:00 scsi_eh_5
 2129 ?        00:00:00 kjournald
 2303 ?        00:00:00 udevd
 2648 ?        00:00:00 kmmcd
 2709 ?        00:00:00 kpsmoused
 4338 tty4     00:00:00 getty
 4339 tty5     00:00:00 getty
 4346 tty2     00:00:00 getty
 4348 tty3     00:00:00 getty
 4350 tty6     00:00:00 getty
 4517 ?        00:00:00 acpid
 4564 ?        00:00:00 kondemand/0
 4626 ?        00:00:01 syslogd
 4675 ?        00:00:11 dd
 4677 ?        00:00:06 klogd
 4700 ?        00:00:03 dbus-daemon
 4722 ?        00:00:00 avahi-daemon
 4723 ?        00:00:00 avahi-daemon
 4767 ?        00:00:00 cupsd
 4845 ?        00:00:01 hald
 4848 ?        00:00:00 console-kit-dae
 4911 ?        00:00:00 hald-runner
 4931 ?        00:00:00 hald-addon-dell
 4932 ?        00:00:00 hald-addon-inpu
 4942 ?        00:00:00 hald-addon-cpuf
 4943 ?        00:00:00 hald-addon-acpi
 4951 ?        00:00:01 hald-addon-stor
 4990 ?        00:00:00 bluetoothd
 4994 ?        00:00:00 btaddconn
 4996 ?        00:00:00 btdelconn
 5022 ?        00:00:00 krfcommd
 5045 ?        00:00:00 NetworkManager
 5049 ?        00:00:00 wpa_supplicant
 5052 ?        00:00:00 nm-system-setti
 5087 ?        00:00:00 gdm
 5088 ?        00:00:00 gdm
 5093 tty7     00:08:51 Xorg
 5125 ?        00:00:00 system-tools-ba
 5160 ?        00:00:00 atd
 5188 ?        00:00:00 cron
 5260 tty1     00:00:00 getty
 5319 ?        00:00:00 dhclient
 5390 ?        00:00:00 gnome-keyring-d
 5401 ?        00:00:00 x-session-manag
 5503 ?        00:00:00 dbus-launch
 5504 ?        00:00:00 dbus-daemon
 5507 ?        00:00:44 pulseaudio
 5510 ?        00:00:00 gconf-helper
 5512 ?        00:00:04 gconfd-2
 5519 ?        00:00:00 seahorse-agent
 5521 ?        00:00:00 gnome-keyring-d
 5530 ?        00:00:02 gnome-settings-
 5531 ?        00:00:00 compiz
 5545 ?        00:00:00 gvfsd
 5569 ?        00:00:00 gvfs-fuse-daemo
 5608 ?        00:00:26 compiz.real
 5616 ?        00:00:08 gnome-screensav
 5617 ?        00:00:00 sh
 5618 ?        00:00:00 compiz-decorato
 5620 ?        00:00:02 gtk-window-deco
 5625 ?        00:00:09 gnome-panel
 5626 ?        00:00:01 nautilus
 5629 ?        00:00:00 bonobo-activati
 5642 ?        00:00:00 gvfs-hal-volume
 5644 ?        00:00:00 gvfs-gphoto2-vo
 5647 ?        00:00:00 gvfsd-burn
 5650 ?        00:00:00 gvfsd-trash
 5654 ?        00:00:01 stickynotes_app
 5657 ?        00:00:00 trashapplet
 5665 ?        00:00:00 mixer_applet2
 5677 ?        00:00:00 trackerd
 5679 ?        00:00:00 evolution-alarm
 5680 ?        00:00:00 nm-applet
 5685 ?        00:00:00 tracker-applet
 5688 ?        00:00:00 bluetooth-apple
 5691 ?        00:00:02 update-notifier
 5693 ?        00:00:00 python
 5694 ?        00:00:00 gnome-power-man
 5714 ?        00:00:01 notification-da
 5825 ?        00:00:09 jockey-backend
 6420 ?        00:00:00 b43
 6532 ?        00:00:02 http
 8977 ?        00:00:08 firefox
 9019 ?        00:00:00 gnome-terminal
 9021 ?        00:00:00 gnome-pty-helpe
 9022 pts/0    00:00:00 bash
 9043 pts/0    00:00:00 ps
[/HTML]

---

### Post by taurus on 2008-12-18
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by charlescarroll1 on 2008-12-18
Okay

---

### Post by charlescarroll1 on 2008-12-18
When I typed sudo apt-get update, it went all through

Heres what I see when I type sudo apt-get upgrade

```

sysop@sysop-laptop:~$ sudo apt-get update
[sudo] password for sysop: 
Get:1 http://security.ubuntu.com intrepid-security Release.gpg [189B]
Ign http://security.ubuntu.com intrepid-security/main Translation-en_CA        
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_CA
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_CA
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_CA
Get:2 http://security.ubuntu.com intrepid-security Release [44.0kB]
Get:3 http://security.ubuntu.com intrepid-security/main Packages [42.0kB]      
Get:4 http://security.ubuntu.com intrepid-security/restricted Packages [1785B] 
Get:5 http://security.ubuntu.com intrepid-security/main Sources [13.2kB]       
Get:6 http://security.ubuntu.com intrepid-security/restricted Sources [571B]   
Get:7 http://security.ubuntu.com intrepid-security/universe Packages [17.6kB] 
Get:8 http://security.ubuntu.com intrepid-security/universe Sources [2429B]    
Get:9 http://security.ubuntu.com intrepid-security/multiverse Packages [1330B] 
Get:10 http://security.ubuntu.com intrepid-security/multiverse Sources [584B]  
Hit http://ca.archive.ubuntu.com intrepid Release.gpg                          
Ign http://ca.archive.ubuntu.com intrepid/main Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid/multiverse Translation-en_CA
Get:11 http://ca.archive.ubuntu.com intrepid-updates Release.gpg [189B]
Hit http://ca.archive.ubuntu.com intrepid-updates/main Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid-updates/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid Release
Get:12 http://ca.archive.ubuntu.com intrepid-updates Release [51.2kB]
Hit http://ca.archive.ubuntu.com intrepid/main Packages                        
Hit http://ca.archive.ubuntu.com intrepid/restricted Packages                  
Hit http://ca.archive.ubuntu.com intrepid/main Sources                         
Hit http://ca.archive.ubuntu.com intrepid/restricted Sources                   
Hit http://ca.archive.ubuntu.com intrepid/universe Packages                    
Hit http://ca.archive.ubuntu.com intrepid/universe Sources                     
Hit http://ca.archive.ubuntu.com intrepid/multiverse Packages                  
Hit http://ca.archive.ubuntu.com intrepid/multiverse Sources                   
Get:13 http://ca.archive.ubuntu.com intrepid-updates/main Packages [256kB]     
Get:14 http://ca.archive.ubuntu.com intrepid-updates/main Packages [256kB]     
Get:15 http://ca.archive.ubuntu.com intrepid-updates/restricted Packages [3861B]
Get:16 http://ca.archive.ubuntu.com intrepid-updates/main Sources [80.1kB]     
Get:17 http://ca.archive.ubuntu.com intrepid-updates/restricted Sources [1169B]
Get:18 http://ca.archive.ubuntu.com intrepid-updates/universe Packages [31.5kB]
Get:19 http://ca.archive.ubuntu.com intrepid-updates/universe Sources [6412B]  
Get:20 http://ca.archive.ubuntu.com intrepid-updates/multiverse Packages [1923B]
Get:21 http://ca.archive.ubuntu.com intrepid-updates/multiverse Sources [803B] 
Fetched 516kB in 2min54s (2967B/s)                                             
Reading package lists... Done
sysop@sysop-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
The following packages will be upgraded:
  alsa-utils apparmor apparmor-utils avahi-autoipd avahi-daemon avahi-utils
  base-files bind9-host ca-certificates capplets-data command-not-found
  command-not-found-data compiz compiz-core compiz-fusion-plugins-main
  compiz-gnome compiz-plugins compiz-wrapper console-setup cups cups-bsd
  cups-client cups-common dnsutils evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-exchange
  evolution-plugins f-spot firefox firefox-3.0 firefox-3.0-branding
  firefox-3.0-gnome-support firefox-gnome-support flashplugin-nonfree
  gdm-guest-session gedit gedit-common gnome-cards-data gnome-control-center
  gnome-games gnome-games-data gnome-panel gnome-panel-data gnome-pilot
  gnome-power-manager gnome-settings-daemon gnome-terminal gnome-terminal-data
  hal-info human-theme initramfs-tools jockey-common jockey-gtk
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libapparmor-perl libapparmor1 libasound2-plugins
  libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libavahi-gobject0
  libavahi-ui0 libbind9-40 libcamel1.2-14 libcups2 libcupsimage2
  libdecoration0 libdeskbar-tracker libdns43 libebackend1.2-0 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libgadu3
  libgdata-google1.2-1 libgdata1.2-1 libglib2.0-0 libglib2.0-data
  libgnome-pilot2 libgnome-window-settings1 libgnomecanvas2-0
  libgnomecanvas2-common libgnutls26 libgphoto2-2 libgphoto2-port0
  libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19
  libgtksourceview2.0-0 libgtksourceview2.0-common libisc44 libisccc40
  libisccfg40 liblcms1 liblwres40 libnm-glib0 libnm-util0 libpam-modules
  libpam-runtime libpam0g libpanel-applet2-0 libpango1.0-0 libpango1.0-common
  libpulse-browse0 libpulse0 libpulsecore5 libshout3 libsmbclient libsnmp-base
  libsnmp15 libtotem-plparser12 libtracker-gtk0 libtrackerclient0 libv4l-0
  libvolume-id0 libwbclient0 libx11-6 libx11-data libx11-xcb1 libxml2
  libxml2-utils linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
  linux-image-2.6.27-7-generic linux-libc-dev linux-restricted-modules-common
  login network-manager network-manager-gnome nvidia-96-modaliases
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-math openoffice.org-style-human openoffice.org-writer passwd
  pm-utils ppp procps pulseaudio pulseaudio-esound-compat
  pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11
  pulseaudio-utils python-libxml2 python-software-properties python-uno
  rhythmbox samba-common smbclient software-properties-gtk splix
  system-tools-backends totem totem-common totem-gstreamer totem-mozilla
  totem-plugins tracker tracker-search-tool tracker-utils transmission-common
  transmission-gtk ttf-opensymbol ubufox udev update-manager
  update-manager-core vinagre xkb-data xserver-xorg-input-evdev
  xserver-xorg-input-vmmouse xulrunner-1.9 xulrunner-1.9-gnome-support
196 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 168MB/184MB of archives.
After this operation, 545kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]
Get:2 http://security.ubuntu.com intrepid-security/main avahi-autoipd 0.6.23-2ubuntu2.1 [48.4kB]
Get:3 http://security.ubuntu.com intrepid-security/main libavahi-common-data 0.6.23-2ubuntu2.1 [31.2kB]
Get:4 http://security.ubuntu.com intrepid-security/main libavahi-common3 0.6.23-2ubuntu2.1 [23.2kB]
Get:5 http://security.ubuntu.com intrepid-security/main libavahi-core5 0.6.23-2ubuntu2.1 [112kB]
Get:6 http://security.ubuntu.com intrepid-security/main avahi-daemon 0.6.23-2ubuntu2.1 [63.1kB]
Get:7 http://security.ubuntu.com intrepid-security/main libavahi-client3 0.6.23-2ubuntu2.1 [51.5kB]
Get:8 http://security.ubuntu.com intrepid-security/main avahi-utils 0.6.23-2ubuntu2.1 [27.5kB]
Get:9 http://security.ubuntu.com intrepid-security/main libavahi-compat-libdnssd1 0.6.23-2ubuntu2.1 [16.6kB]
Get:10 http://security.ubuntu.com intrepid-security/multiverse flashplugin-nonfree 10.0.15.3ubuntu1~intrepid1 [19.2kB]
Get:11 http://security.ubuntu.com intrepid-security/main libavahi-glib1 0.6.23-2ubuntu2.1 [32.1kB]
Get:12 http://security.ubuntu.com intrepid-security/main libavahi-gobject0 0.6.23-2ubuntu2.1 [17.8kB]
Get:13 http://security.ubuntu.com intrepid-security/main libavahi-ui0 0.6.23-2ubuntu2.1 [21.3kB]
1% [1 linux-image-2.6.27-7-generic 2575390/23.4MB 11%]      899B/s 2d 3h7min56s^2% [1 linux-image-2.6.27-7-generic 3356003/23.4MB 14%]    225B/s 8d 11h34min50s^2% [1 linux-image-2.6.27-7-generic 3356003/23.4MB 14%]    225B/s 8d 11h34min50s^2% [1 linux-image-2.6.27-7-generic 3356003/23.4MB 14%]                         
2% [1 linux-image-2.6.27-7-generic 3357463/23.4MB 14%]                         
2% [1 linux-image-2.6.27-7-generic 3357463/23.4MB 14%]

```

...and it just sits like that, with little or no progression.

---

### Post by charlescarroll1 on 2008-12-19
Well friends, the problem seems to have fixed itself.  After letting the console site for several hours, the updates have finished and Add/Remove Applications is letting me install applications.

---

