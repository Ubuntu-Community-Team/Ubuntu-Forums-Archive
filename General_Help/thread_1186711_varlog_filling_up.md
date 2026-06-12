---
title: "/var/log/ filling up"
date: 2009-06-13
forum: General Help
---

### Post by hg21 on 2009-06-13
Hi,

Since upgrading to Jaunty I regularly get messages saying I running out of disc space. This has never happened before.

du shows /var/log is the problem ~6.5Gb.

kern.log and messages and syslog seem excessive at ~1.5Gb each with thousands consecutive entries like:-
=======================================
 Jun 13 17:58:29 ahg kernel: [12371.936020] urb status -32
==========================================
the only thing changing from line to line being the number  after the dot  in the [  ] brackets. This cannot be right.

 What does it mean? My research suggests it's a usb problem

My /etc/logrotate.conf file is:-
=============================================
# see "man logrotate" for details
# rotate log files weekly
weekly

# keep 4 weeks worth of backlogs
rotate 2

# create new (empty) log files after rotating old ones
#create

 # uncomment this if you want your log files compressed
compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

/var/log/btmp {
    missingok
    monthly
    create 0660 root utmp
    rotate 1
}

# system-specific logs may be configured here

================================================



Thanks

---

### Post by bab1 on 2009-06-13
> What does it mean? My research suggests it's a usb problem

I'm no USB driver expert, but my goggling confirms that it is a USB communications problem.  What do you have attached via a USB port?

---

### Post by ActiveFrost on 2009-06-13
If it's 6GB in size, what's exactly being stored ? Logs for what ?

---

### Post by hg21 on 2009-06-14
> **bab1 said:**
> I'm no USB driver expert, but my goggling confirms that it is a USB communications problem.  What do you have attached via a USB port?

Thanks for reply bab1

A konica-minolta printer - attached but usually switched of
A Avermedia TV card - usually on but doesn't always start on boot
A Roland keyboard via a MIDI dongle - often switched off

I'm keeping the latter two unplugged for a few days I'll then put them back one at a time. I am beining to wonder if this problem only started after I rigged up the Roland.

---

### Post by hg21 on 2009-06-14
> **ActiveFrost said:**
> If it's 6GB in size, what's exactly being stored ? Logs for what ?

Thanks for reply ActiveFrost.

Here's a listing as of now. I deleted the big kern.log, syslog and messages files yesterday. New ones have been created ( as expected) but they are reasonably sized and do not contain any urb status messages as yet. (I unplugged 2 usb things see reply to bab1)

I also did rm -rf /var/log*.n.* where n=2,3,4,5,6 yesterday, ie zipped backlogs.

This set up, for what is logged, is as set by jaunty install.

$ ls -alF /var/log
total 976                         
drwxr-xr-x  6 root   root   4096 2009-06-14 12:12 ./
drwxr-xr-x 15 root   root   4096 2009-05-20 14:48 ../
drwxr-xr-x  2 root   root   4096 2009-06-05 10:06 apt/
-rw-r-----  1 syslog adm   40330 2009-06-14 12:30 auth.log
-rw-r-----  1 syslog adm  141247 2009-06-12 10:01 auth.log.0
-rw-r-----  1 syslog adm    9598 2009-06-05 10:20 auth.log.1.gz
drwxr-xr-x  2 root   root   4096 2009-05-20 14:48 ConsoleKit/
drwxr-xr-x  2 root   lp     4096 2009-06-14 12:12 cups/
-rw-r-----  1 syslog adm   19430 2009-06-14 11:54 daemon.log
-rw-r-----  1 syslog adm   77679 2009-06-12 09:45 daemon.log.0
-rw-r-----  1 syslog adm    6116 2009-06-05 09:54 daemon.log.1.gz
-rw-r-----  1 syslog adm   12856 2009-06-14 11:54 debug
-rw-r-----  1 syslog adm   49590 2009-06-12 09:44 debug.0
-rw-r-----  1 syslog adm    4499 2009-06-05 09:54 debug.1.gz
-rw-r--r--  1 root   root   1458 2009-06-14 11:54 dkms_autoinstaller
-rw-r--r--  1 root   adm   30875 2009-06-14 11:54 dmesg
-rw-r--r--  1 root   adm   31615 2009-06-13 14:32 dmesg.0
-rw-r--r--  1 root   adm    9904 2009-06-12 09:44 dmesg.1.gz
-rw-r--r--  1 root   adm   10220 2009-06-11 12:19 dmesg.2.gz
-rw-r-----  1 root   adm   90423 2009-06-13 17:17 dpkg.log
-rw-r--r--  1 root   root   5578 2009-05-21 13:04 dpkg.log.1
-rw-r--r--  1 root   root      0 2009-06-14 12:12 kdm.log
-rw-r--r--  1 root   root    764 2009-06-14 12:12 kdm.log.1
-rw-r--r--  1 root   root    662 2009-06-13 15:02 kdm.log.2.gz
-rw-r--r--  1 syslog adm   45089 2009-06-14 11:54 kern.log
drwxr-xr-x  2 root   root   4096 2009-05-20 14:50 landscape/
-rw-r--r--  1 syslog adm       0 2009-05-21 09:27 lpr.log
-rw-r--r--  1 syslog adm       0 2009-05-21 09:27 mail.err
-rw-r--r--  1 syslog adm       0 2009-05-21 09:27 mail.info
-rw-r--r--  1 syslog adm       0 2009-05-21 09:27 mail.log
-rw-r--r--  1 syslog adm       0 2009-05-21 09:27 mail.warn
-rw-r--r--  1 syslog adm   39998 2009-06-14 12:12 messages
-rw-r--r--  1 root   root    191 2009-06-14 11:54 pm-powersave.log
-rw-r--r--  1 root   root      0 2009-06-05 10:45 pycentral.log
-rw-r--r--  1 root   root      0 2009-06-14 12:12 scrollkeeper.log
-rw-r--r--  1 root   root     20 2009-06-07 15:11 scrollkeeper.log.1.gz
-rw-r--r--  1 root   root     20 2009-05-31 15:51 scrollkeeper.log.2.gz
-rw-r-----  1 syslog adm     650 2009-06-14 12:30 syslog
-rw-r-----  1 syslog adm   54171 2009-06-14 12:10 syslog.0
-rw-r--r--  1 root   root 153737 2009-06-14 11:54 udev
-rw-r-----  1 syslog adm     156 2009-06-14 11:54 user.log
-rw-r-----  1 syslog adm     700 2009-06-12 09:44 user.log.0
-rw-r-----  1 syslog adm     212 2009-06-05 09:54 user.log.1.gz
-rw-r--r--  1 root   root      0 2009-06-14 12:12 wpa_supplicant.log
-rw-r--r--  1 root   root     20 2009-06-13 15:02 wpa_supplicant.log.1.gz
-rw-r--r--  1 root   root     20 2009-06-12 10:04 wpa_supplicant.log.2.gz
-rw-r--r--  1 root   root  10770 2009-06-14 11:54 Xorg.0.log
-rw-r--r--  1 root   root  11817 2009-06-13 23:39 Xorg.0.log.old

---

