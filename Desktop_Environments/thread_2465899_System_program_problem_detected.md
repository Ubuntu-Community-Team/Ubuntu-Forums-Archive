---
title: "System program problem detected"
date: 2021-08-14
forum: Desktop Environments
---

### Post by alro7779 on 2021-08-14
Hi, guys!
Since the day I made desktop-login sound works after all the help I got here, now every time the system starts up, this error window popups:

[[IMG]https://i.ibb.co/xL7kD09/System-startup-error.png[/IMG]]("https://imgbb.com/")

The changes I made after I did what I posted above, are:
[LIST=1]
[*]Editing *GNOME Login Sound.desktop* file and putting another one in ~/.config/autostart/ folder
[*]Changing the *SoundThemeName* of *xsettings* from default to *ubuntu* for having desktop-login sound (with success)
[*]Enabling *EnableEventSounds* of *xsettings*, as well.
[/LIST]

These are the files I got in my *autostart* folder:

[[IMG]https://i.ibb.co/2vYqCBm/autostart-folder.png[/IMG]]("https://ibb.co/v3v1T8g")

Those are the only changes I made on the system for enabling desktop-login and event sounds. By the way, yesterday I had a sudden system reboot, so I don't know if it has something to do with the problem.

I've searched in the **/var/log** folder but I don't know which one of those log files is the right one:
> /var/log$ ls -l *log*
-rw-r--r-- 1 root   root    2077 ago 14 01:52 alternatives.log
-rw-r--r-- 1 root   root   39205 jul 31 02:51 alternatives.log.1
-rw-r----- 1 root   adm        0 ago 14 01:27 apport.log
-rw-r----- 1 root   adm     6787 ago 13 11:03 apport.log.1
-rw-r----- 1 root   adm      956 ago 12 15:04 apport.log.2.gz
-rw-r----- 1 root   adm      439 ago 11 21:00 apport.log.3.gz
-rw-r----- 1 root   adm      670 ago  8 12:15 apport.log.4.gz
-rw-r----- 1 root   adm      317 jul 31 12:24 apport.log.5.gz
-rw-r----- 1 syslog adm   307484 ago 14 10:17 auth.log
-rw-r----- 1 syslog adm   178666 ago  7 20:41 auth.log.1
-rw-r----- 1 syslog adm     4899 ago  1 04:31 auth.log.2.gz
-rw------- 1 root   root   34944 ago 14 09:07 boot.log
-rw------- 1 root   root   25888 ago 14 01:27 boot.log.1
-rw------- 1 root   root    1167 ago 13 00:00 boot.log.2
-rw------- 1 root   root   26579 ago 12 05:12 boot.log.3
-rw------- 1 root   root   16046 ago 11 06:27 boot.log.4
-rw------- 1 root   root   16013 ago 10 02:17 boot.log.5
-rw------- 1 root   root   16753 ago  9 02:22 boot.log.6
-rw------- 1 root   root   24101 ago  8 01:42 boot.log.7
-rw-r--r-- 1 root   root  104003 feb  9  2021 bootstrap.log
-rw-r--r-- 1 root   root  209381 ago 14 01:53 dpkg.log
-rw-r--r-- 1 root   root 1333191 jul 31 12:27 dpkg.log.1
-rw-r--r-- 1 root   root   32032 ago 14 02:07 faillog
-rw-r--r-- 1 root   root   11474 jul 31 12:27 fontconfig.log
-rw-r--r-- 1 root   root    1413 ago 14 09:07 gpu-manager.log
-rw-r--r-- 1 root   root    1420 ago 14 03:41 gpu-manager-switch.log
-rw-r----- 1 syslog adm  1305175 ago 14 09:08 kern.log
-rw-r----- 1 syslog adm  1633836 ago  7 20:41 kern.log.1
-rw-r----- 1 syslog adm   131722 ago  1 04:31 kern.log.2.gz
-rw-rw-r-- 1 root   utmp  292292 ago 14 02:07 lastlog
-rw-r--r-- 1 root   root      55 ago 14 09:08 prime-offload.log
-rw-r--r-- 1 root   root      30 ago 14 09:08 prime-supported.log
-rw-r----- 1 syslog adm   668522 ago 14 10:17 syslog
-rw-r----- 1 syslog adm   633530 ago 14 01:27 syslog.1
-rw-r----- 1 syslog adm    18889 ago 13 00:00 syslog.2.gz
-rw-r----- 1 syslog adm    92527 ago 12 05:12 syslog.3.gz
-rw-r----- 1 syslog adm    52911 ago 11 06:27 syslog.4.gz
-rw-r----- 1 syslog adm    64396 ago 10 02:17 syslog.5.gz
-rw-r----- 1 syslog adm    66310 ago  9 02:22 syslog.6.gz
-rw-r----- 1 syslog adm    85838 ago  8 01:42 syslog.7.gz
-rw------- 1 root   root   29216 ago 14 10:06 ubuntu-advantage.log
-rw------- 1 root   root    2656 jul 31 10:31 ubuntu-advantage.log.1
-rw-r--r-- 1 root   root     102 ago 14 09:08 vbox-setup.log
-rw-r--r-- 1 root   root     102 ago 14 01:55 vbox-setup.log.1
-rw-r--r-- 1 root   root     102 ago 14 01:49 vbox-setup.log.2
-rw-r--r-- 1 root   root     102 ago 13 21:01 vbox-setup.log.3
-rw-r--r-- 1 root   root     102 ago 13 09:39 vbox-setup.log.4
-rw-r--r-- 1 root   root   30547 ago 14 09:28 Xorg.0.log
-rw-r--r-- 1 root   root   29663 ago 14 03:41 Xorg.0.log.old
-rw-r--r-- 1 root   root   27846 ago  5 13:03 Xorg.1.log

Could you please give me a hand?




[IMG]https://ibb.co/3dC37q6[/IMG]
[IMG]https://ibb.co/3dC37q6[/IMG]

---

### Post by deadflowr on 2021-08-14
Crash/System Errors are found in the /var/crash folder.
You can look and see what the problem is there.
Typically you can click on a .crash file and it will open the crash report program which will usually show the the crash information in a basic text box.
It should also give you the choice of sending it or not.
(And sometimes, it may give an option to ignore it in the future.)

---

### Post by T6&amp;sfpER35% on 2021-08-14
also have a look [here](https://www.techrepublic.com/article/how-to-get-rid-of-the-system-crash-popup-in-ubuntu-linux/)

---

### Post by alro7779 on 2021-08-14
Thanks for your reply, guys!

This is what I got in that folder:

[[IMG]https://i.ibb.co/ydsrVQJ/crash-logs-folder.png[/IMG]]("https://imgbb.com/")

I can open those two text-typed files only, but they have _crash date_ different than the actual august 14th, so it's not what I need. The 'caja crash' file... I don't know what program to use with to open it up, but I suppose it's not what I'm looking for either. Any other clue?

---

### Post by alro7779 on 2021-08-14
> **3nd said:**
> also have a look [here]("https://www.techrepublic.com/article/how-to-get-rid-of-the-system-crash-popup-in-ubuntu-linux/") I looked forward doing what you mentioned on looking at that link, and I removed those 2 text crash-logs only, then I logged out and logged in... but the problem persisted, however, I went to that /var/crash folder again, and finally I found the culprit!!! It's the Opera browser:

> ProblemType: CrashArchitecture: amd64
Date: Sat Aug 14 12:51:10 2021
DistroRelease: Ubuntu 20.04
ExecutablePath: /usr/lib/x86_64-linux-gnu/opera/opera

So, from here I suppose that reinstalling that browser, the error message will disappear. Let's see what happens after doing that.

EDIT: Well, that way it didn't work, but removing the 'caja crash' file it did.

---

