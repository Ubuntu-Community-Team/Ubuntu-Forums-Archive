---
title: "xscreensaver randomly disappears after automatic updates"
date: 2021-06-19
forum: Desktop Environments
---

### Post by opus1 on 2021-06-19
I upgraded my System 76 meerkat from 16.04 to 18.04 a couple of weeks ago.  i run xubuntu and have the power manager set to lock the screen when the screensaver deactivates.    3 or 4 times now since I upgraded, I have wiggled the mouse 1st thing in the morning to find that the screensaver is not on and the screen is still unlocked.  I then find that there is no "screensaver" entry in the menu, and I open synaptic to find that xscreensaver is no longer installed.  

Re-installing sets things back to normal, however I have no warning when xscreensaver is uninstalled, nor do I have any idea why it is happening.  dpkg.log doesn't seem to provide any information I can use, except that when the screen saver disappeared, the chain of entries in the log does _not_ end in  ```
status installed xscreensaver:amd64 5.36-1ubuntu1
``` This means the last entry is ```
status half-configured xscreensaver:amd64 5.36-1ubuntu1
``` which indicates to me that xscreensaver gets broken somehow.

Since there appears to be no other way to automatically lock the screen without xscreensaver (which seems silly to me), this has become a real issue.  Especially in a busy household with 3 kids and a wife using the same computer.

Any help would be appreciated.

---

### Post by &amp;KyT$0P# on 2021-06-19
Next time this happens can you please:

1) check [FONT=Courier New]/var/log/apt/history.log[/FONT] and post here the entry from that log file where it gets removed, and

2) post here the full terminal output from when you [FONT=Courier New]sudo apt-get install xscreensaver[/FONT] ?

Also can you please post the entire content of [FONT=Courier New]/etc/apt/sources.list[/FONT] and any *.list files in [FONT=Courier New]/etc/apt/sources.list.d/[/FONT] if any?

> **opus1 said:**
> Since there appears to be no other way to automatically lock the screen without xscreensaver (which seems silly to me), 

Seems silly to me too.  When I had Xubuntu 18.04 it was light-locker that handled screen locking, not xscreensaver, and I didn't have to do anything special to set that up in 18.04.

In Xfce Power Manager settings, do you have a Security tab?

---

### Post by opus1 on 2021-06-19
I forgot about /var/log/apt.  I took a look at history.log and there were no entries for the date that things appeared to get borked up.  Likely because I ran my update script, which consists of:```
sudo apt update && sudo apt-get autoremove && sudo apt dist-upgrade

```

(I realize I should just let unattended-upgrade do it's thing, and I realize I could just do a ctrl-R in bash to recall the command string above, but I got into these habits a long time ago, and old habits die hard).

grep'ing dpkg.log for "xscreensaver:" gives this:

```
2021-06-05 20:30:13 status installed xscreensaver:amd64 5.36-1ubuntu1
2021-06-05 20:30:13 remove xscreensaver:amd64 5.36-1ubuntu1 <none>
2021-06-05 20:30:13 status half-configured xscreensaver:amd64 5.36-1ubuntu1
2021-06-05 20:30:13 status half-installed xscreensaver:amd64 5.36-1ubuntu1
2021-06-05 20:30:13 status config-files xscreensaver:amd64 5.36-1ubuntu1
2021-06-05 20:30:13 status config-files xscreensaver:amd64 5.36-1ubuntu1
2021-06-19 05:24:29 install xscreensaver:amd64 5.36-1ubuntu1 5.36-1ubuntu1
2021-06-19 05:24:29 status half-installed xscreensaver:amd64 5.36-1ubuntu1
2021-06-19 05:24:29 status unpacked xscreensaver:amd64 5.36-1ubuntu1
2021-06-19 05:24:29 status unpacked xscreensaver:amd64 5.36-1ubuntu1
2021-06-19 05:24:31 configure xscreensaver:amd64 5.36-1ubuntu1 <none>
2021-06-19 05:24:31 status unpacked xscreensaver:amd64 5.36-1ubuntu1
2021-06-19 05:24:31 status unpacked xscreensaver:amd64 5.36-1ubuntu1
2021-06-19 05:24:31 status half-configured xscreensaver:amd64 5.36-1ubuntu1
2021-06-19 05:24:31 status installed xscreensaver:amd64 5.36-1ubuntu1

