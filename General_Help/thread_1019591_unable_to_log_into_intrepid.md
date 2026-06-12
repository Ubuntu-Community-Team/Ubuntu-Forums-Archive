---
title: "unable to log into intrepid"
date: 2008-12-23
forum: General Help
---

### Post by tmetzcc325 on 2008-12-23
Hey guys,

Yesterday I ran into a problem logging in.  Here is what happened:

I have an HP Deskjet 5740 printer hooked up to my box.  Last week, I was able to print just fine.  Last night, When I'd try to print, I'd get a message saying "Printer Deskjet-5700 may not be connected", and all jobs would just say that they were completed, even though nothing was printed.  After a bit of searching, I just tried to delete and then re-add the printer by going to System-Administration-Printing.  All that worked fine, I was able to re-add the printer, but still couldn't print.

I then tried to configure the printer by going to localhost:631 and configuring there.  Being my first time seeing that utility, I was just checking out the various pages and utilties.  I deleted the printer from that page, just fine, but when I tried to re-add it through the web interface, I kept getting the firefox "unable to connect to website error".  Unsure why this was happening, I simply restarted the computer.

Now the bad part...I am unable to log back in.  I enter my credentials, and the GDM login screen just comes right back.  If I enter a bad password, then I get the bad username/password message, but if I enter the correct username/password, the screen goes black, but then the login screen just comes right back.

Same thing happens if I try to go to one of the TTYs and login there.  I get a message if I enter a bad password, but if I enter correct credentials, it just gives me another login prompt.  If I try to connect thru PuTTY from my Windows machine, PuTTY immediately closes after entering my password.

Amd I completely hosed here?  Is there a way to fix this?  I am completely at a loss as to what happened.

Thanks,
Tom

---

### Post by taurus on 2008-12-23
Boot into recovery mode from GRUB menu and post the output of this command.

```
ls -la /home/*username*
```
Replace *username* with your login name.

Also, check the disk space.

```
df -h
```

---

### Post by tmetzcc325 on 2008-12-23
Thanks Taurus, I will try this when I get home.

