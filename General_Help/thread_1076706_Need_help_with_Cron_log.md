---
title: "Need help with Cron log"
date: 2009-02-21
forum: General Help
---

### Post by prickly on 2009-02-21
I recently followed a guide to set up a Cron job to automate updates on one of my servers.

The server is Ubuntu JeOS and I set up Cron as follows:

```
sudo apt-get install aptitude

sudo apt-get install cron

sudo crontab -e

0 1 * * * (aptitude -y update && aptitude -y safe-upgrade) 2>&1 >> /var/log/auto_update.log
```

I have let this run for a few days and checked the auto_update log and have found that it seems to be stuck and doing the same thing over and over each night.

Here is the log:

```
The following NEW packages will be installed:
  linux-image-2.6.27-11-virtual{a}
The following packages will be upgraded:
  busybox-initramfs console-setup dpkg dpkg-dev glibc-source libc6
  libc6-dev libc6-i686 libgnutls26 libldap-2.4-2 libsqlite3-0 libssl0.9.8
  libx11-6 libx11-data linux-image-virtual linux-virtual login ntpdate
  openssl passwd sudo vim-common vim-tiny xkb-data
24 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/46.9MB of archives. After unpacking 30.5MB will be used.
Writing extended state information...
dpkg: `ldconfig' not found on PATH.
dpkg: `start-stop-daemon' not found on PATH.
dpkg: `install-info' not found on PATH.
dpkg: `update-rc.d' not found on PATH.
dpkg: 4 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
```

Can anyone help me figure this out?

Many thanks.

---

### Post by dcstar on 2009-02-21
> **prickly said:**
> I recently followed a guide to set up a Cron job to automate updates on one of my servers.

The server is Ubuntu JeOS and I set up Cron as follows:

```
sudo apt-get install aptitude

sudo apt-get install cron

sudo crontab -e

0 1 * * * (aptitude -y update && aptitude -y safe-upgrade) 2>&1 >> /var/log/auto_update.log
```

I have let this run for a few days and checked the auto_update log and have found that it seems to be stuck and doing the same thing over and over each night.

Here is the log:

```
The following NEW packages will be installed:
  linux-image-2.6.27-11-virtual{a}
The following packages will be upgraded:
  busybox-initramfs console-setup dpkg dpkg-dev glibc-source libc6
  libc6-dev libc6-i686 libgnutls26 libldap-2.4-2 libsqlite3-0 libssl0.9.8
  libx11-6 libx11-data linux-image-virtual linux-virtual login ntpdate
  openssl passwd sudo vim-common vim-tiny xkb-data
24 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/46.9MB of archives. After unpacking 30.5MB will be used.
Writing extended state information...
dpkg: `ldconfig' not found on PATH.
dpkg: `start-stop-daemon' not found on PATH.
dpkg: `install-info' not found on PATH.
dpkg: `update-rc.d' not found on PATH.
**dpkg: 4 expected program(s) not found on PATH.**
**NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.**
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
```

Can anyone help me figure this out?

Many thanks.

Cron's environment is not the same as a user environment.

---