```

my guess is that the 6-5-2021 entry is where it was messed up because  the set of entries didn't end with "Status installed".  Going through all the other dpkg logs, I found 2 other instances where that was the case, and I'm pretty sure I had to re-install xscreensaver a total of 3 times now.

/var/log/apt/history.log gives:

```
Start-Date: 2021-06-03  06:57:15
Commandline: /usr/bin/unattended-upgrade
Upgrade: chromium-codecs-ffmpeg-extra:amd64 (90.0.4430.93-0ubuntu0.18.04.1, 91.0.4472.77-0ubuntu0.18.04.1)
End-Date: 2021-06-03  06:57:17

Start-Date: 2021-06-03  06:57:22
Commandline: /usr/bin/unattended-upgrade
Upgrade: dnsmasq-base:amd64 (2.79-1ubuntu0.3, 2.79-1ubuntu0.4)
End-Date: 2021-06-03  06:57:27

Start-Date: 2021-06-03  06:57:32
Commandline: /usr/bin/unattended-upgrade
Upgrade: libpq5:amd64 (10.16-0ubuntu0.18.04.1, 10.17-0ubuntu0.18.04.1)
End-Date: 2021-06-03  06:57:34

Start-Date: 2021-06-03  06:57:38
Commandline: /usr/bin/unattended-upgrade
Upgrade: libwebp6:amd64 (0.6.1-2, 0.6.1-2ubuntu0.18.04.1)
End-Date: 2021-06-03  06:57:39

Start-Date: 2021-06-03  06:57:44
Commandline: /usr/bin/unattended-upgrade
Upgrade: libwebpdemux2:amd64 (0.6.1-2, 0.6.1-2ubuntu0.18.04.1)
End-Date: 2021-06-03  06:57:45

Start-Date: 2021-06-03  06:57:50
Commandline: /usr/bin/unattended-upgrade
Upgrade: libwebpmux3:amd64 (0.6.1-2, 0.6.1-2ubuntu0.18.04.1)
End-Date: 2021-06-03  06:57:52

Start-Date: 2021-06-04  06:14:46
Commandline: /usr/bin/unattended-upgrade
Upgrade: firefox:amd64 (88.0.1+build1-0ubuntu0.18.04.2, 89.0+build2-0ubuntu0.18.04.2)
End-Date: 2021-06-04  06:15:05

Start-Date: 2021-06-04  06:15:10
Commandline: /usr/bin/unattended-upgrade
Upgrade: firefox-locale-en:amd64 (88.0.1+build1-0ubuntu0.18.04.2, 89.0+build2-0ubuntu0.18.04.2)
End-Date: 2021-06-04  06:15:12

Start-Date: 2021-06-08  06:01:11
Commandline: /usr/bin/unattended-upgrade
Upgrade: libarchive13:amd64 (3.2.2-3.1ubuntu0.6, 3.2.2-3.1ubuntu0.7)
End-Date: 2021-06-08  06:01:13

Start-Date: 2021-06-08  06:01:18
Commandline: /usr/bin/unattended-upgrade
Upgrade: libgnome-autoar-0-0:amd64 (0.2.3-1ubuntu0.3, 0.2.3-1ubuntu0.4)
End-Date: 2021-06-08  06:01:19

Start-Date: 2021-06-10  06:28:13
Commandline: /usr/bin/unattended-upgrade
Upgrade: intel-microcode:amd64 (3.20210216.0ubuntu0.18.04.1, 3.20210608.0ubuntu0.18.04.1)
End-Date: 2021-06-10  06:28:43

Start-Date: 2021-06-10  06:28:48
Commandline: /usr/bin/unattended-upgrade
Upgrade: rpcbind:amd64 (0.2.3-0.6ubuntu0.18.04.1, 0.2.3-0.6ubuntu0.18.04.2)
End-Date: 2021-06-10  06:28:55

Start-Date: 2021-06-12  06:20:11
Commandline: /usr/bin/unattended-upgrade
Upgrade: libimage-exiftool-perl:amd64 (10.80-1, 10.80-1ubuntu0.1)
End-Date: 2021-06-12  06:20:22

