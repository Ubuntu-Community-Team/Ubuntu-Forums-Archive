---
title: "Sound problem on lenovo r61 using Ubuntu 8.10"
date: 2009-03-14
forum: General Help
---

### Post by alphageek89 on 2009-03-14
am using UBUNTU 8.10 on Lenovo r61.around 2 weeks ago my sound stopped working (most probably after an update,don't remember exactly when).
These are some of the things that i tried :
```
System/Preferences/Sound 
	Autodetect did not have any sound with test button.
	ALSA - Advanced LINUX Sound Architecture NO SOUND either
	OSS - Open Sound System does not have sound.
```
	
```
I typed alsamixer in terminal and master was set to 100 and these where the things it said
	 Card: PulseAudio                                                             
	 Chip: PulseAudio                                                             
	 View: [Playback] Capture  All                                                
	 Item: Master
```
```

In synaptic package manager this is my last update history
		Commit Log for Thu Feb 19 01:21:33 2009


		Upgraded the following packages:
at-spi (1.24.0-0ubuntu3) to 1.24.0-0ubuntu3.8.10.1
busybox-initramfs (1:1.10.2-1ubuntu6) to 1:1.10.2-1ubuntu7
consolekit (0.2.10-1ubuntu9) to 0.2.10-1ubuntu10
dpkg (1.14.20ubuntu6) to 1.14.20ubuntu6.1
dpkg-dev (1.14.20ubuntu6) to 1.14.20ubuntu6.1
evolution (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
evolution-common (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
evolution-data-server (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
evolution-data-server-common (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
evolution-exchange (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
evolution-plugins (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
fglrx-modaliases (2:8.543-0ubuntu4) to 2:8.543-0ubuntu4.1
firefox (3.0.5+nobinonly-0ubuntu0.8.10.1) to 3.0.6+nobinonly-0ubuntu0.8.10.1
firefox-3.0 (3.0.5+nobinonly-0ubuntu0.8.10.1) to 3.0.6+nobinonly-0ubuntu0.8.10.1
firefox-3.0-branding (3.0.5+nobinonly-0ubuntu0.8.10.1) to 3.0.6+nobinonly-0ubuntu0.8.10.1
firefox-3.0-gnome-support (3.0.5+nobinonly-0ubuntu0.8.10.1) to 3.0.6+nobinonly-0ubuntu0.8.10.1
firefox-gnome-support (3.0.5+nobinonly-0ubuntu0.8.10.1) to 3.0.6+nobinonly-0ubuntu0.8.10.1
ghostscript (8.63.dfsg.1-0ubuntu6.1) to 8.63.dfsg.1-0ubuntu6.2
ghostscript-x (8.63.dfsg.1-0ubuntu6.1) to 8.63.dfsg.1-0ubuntu6.2
gnome-power-manager (2.24.0-0ubuntu8.1) to 2.24.0-0ubuntu8.2
gvfs (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
gvfs-backends (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
gvfs-bin (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
gvfs-fuse (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
hal-info (20081124-0ubuntu1~intrepid) to 20090128-0ubuntu1~intrepid2
libapache2-mod-php5 (5.2.6-2ubuntu4) to 5.2.6-2ubuntu4.1
libatspi1.0-0 (1.24.0-0ubuntu3) to 1.24.0-0ubuntu3.8.10.1
libc6 (2.8~20080505-0ubuntu8) to 2.8~20080505-0ubuntu9
libc6-dev (2.8~20080505-0ubuntu8) to 2.8~20080505-0ubuntu9
libc6-i686 (2.8~20080505-0ubuntu8) to 2.8~20080505-0ubuntu9
libcamel1.2-14 (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
libck-connector0 (0.2.10-1ubuntu9) to 0.2.10-1ubuntu10
libebackend1.2-0 (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
libebook1.2-9 (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
libecal1.2-7 (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
libedata-book1.2-2 (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
libedata-cal1.2-6 (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
libedataserver1.2-11 (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
libedataserverui1.2-8 (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
libegroupwise1.2-13 (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
libexchange-storage1.2-3 (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
libgdata-google1.2-1 (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
libgdata1.2-1 (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
libgs8 (8.63.dfsg.1-0ubuntu6.1) to 8.63.dfsg.1-0ubuntu6.2
libgvfscommon0 (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
libldap-2.4-2 (2.4.11-0ubuntu6) to 2.4.11-0ubuntu6.1
libnautilus-extension1 (1:2.24.1-0ubuntu1) to 1:2.24.1-0ubuntu2
libpam-ck-connector (0.2.10-1ubuntu9) to 0.2.10-1ubuntu10
libpoppler-glib3 (0.8.7-1) to 0.8.7-1ubuntu0.1
libpoppler3 (0.8.7-1) to 0.8.7-1ubuntu0.1
libpq5 (8.3.5-0ubuntu8.10) to 8.3.6-0ubuntu8.10
libpulse-browse0 (0.9.10-2ubuntu9.2) to 0.9.10-2ubuntu9.3
libpulse0 (0.9.10-2ubuntu9.2) to 0.9.10-2ubuntu9.3
libpulsecore5 (0.9.10-2ubuntu9.2) to 0.9.10-2ubuntu9.3
libsqlite3-0 (3.5.9-3) to 3.5.9-3ubuntu1
libv4l-0 (0.5.6-1~intrepid1) to 0.5.7-1~intrepid1
libxine1 (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3.1intrepid1
libxine1-bin (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3.1intrepid1
libxine1-console (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3.1intrepid1
libxine1-ffmpeg (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3.1intrepid1
libxine1-misc-plugins (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3.1intrepid1
libxine1-x (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3.1intrepid1
linux-generic (2.6.27.9.13) to 2.6.27.11.14
linux-headers-generic (2.6.27.9.13) to 2.6.27.11.14
linux-image-generic (2.6.27.9.13) to 2.6.27.11.14
linux-restricted-modules-generic (2.6.27.9.13) to 2.6.27.11.14
nautilus (1:2.24.1-0ubuntu1) to 1:2.24.1-0ubuntu2
nautilus-data (1:2.24.1-0ubuntu1) to 1:2.24.1-0ubuntu2
nvidia-173-modaliases (173.14.12-1-0ubuntu4) to 173.14.12-1-0ubuntu5.1
nvidia-96-modaliases (96.43.09-0ubuntu1) to 96.43.09-0ubuntu1.1
openjdk-6-jdk (6b12-0ubuntu6) to 6b12-0ubuntu6.1
openjdk-6-jre (6b12-0ubuntu6) to 6b12-0ubuntu6.1
openjdk-6-jre-headless (6b12-0ubuntu6) to 6b12-0ubuntu6.1
php5 (5.2.6-2ubuntu4) to 5.2.6-2ubuntu4.1
php5-common (5.2.6-2ubuntu4) to 5.2.6-2ubuntu4.1
php5-mysql (5.2.6-2ubuntu4) to 5.2.6-2ubuntu4.1
poppler-utils (0.8.7-1) to 0.8.7-1ubuntu0.1
pulseaudio (0.9.10-2ubuntu9.2) to 0.9.10-2ubuntu9.3
pulseaudio-esound-compat (0.9.10-2ubuntu9.2) to 0.9.10-2ubuntu9.3
pulseaudio-module-gconf (0.9.10-2ubuntu9.2) to 0.9.10-2ubuntu9.3
pulseaudio-module-hal (0.9.10-2ubuntu9.2) to 0.9.10-2ubuntu9.3
pulseaudio-module-x11 (0.9.10-2ubuntu9.2) to 0.9.10-2ubuntu9.3
pulseaudio-utils (0.9.10-2ubuntu9.2) to 0.9.10-2ubuntu9.3
python-pyatspi (1.24.0-0ubuntu3) to 1.24.0-0ubuntu3.8.10.1
rhythmbox (0.11.6svn20081008-0ubuntu4.2) to 0.11.6svn20081008-0ubuntu4.3
sqlite3 (3.5.9-3) to 3.5.9-3ubuntu1
sudo (1.6.9p17-1ubuntu2) to 1.6.9p17-1ubuntu2.1
ufw (0.23.2) to 0.23.3
vim-common (1:7.1.314-3ubuntu3) to 1:7.1.314-3ubuntu3.1
vim-tiny (1:7.1.314-3ubuntu3) to 1:7.1.314-3ubuntu3.1
xserver-xorg-video-intel (2:2.4.1-1ubuntu10) to 2:2.4.1-1ubuntu10.3
xulrunner-1.9 (1.9.0.5+nobinonly-0ubuntu0.8.10.1) to 1.9.0.6+nobinonly-0ubuntu0.8.10.1
xulrunner-1.9-gnome-support (1.9.0.5+nobinonly-0ubuntu0.8.10.1) to 1.9.0.6+nobinonly-0ubuntu0.8.10.1

Installed the following packages:
linux-headers-2.6.27-11 (2.6.27-11.27)
linux-headers-2.6.27-11-generic (2.6.27-11.27)
```

Hope this information is enough :D
Please help!I hate using vista meanwhile.

---

### Post by alphageek89 on 2009-03-16
can someone help?

---

### Post by manishtech on 2009-03-19
Pulseaudio has always given me nightmares.

I found the following HOWTOs on the net, check them

[http://www.pulseaudio.org/wiki/Troubleshooting](http://www.pulseaudio.org/wiki/Troubleshooting)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Try to kill the pulseaudio daemon
```
pulseaudio -k
```

and then try to restart it

```
pulseaudio -D -vvv
```

If the above two commands don't work then maybe the configuration files have been borked. Check the above 3 links for getting it right.

---

### Post by alphageek89 on 2009-03-22
thanjs a lot :p:p:p:p:p

Part C: Intrepid Ibex (8.10)
Follow the steps in this section only if you are running the Intrepid Ibex release.
Disclaimer: Currently there are no updated packages for Intrepid in my PPA (except for an updated nspluginwrapper package for i386 users). I have decided to keep this step in the guide in case I upload any important updates that will not make it into the official repositories. I will never upload any "risky" packages (i.e. highly untested backports), only upgrades that seem compelling and relatively stable.

1. Edit /etc/apt/sources.list:
Code:

$ gksudo gedit /etc/apt/sources.list

If they don't already exist, add the following lines to the end of this file and save:
Code:

# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main

2. Update your repositories and upgrade packages:
Code:

$ sudo apt-get update && sudo apt-get dist-upgrade

this did the trick.

---