Disk space should be okay, I just got this computer a few weeks ago.  I did just start using sbackup a few days ago, though, and it is currently still storing backups locally (haven't had time to set it up to move the backups off-site), so I wonder if I misconfigured something and it is eating up a ton of space.

---

### Post by firsttimeuser on 2008-12-23
never mind, I thought you was talking about 8.10 upgrade, deleted my post, sorry

---

### Post by tmetzcc325 on 2008-12-23
Unfortunately, that bug has to do with KDE, and only on the first reboot.

I am using gnome only, and have been able to reboot many times up until last night.  I tried using all the different session options on the login screen, but the same thing happens every time.

---

### Post by tmetzcc325 on 2008-12-28
Sorry for the delay,  I went away for the holidays and never got the chance to reply.  It turns out my disk space was a problem.  My / partition was completely full (because I wasn't paying attention when setting up sbackup), so I was able to clear most of it out from the recovery mode console.  I am not sure what to do next, though.  Here is the output from the two commands above, after clearing space on the / partition:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              15G  2.5G   12G  18% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M   12K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  2.8M 1005M   1% /dev
tmpfs                1007M     0 1007M   0% /dev/shm
lrm                  1007M  2.0M 1005M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda5             276G   20G  242G   8% /home
```

and

```
total 272
drwxr-xr-x 40 tom  tom   4096 Dec 23 21:45 .
drwxr-xr-x  6 root root  4096 Dec  8 21:15 ..
-rw-------  1 tom  tom   2771 Dec 22 21:26 .ICEauthority
drwx------  3 tom  tom   4096 Dec  9 18:05 .adobe
-rw-------  1 tom  tom   3710 Dec 22 21:43 .bash_history
-rw-r--r--  1 tom  tom    220 Dec  8 19:51 .bash_logout
-rw-r--r--  1 tom  tom   3115 Dec  8 19:51 .bashrc
drwxr-xr-x  5 tom  tom   4096 Dec 18 15:29 .cache
drwx------  3 tom  tom   4096 Dec  8 21:29 .compiz
drwxr-xr-x 11 tom  tom   4096 Dec 22 21:26 .config
drwx------  3 tom  tom   4096 Dec  8 19:57 .dbus
-rw-------  1 tom  tom     28 Dec 22 21:26 .dmrc
-rw-------  1 tom  tom     16 Dec  8 19:57 .esd_auth
drwxr-xr-x  3 tom  tom   4096 Dec  8 20:49 .evolution
drwx------  2 tom  tom   4096 Dec  9 22:04 .filezilla
drwxr-xr-x  2 tom  tom   4096 Dec  8 20:57 .fontconfig
drwx------  5 tom  tom   4096 Dec 22 21:26 .gconf
drwx------  2 tom  tom   4096 Dec 22 21:44 .gconfd
drwx------  3 tom  tom   4096 Dec  9 18:32 .gftp
-rw-r-----  1 tom  tom      0 Dec 20 11:51 .gksu.lock
drwx------ 12 tom  tom   4096 Dec 22 21:43 .gnome2
drwx------  2 tom  tom   4096 Dec  8 19:57 .gnome2_private
drwx------  2 tom  tom   4096 Dec  8 19:57 .gnupg
drwxr-xr-x  2 tom  tom   4096 Dec 10 19:32 .gstreamer-0.10
-rw-r--r--  1 tom  tom     77 Dec 22 21:32 .gtk-bookmarks
drwx------  2 tom  tom   4096 Dec  8 19:57 .gvfs
drwxr-xr-x  2 tom  tom   4096 Dec  8 20:02 .icons
drwx------  3 tom  tom   4096 Dec  8 19:58 .local
drwx------  3 tom  tom   4096 Dec  9 18:05 .macromedia
drwx------  4 tom  tom   4096 Dec  8 20:02 .mozilla
drwxr-xr-x  3 tom  tom   4096 Dec 22 21:25 .nautilus
drwx------  3 tom  tom   4096 Dec 14 16:55 .openoffice.org2
drwx------ 10 tom  tom   4096 Dec 18 15:25 .opera
-rw-r--r--  1 tom  tom    675 Dec  8 19:51 .profile
drwxr-xr-x  2 tom  tom   4096 Dec  8 19:58 .pulse
-rw-------  1 tom  tom    256 Dec  8 19:57 .pulse-cookie
drwx------  6 tom  tom   4096 Dec 18 16:18 .purple
drwx------  2 tom  tom   4096 Dec  9 19:40 .putty
drwxr-xr-x  2 tom  tom   4096 Dec  9 18:04 .qt
-rw-------  1 tom  tom    608 Dec 14 16:55 .recently-used
-rw-------  1 tom  tom  58508 Dec 22 21:43 .recently-used.xbel
drwx------  2 tom  tom   4096 Dec  9 22:16 .ssh
-rw-r--r--  1 tom  tom      0 Dec  8 20:09 .sudo_as_admin_successful
drwxr-xr-x  2 tom  tom   4096 Dec  8 20:02 .themes
drwx------  5 tom  tom   4096 Dec 18 14:46 .thumbnails
drwx------  2 tom  tom   4096 Dec 10 19:17 .tsclient
drwxr-xr-x  2 tom  tom   4096 Dec  9 19:39 .update-manager-core
drwx------  2 tom  tom   4096 Dec  8 20:59 .update-notifier
drwxr-xr-x  2 tom  tom   4096 Dec 10 22:33 .wapi
-rw-r--r--  1 tom  tom    129 Dec 12 02:31 .xscreensaver-getimage.cache
-rw-r--r--  1 tom  tom   1609 Dec 22 21:44 .xsession-errors
drwxr-xr-x  2 tom  tom   4096 Dec 22 21:15 Desktop
drwxr-xr-x 22 tom  tom   4096 Dec 13 12:30 Pictures
drwxr-xr-x  9 tom  tom   4096 Dec 14 16:34 financials

```

Thanks a bunch for your help,
Tom

---

### Post by tmetzcc325 on 2008-12-30
Not trying to sound impatient, but I am still unable to login, even after clearing up some disk space.  I understand people are away for the holidays, but is there anyone else around that might have an idea?  I am completely at a loss for what to do next :)

Thanks in advance,
Tom

---