Start-Date: 2021-06-12  06:20:26
Commandline: /usr/bin/unattended-upgrade
Upgrade: rpcbind:amd64 (0.2.3-0.6ubuntu0.18.04.2, 0.2.3-0.6ubuntu0.18.04.4)
End-Date: 2021-06-12  06:20:32

Start-Date: 2021-06-15  06:15:01
Commandline: /usr/bin/unattended-upgrade
Upgrade: chromium-codecs-ffmpeg-extra:amd64 (91.0.4472.77-0ubuntu0.18.04.1, 91.0.4472.101-0ubuntu0.18.04.1)
End-Date: 2021-06-15  06:15:03

Start-Date: 2021-06-16  06:19:16
Commandline: /usr/bin/unattended-upgrade
Upgrade: imagemagick:amd64 (8:6.9.7.4+dfsg-16ubuntu6.9, 8:6.9.7.4+dfsg-16ubuntu6.11)
End-Date: 2021-06-16  06:19:17

Start-Date: 2021-06-16  06:19:22
Commandline: /usr/bin/unattended-upgrade
Upgrade: imagemagick-6.q16:amd64 (8:6.9.7.4+dfsg-16ubuntu6.9, 8:6.9.7.4+dfsg-16ubuntu6.11)
End-Date: 2021-06-16  06:19:33

Start-Date: 2021-06-16  06:19:37
Commandline: /usr/bin/unattended-upgrade
Upgrade: libmagickcore-6.q16-3:amd64 (8:6.9.7.4+dfsg-16ubuntu6.9, 8:6.9.7.4+dfsg-16ubuntu6.11)
End-Date: 2021-06-16  06:19:39

Start-Date: 2021-06-16  06:19:43
Commandline: /usr/bin/unattended-upgrade
Upgrade: libmagickcore-6.q16-3-extra:amd64 (8:6.9.7.4+dfsg-16ubuntu6.9, 8:6.9.7.4+dfsg-16ubuntu6.11)
End-Date: 2021-06-16  06:19:45

Start-Date: 2021-06-16  06:19:50
Commandline: /usr/bin/unattended-upgrade
Upgrade: libmagickwand-6.q16-3:amd64 (8:6.9.7.4+dfsg-16ubuntu6.9, 8:6.9.7.4+dfsg-16ubuntu6.11)
End-Date: 2021-06-16  06:19:51

Start-Date: 2021-06-16  06:19:56
Commandline: /usr/bin/unattended-upgrade
Upgrade: imagemagick-common:amd64 (8:6.9.7.4+dfsg-16ubuntu6.9, 8:6.9.7.4+dfsg-16ubuntu6.11), imagemagick-6-common:amd64 (8:6.9.7.4+dfsg-16ubuntu6.9, 8:6.9.7.4+dfsg-16ubuntu6.11)
End-Date: 2021-06-16  06:19:59

Start-Date: 2021-06-16  22:10:23
Commandline: apt dist-upgrade
Upgrade: bluez:amd64 (5.48-0ubuntu3.4, 5.48-0ubuntu3.5), bluez-cups:amd64 (5.48-0ubuntu3.4, 5.48-0ubuntu3.5), update-notifier-common:amd64 (3.192.1.10, 3.192.1.11), libsystemd0:amd64 (237-3ubuntu10.47, 237-3ubuntu10.48), snapd:amd64 (2.48.3+18.04, 2.49.2+18.04), system76-driver:amd64 (20.04.33~1621030200~18.04~a62678c~dev, 20.04.34~1623339803~18.04~6324381~dev), squashfs-tools:amd64 (1:4.3-6ubuntu0.18.04.1, 1:4.3-6ubuntu0.18.04.2), python3-pip:amd64 (9.0.1-2.3~ubuntu1.18.04.4, 9.0.1-2.3~ubuntu1.18.04.5), udev:amd64 (237-3ubuntu10.47, 237-3ubuntu10.48), vivaldi-stable:amd64 (3.8.2259.42-1, 4.0.2312.27-1), libudev1:amd64 (237-3ubuntu10.47, 237-3ubuntu10.48), libudev-dev:amd64 (237-3ubuntu10.47, 237-3ubuntu10.48), libnss-myhostname:amd64 (237-3ubuntu10.47, 237-3ubuntu10.48), systemd-sysv:amd64 (237-3ubuntu10.47, 237-3ubuntu10.48), libpam-systemd:amd64 (237-3ubuntu10.47, 237-3ubuntu10.48), systemd:amd64 (237-3ubuntu10.47, 237-3ubuntu10.48), libnss-systemd:amd64 (237-3ubuntu10.47, 237-3ubuntu10.48), bluez-obexd:amd64 (5.48-0ubuntu3.4, 5.48-0ubuntu3.5), libbluetooth3:amd64 (5.48-0ubuntu3.4, 5.48-0ubuntu3.5), update-notifier:amd64 (3.192.1.10, 3.192.1.11), python-pip-whl:amd64 (9.0.1-2.3~ubuntu1.18.04.4, 9.0.1-2.3~ubuntu1.18.04.5), python-pip:amd64 (9.0.1-2.3~ubuntu1.18.04.4, 9.0.1-2.3~ubuntu1.18.04.5), system76-dkms:amd64 (1.0.12~1621869370~18.04~c647a22~dev, 1.0.12~1622747152~18.04~63cf134~dev)
End-Date: 2021-06-16  22:11:57

