---
title: "chroot error"
date: 2009-05-12
forum: General Help
---

### Post by ForgivenByJC on 2009-05-12
Trying to Customize a LiveCD and following guide [https://help.ubuntu.com/community/LiveCDCustomization#Customization%20limits](https://help.ubuntu.com/community/LiveCDCustomization#Customization%20limits).
When I got to step```
$ sudo chroot edit
chroot: cannot run command `/sbin/bash': No such file or directory
$
``` that is the error I get.
I Google'd ["chroot: cannot run command `/sbin/bash': No such file or directory"] and got:
```
No results found for "chroot: cannot run command `/sbin/bash': No such file or directory".
Results for chroot: cannot run command `/sbin/bash': No such file or directory (without quotes):
Did you mean: "chroot: cannot run command `/bin/bash': No such file or directory"  Top 2 results shown
```
Could this be a bug?  Thanks.  -John

---

### Post by hw-tph on 2009-05-12
chroot will accept a second parameter as well - the command to run in the chroot. bash lives in /bin, not /sbin, so try this:
```
sudo chroot edit /bin/bash
```

---

### Post by ForgivenByJC on 2009-05-12
Awesome, that worked!  Thanks!

I have never used chroot, so I do not know how it could be messed up.  I have reinstalled coreutils.  Is there a setting wrong somewhere I should change or is ```
sudo chroot <directory> /bin/bash
```just the preferred way to do it?

---

### Post by hw-tph on 2009-05-13
The chroot syntax is **chroot <directory> <command>**, where <command> usually is a shell of some sort (/bin/sh, /bin/bash, /usr/bin/zsh, /usr/local/bin/bash...etc). You could execute **ls** or any command instead of a shell if you wanted to (but if you did that would be all that happened, you wouldn't get a shell with the root set to <directory> but rather the command would execute and then you'd be back in your usual shell).

---

### Post by ForgivenByJC on 2009-05-14
Is there maybe something screwed up in my configuration files (~/.files)?  I am having trouble with my "su" command too.
```
john@Sonja:~$ sudo su
root@Sonja:/home/john# su john
Cannot execute /sbin/bash: No such file or directory
root@Sonja:/home/john# su -s /bin/bash john
john@Sonja:~$
```
In a moment of lucidity I tried the "su -s /bin/bash john" because I was getting a similar error message as the chroot problem.  Maybe one of my ~/.files is messed up?  Wrong permissions?  I did change the permissions --like an idiot, don't EVER do that-- to 777, and had to change them back.  I searched, but cannot find a way to reset the permissions on these files.

```
total 2440
drwxr--r-- 66 john john    4096 2009-05-14 14:02 .
drwxr-xr-x  4 root root    4096 2008-12-17 02:36 ..
drwxrwxr-x  3 john john    4096 2008-12-17 12:00 .adobe
drwxrwxr-x  4 john john    4096 2009-05-14 14:02 .aMule
drwxrwxr-x  2 john john    4096 2009-02-26 23:22 .audacity1.3-john
drwxrwxr-x  4 john john    4096 2009-02-26 23:22 .audacity-data
drwxrwxr-x  3 john john    4096 2009-04-18 14:41 .avidemux
-rw-------  1 john admin  13891 2009-05-13 11:37 .bash_history
-rw-r--r--  1 john john     220 2008-12-16 23:44 .bash_logout
-rw-r--r--  1 john john    3115 2008-12-16 23:44 .bashrc
-rw-rw-r--  1 john john     289 2009-02-26 00:14 .bitpim
drwxrwxr-x  5 john john    4096 2009-03-05 19:57 .bitpim-files
drwxrwxr-x 10 john john    4096 2009-05-14 12:57 .cache
-rw-rw-r--  1 john john     171 2009-01-19 11:23 .cdserverrc
-rw-r--r--  1 john john  876015 2009-05-14 01:28 Company Logos.odg
-rw-r--r--  1 john john  848941 2009-05-14 01:31 Company Logos.pdf
drwxrwxr-x  3 john john    4096 2008-12-17 02:29 .compiz
-rw-rw-r--  1 john john     175 2009-01-13 17:50 .com.zerog.registry.xml
drwxrwxr-x 16 john john    4096 2009-05-01 11:51 .config
drwxrwxr-x  2 john john    4096 2009-01-13 14:01 .cups
drwxrwxr-x  3 john john    4096 2009-04-17 02:35 .cxchromium
drwxrwxr-x  3 john john    4096 2008-12-16 23:46 .dbus
drwxrwxr-x  4 john john    4096 2009-05-14 12:49 Desktop
-rw-rw-r--  1 john john      52 2009-04-20 12:17 .devede
-rw-------  1 john john      26 2009-05-12 14:07 .dmrc
drwxrwxr-x  5 john john    4096 2009-04-17 02:35 Documents
drwxrwxr-x  4 john john    4096 2009-04-23 16:57 .dvdcss
-rw-rw-r--  1 john john      16 2008-12-16 23:46 .esd_auth
drwxrwxr-x  8 john john    4096 2009-04-09 13:43 .evolution
drwxrwxr-x  2 john john    4096 2009-05-06 11:35 .fontconfig
drwxrwxr-x  2 john john    4096 2009-01-16 15:16 .fonts
drwxrwxr-x  5 john john    4096 2009-05-14 08:02 .gconf
drwxrwxr-x  2 john john    4096 2009-05-14 13:50 .gconfd
drwxrwxr-x  4 john john    4096 2008-12-17 03:45 .gegl-0.0
drwxrwxr-x 22 john john    4096 2009-05-14 01:31 .gimp-2.6
-rw-rw-r--  1 john john       0 2009-05-14 13:49 .gksu.lock
drwxrwxr-x  3 john john    4096 2009-03-14 10:25 .gnome
drwxrwxr-x 13 john john    4096 2009-05-14 00:19 .gnome2
drwxrwxr-x  2 john john    4096 2008-12-17 02:19 .gnome2_private
drwxrwxr-x  2 john john    4096 2009-01-26 15:52 .gnupg
drwxrwxr-x  4 john john    4096 2009-03-04 03:22 GNUstep
drwxrwxr-x  2 john john    4096 2009-02-04 16:05 .gpilotd
-rw-rw-r--  1 john john       4 2009-02-04 16:05 .gpilotd.pid
drwxrwxr-x  2 john john    4096 2009-05-07 14:17 .gstreamer-0.10
-rw-r--r--  1 john john     329 2009-05-13 12:52 .gtk-bookmarks
dr-x------  2 john john       0 2009-05-12 14:07 .gvfs
drwxrwxr-x  2 john john    4096 2009-05-12 14:07 .hplip
-rw-------  1 john john   31259 2009-05-12 16:27 .ICEauthority
drwxrwxr-x  2 john john    4096 2009-05-05 13:22 .icedteaplugin
drwxrwxr-x  2 john john    4096 2008-12-17 02:20 .icons
drwxr-x---  7 john john    4096 2009-05-08 13:04 .inkscape
-rwx------  1 root root      29 2009-04-15 16:17 .joycredentials
drwxrwxr-x  3 john john    4096 2008-12-21 22:35 .kde
drwxrwxr-x  2 john john    4096 2008-12-17 02:56 .lirc
-rw-rw-r--  1 john john     296 2008-12-17 02:56 .lircrc
drwxrwxr-x  3 john john    4096 2008-12-16 23:46 .local
-rw-r--r--  1 john john       0 2009-05-14 14:02 ls.txt
drwxrwxr-x  3 john john    4096 2008-12-17 12:00 .macromedia
drwxrwxr-x  3 john john    4096 2009-04-15 10:49 .mcop
-rw-rw-r--  1 john john      31 2009-04-26 01:32 .mcoprc
drwxrwxr-x  4 john john    4096 2009-04-09 11:57 .mozilla
drwxrwxr-x  3 john john    4096 2009-04-09 11:57 .mozilla-thunderbird
drwxrwxr-x  2 john john    4096 2009-01-26 12:29 .mplayer
drwxrwxr-x  2 john john    4096 2008-12-16 23:46 Music
drwxrwxr-x  9 john john    4096 2009-05-01 23:20 .mythtv
drwxrwxr-x  3 john john   20480 2009-04-30 11:27 .nautilus
-rw-r--r--  1 root root    1098 2008-12-17 03:05 .nvidia-settings-rc
drwxr-xr-x  3 john john    4096 2009-05-08 12:46 .openoffice.org
drwxrwxr-x  3 john john    4096 2009-04-30 13:14 .openoffice.org2
drwxrwxr-x  2 john john    4096 2008-12-16 23:46 Pictures
-rw-rw-r--  1 john john      37 2009-05-04 12:37 .printer-groups.xml
-rw-rw-r--  1 john john     675 2008-12-16 23:44 .profile
drwxrwxr-x  2 john john    4096 2008-12-16 23:46 Public
drwx------  2 john john    4096 2009-05-12 14:07 .pulse
-rw-rw-r--  1 john john     256 2008-12-16 23:46 .pulse-cookie
drwxrwxr-x  3 john john    4096 2009-01-07 11:44 .putty
drwxrwxr-x  2 john john    4096 2009-05-01 11:45 .qt
-rw-rw-r--  1 john john    5780 2009-05-13 17:34 .recently-used
-rw-------  1 john john  122302 2009-05-14 13:18 .recently-used.xbel
-rw-rw-r--  1 john john    2815 2009-01-06 17:06 registrations.odb
-rw-rw-r--  1 john john       7 2009-01-26 12:31 Section original.idx
drwxrwxr-x  2 john john    4096 2009-04-18 14:43 .spumux
drwxrwxr-x  2 john john    4096 2008-12-19 14:42 .ssh
-rw-rw-r--  1 john john       0 2008-12-16 23:48 .sudo_as_admin_successful
drwxrwxr-x  2 john john    4096 2008-12-16 23:46 Templates
drwxrwxr-x  2 john john    4096 2008-12-17 02:20 .themes
drwxrwxr-x  5 john john    4096 2009-05-14 00:19 .thumbnails
drwxrwxr-x  2 john john    4096 2009-01-08 12:03 .tsclient
drwxrwxr-x  2 john john    4096 2008-12-18 11:23 .update-manager-core
drwxrwxr-x  2 john john    4096 2008-12-17 00:16 .update-notifier
-rw-r--r--  1 root root    2799 2009-05-12 11:26 .usb-creator.log
drwxrwxr-x  2 john john    4096 2009-02-23 17:20 Videos
drwxrwxr-x  2 john john    4096 2009-05-14 00:19 .wapi
drwxrwxr-x  4 john john    4096 2009-05-13 01:03 .wine
-rw-rw-r--  1 john john     194 2009-01-14 11:05 Winpower_InstallLog.log
-rw-rw-r--  1 john john     116 2009-05-05 16:19 .Xauthority
drwxrwxr-x  3 john john    4096 2008-12-17 03:01 .xmltv
-rw-r--r--  1 john john  200081 2009-05-12 23:59 .xsession-errors
```

Can anybody assist in telling me if this could cause the ```
root@Sonja:/home/john# su john
Cannot execute /sbin/bash: No such file or directory
```error and/or what these permissions should be set to?  Is there a file compare program I could use?

---

### Post by ForgivenByJC on 2009-05-15
/sbin/bash somehow was set in System -> Administration -> Users and Groups -> Advance tab the Shell: was set to /sbin/bash.  Setting that back to /bin/bash corrected this issue.

This does NOT solve the "gksu gnome-terminal" issue.
Does seem to help with ```
pam_sm_authenticate: Called 
pam_sm_authenticate: username = [john] 
Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Error attempting to open [/home/john/.ecryptfs/wrapped-passphrase] for reading 
Error attempting to unwrap passphrase from file [/home/john/.ecryptfs/wrapped-passphrase]; rc = [-5] 
Error adding passphrase key token to user session keyring; rc = [-5]
``` issue.
Also, could not login to tty consoles either, which has been remedied.  I hope this helps someone.

Thank you to hw-tph for your assistance.

---