Start-Date: 2021-06-18  06:15:27
Commandline: /usr/bin/unattended-upgrade
Upgrade: firefox:amd64 (89.0+build2-0ubuntu0.18.04.2, 89.0.1+build1-0ubuntu0.18.04.1)
End-Date: 2021-06-18  06:15:47

Start-Date: 2021-06-18  06:15:51
Commandline: /usr/bin/unattended-upgrade
Upgrade: firefox-locale-en:amd64 (89.0+build2-0ubuntu0.18.04.2, 89.0.1+build1-0ubuntu0.18.04.1)
End-Date: 2021-06-18  06:15:53

Start-Date: 2021-06-18  06:15:57
Commandline: /usr/bin/unattended-upgrade
Upgrade: libxml2:amd64 (2.9.4+dfsg1-6.1ubuntu1.3, 2.9.4+dfsg1-6.1ubuntu1.4)
End-Date: 2021-06-18  06:15:59

Start-Date: 2021-06-18  06:16:03
Commandline: /usr/bin/unattended-upgrade
Upgrade: libxml2-utils:amd64 (2.9.4+dfsg1-6.1ubuntu1.3, 2.9.4+dfsg1-6.1ubuntu1.4)
End-Date: 2021-06-18  06:16:10

Start-Date: 2021-06-18  06:16:14
Commandline: /usr/bin/unattended-upgrade
Upgrade: libhogweed4:amd64 (3.4-1ubuntu0.1, 3.4.1-0ubuntu0.18.04.1), libnettle6:amd64 (3.4-1ubuntu0.1, 3.4.1-0ubuntu0.18.04.1)
End-Date: 2021-06-18  06:16:18

Start-Date: 2021-06-19  05:24:26
Commandline: /usr/sbin/synaptic
Requested-By: bob (1000)
Install: libgnomecanvas2-common:amd64 (2.30.3-3, automatic), libgnomeui-0:amd64 (2.24.5-3.2, automatic), libgnome-keyring-common:amd64 (3.12.0-1build1, automatic), libbonobo2-common:amd64 (2.32.1-3, automatic), libbonoboui2-common:amd64 (2.24.5-4, automatic), libgnomeui-common:amd64 (2.24.5-3.2, automatic), libgnome-2-0:amd64 (2.32.1-6, automatic), libbonoboui2-0:amd64 (2.24.5-4, automatic), libgnome-keyring0:amd64 (3.12.0-1build1, automatic), libgnomevfs2-common:amd64 (1:2.24.4-6.1ubuntu2, automatic), xscreensaver:amd64 (5.36-1ubuntu1), libgnomevfs2-0:amd64 (1:2.24.4-6.1ubuntu2, automatic), liborbit-2-0:amd64 (1:2.14.19-4, automatic), libgnomecanvas2-0:amd64 (2.30.3-3, automatic), libbonobo2-0:amd64 (2.32.1-3, automatic), gconf2:amd64 (3.2.6-4ubuntu1, automatic), libgnome2-common:amd64 (2.32.1-6, automatic)
End-Date: 2021-06-19  05:24:40

Start-Date: 2021-06-19  05:25:22
Commandline: apt dist-upgrade
Upgrade: ubuntu-advantage-tools:amd64 (27.0.2~18.04.1, 27.1~18.04.1), vivaldi-stable:amd64 (4.0.2312.27-1, 4.0.2312.33-1)
End-Date: 2021-06-19  05:25:50

Start-Date: 2021-06-19  12:13:25
Commandline: apt-get install ddccontrol
Requested-By: bob (1000)
Install: libddccontrol0:amd64 (0.4.3-2, automatic), ddccontrol:amd64 (0.4.3-2), ddccontrol-db:amd64 (20171217-1, automatic)
End-Date: 2021-06-19  12:13:32

Start-Date: 2021-06-19  12:18:14
Commandline: apt install ddcutil
Requested-By: bob (1000)
Install: read-edid:amd64 (3.0.2-1build1, automatic), ddcutil:amd64 (0.8.6-1), libi2c0:amd64 (4.0-2, automatic), i2c-tools:amd64 (4.0-2, automatic)
End-Date: 2021-06-19  12:18:23

Start-Date: 2021-06-19  12:29:40
Commandline: apt install edid-decode
Requested-By: bob (1000)
Install: edid-decode:amd64 (0.1~git20160708.c72db881-1)
End-Date: 2021-06-19  12:29:46

Start-Date: 2021-06-19  12:50:27
Commandline: /usr/sbin/synaptic
Requested-By: bob (1000)
Purge: libddccontrol0:amd64 (0.4.3-2), ddccontrol:amd64 (0.4.3-2), edid-decode:amd64 (0.1~git20160708.c72db881-1), ddccontrol-db:amd64 (20171217-1), ddcutil:amd64 (0.8.6-1)
End-Date: 2021-06-19  12:50:36

Start-Date: 2021-06-19  12:53:59
Commandline: /usr/sbin/synaptic
Requested-By: bob (1000)
Install: xautolock:amd64 (1:2.2-5.1)
End-Date: 2021-06-19  12:54:05

Start-Date: 2021-06-19  13:04:31
Commandline: /usr/sbin/synaptic
Requested-By: bob (1000)
Install: suckless-tools:amd64 (43-1)
End-Date: 2021-06-19  13:04:37

Start-Date: 2021-06-19  13:21:36
Commandline: /usr/sbin/synaptic
Requested-By: bob (1000)
Install: libev4:amd64 (1:4.22-1, automatic), giblib1:amd64 (1.2.4-11, automatic), i3lock:amd64 (2.10-1, automatic), scrot:amd64 (0.8-18, automatic), i3lock-fancy:amd64 (0.0~git20160228.0.0fcb933-2)
End-Date: 2021-06-19  13:21:44

```

> Also can you please post the entire content of /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```

> and any *.list files in /etc/apt/sources.list.d/ if any?

```
deadsnakes-ubuntu-ppa-xenial.list
deadsnakes-ubuntu-ppa-xenial.list.distUpgrade
deadsnakes-ubuntu-ppa-xenial.list.save
minecraft-installer-peeps-ubuntu-minecraft-installer-xenial.list
minecraft-installer-peeps-ubuntu-minecraft-installer-xenial.list.distUpgrade
minecraft-installer-peeps-ubuntu-minecraft-installer-xenial.list.save
system76-dev-ubuntu-stable-xenial.list
system76-dev-ubuntu-stable-xenial.list.distUpgrade
system76-dev-ubuntu-stable-xenial.list.save
ubuntu-esm-infra.list
ubuntu-esm-infra.list.distUpgrade
ubuntu-esm-infra.list.save
vivaldi.list
vivaldi.list.distUpgrade
vivaldi.list.save
xenial-partner.list
xenial-partner.list.distUpgrade
xenial-partner.list.save

```

> When I had Xubuntu 18.04 it was light-locker that handled screen locking, not xscreensaver, and I didn't have to do anything special to set that up in 18.04.


I might have been premature in my criticism.  Does light-locker count as a screensaver in the power manager?  I think light-locker worked until the upgrade when it was replaced by an account selector with a purple screen that says "ubuntu" at the bottom rather than "xubuntu".  what ever lock program was installed before didn't play well with xscreensaver because we had to enter the password into both xscreensaver and whatever built-in locker there was.

Maybe it's time for me to to get rid of xscreensaver.  we just use it because it shows family photos, but if it's this much trouble...

Without xscreensaver though, the screen never locks.  you asked > In Xfce Power Manager settings, do you have a Security tab? the answer is "yes" and the options for "automatically lock the session" are : "Never | When the screensaver is activated | When the screensaver is deactivated".  without a screensaver it doesn't work. :(

---

### Post by guiverc on 2021-06-20
Are you aware that flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors), so you're asking about a release that is now EOL.

- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)
- [https://lubuntu.me/bionic-5-released/](https://lubuntu.me/bionic-5-released/)
- [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

A recent Ubuntu Weekly Newsletter
- [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses)
(or on this forum see [https://ubuntuforums.org/showthread.php?t=2461582](https://ubuntuforums.org/showthread.php?t=2461582)) highlighted flavors are now EOL.

Not all flavors gave EOL notices, but if you look they had dates provided already. eg. Xubuntu mentioned on [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/) that EOL was 29-April-2021

Note:  *If you box is i386/32-bit only then you can't upgrade.. as whilst Xubuntu also provided ISOs for 18.10, and into the disco (19.04) cycle, those release are EOL too.*

---

### Post by opus1 on 2021-06-20
Are you kidding?  I never knew that "Flavors" had a shorter life than regular ubuntu.  I just upgraded a month ago.  Now I have to do it again?

---

### Post by opus1 on 2021-06-20
Since I installed xubuntu over ubuntu, does that mean if I select ubuntu at the log-in screen, I will be using a supported OS again?  what are the security ramifications of doing that?  It seems like there would be unsupported components installed on my computer through an older version of ubuntu -- doesn't that pose a security risk?

---

### Post by &amp;KyT$0P# on 2021-06-20
> **opus1 said:**
> Since I installed xubuntu over ubuntu,

Umm.  That is almost certainly the actual problem here.  I tried this mix a couple times (once Xubuntu-over-Ubuntu and once Ubuntu-over-Xubuntu) and couldn't get screen lock in Xfce to work *at all* either way.

Unfortunately, my advice would be to start from a completely clean install of Xubuntu (20.04 if possible), preserving only the home directories - everything else needs to be erased or rebuilt from scratch.  Sorry. :(

(By the way, in Xubuntu 20.04 you can choose the command for screen locking to be anything you want.)

---

### Post by guiverc on 2021-06-20
> **opus1 said:**
> Are you kidding?  I never knew that "Flavors" had a shorter life than regular ubuntu.  I just upgraded a month ago.  Now I have to do it again?

Both Ubuntu and *flavors* had 2 years of supported life, then that was extended to 3 years.  Ubuntu increased to 5 years, however no *flavor* increased supported life beyond 5 years   (*always exceptions to rules though; Canonical helped fund Ubuntu Kylin 16.04 so it had 5 years, but it was a once-off only*)

You can use `ubuntu-support-status` to view what programs are still supported (on later releases the tool is `ubuntu-security-status` but I prefer the older one myself, despite parts of it being unclear which resulted in the change).

If you don't believe me, you can read release notes or any official documents.

- [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/)
- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)
..
- [https://fridge.ubuntu.com/2018/04/27/ubuntu-18-04-lts-bionic-beaver-released/](https://fridge.ubuntu.com/2018/04/27/ubuntu-18-04-lts-bionic-beaver-released/)

Where you'll note it states clearly

> "Maintenance updates will be provided for 5 years for Ubuntu  Desktop, Ubuntu Server, Ubuntu Cloud, and Ubuntu Core. Ubuntu Studio  will be supported for 9 months. All the remaining flavours will be  supported for 3 years."
[B]
I'd always recommend reading release notes[/B]... Ubuntu Studio 18.04 was **not** a LTS release, but I'm constantly seeing surprise by users who make assumptions (the Ubuntu Studio team provided *extended *support via PPA for 18.04; which they clearly documented for those that looked).

(*grrr..  why I'd have to quote from that page, I see an petty error, now I gotta go fix it!)*

---

