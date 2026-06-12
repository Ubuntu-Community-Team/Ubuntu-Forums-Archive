---
title: "Just about had it with Ubuntu"
date: 2009-02-21
forum: General Help
---

### Post by azathrael on 2009-02-21
This is the third time I've asked for help here and I've just found something in common with all 3 of my problems.

It's ALWAYS after an update.

I've just about had it with Ubuntu, and my image of it being anything of a reliable OS alternative to Windows or Mac is almost gone.  This is the last time I'm going to ask for help here, and if the OS has any major problems again, I am through with Ubuntu.

Here is my problem:

After the last update, my computer will randomly log off and put me into the login screen.  I have NEVER had this problem before.  I usually left this laptop on for nights and had no problems; now it will just randomly put me into the login screen when I'm using Firefox or Movie Player or just leave it alone and take a nap.

What is going on?

PS: I read all the other help threads about "random restarts".  As for my laptop, NO it is not overheating; It's a brand new laptop I've had for less than a year.

---

### Post by azathrael on 2009-02-21
This is my auth.log

Feb 21 00:35:35 sam-laptop gdm[5796]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Feb 21 00:35:50 sam-laptop seahorse-daemon[6369]: Failed to send buffer
Feb 21 00:36:05 sam-laptop seahorse-daemon[6369]: Failed to send buffer
Feb 21 00:36:05 sam-laptop gnome-keyring-daemon[6165]: adding removable location: volume_label_Ubuntu_8_04_1_i386 at /media/cdrom0
Feb 21 00:37:30 sam-laptop sudo:     root : TTY=unknown ; PWD=/ ; USER=sam ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Feb 21 00:37:30 sam-laptop sudo: pam_unix(sudo:session): session opened for user sam by (uid=0)
Feb 21 00:37:30 sam-laptop sudo: pam_unix(sudo:session): session closed for user sam
Feb 21 00:37:30 sam-laptop sudo:     root : TTY=unknown ; PWD=/ ; USER=sam ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Feb 21 00:37:30 sam-laptop sudo: pam_unix(sudo:session): session opened for user sam by (uid=0)
Feb 21 00:37:30 sam-laptop sudo: pam_unix(sudo:session): session closed for user sam
Feb 21 00:37:30 sam-laptop sudo:     root : TTY=unknown ; PWD=/ ; USER=sam ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Feb 21 00:37:30 sam-laptop sudo: pam_unix(sudo:session): session opened for user sam by (uid=0)
Feb 21 00:37:30 sam-laptop sudo: pam_unix(sudo:session): session closed for user sam
Feb 21 01:09:30 sam-laptop sudo:      sam : TTY=unknown ; PWD=/home/sam ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 73400323 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmp7kAa6b
Feb 21 01:09:31 sam-laptop sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Feb 21 01:09:31 sam-laptop sudo: pam_unix(sudo:session): session closed for user root
Feb 21 01:17:01 sam-laptop CRON[9263]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 01:17:01 sam-laptop CRON[9263]: pam_unix(cron:session): session closed for user root
Feb 21 01:44:39 sam-laptop gdm[5796]: pam_unix(gdm:session): session closed for user sam
Feb 21 02:17:01 sam-laptop CRON[11780]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 02:17:01 sam-laptop CRON[11780]: pam_unix(cron:session): session closed for user root
Feb 21 03:17:01 sam-laptop CRON[14175]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 03:17:01 sam-laptop CRON[14175]: pam_unix(cron:session): session closed for user root
Feb 21 04:17:01 sam-laptop CRON[16570]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 04:17:01 sam-laptop CRON[16570]: pam_unix(cron:session): session closed for user root
Feb 21 05:17:01 sam-laptop CRON[18965]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 05:17:01 sam-laptop CRON[18965]: pam_unix(cron:session): session closed for user root
Feb 21 06:17:01 sam-laptop CRON[21360]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 06:17:01 sam-laptop CRON[21360]: pam_unix(cron:session): session closed for user root
Feb 21 06:25:01 sam-laptop CRON[21679]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 06:25:01 sam-laptop CRON[21679]: pam_unix(cron:session): session closed for user root
Feb 21 07:17:01 sam-laptop CRON[23757]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 07:17:01 sam-laptop CRON[23757]: pam_unix(cron:session): session closed for user root
Feb 21 07:30:01 sam-laptop CRON[24276]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 07:30:02 sam-laptop CRON[24276]: pam_unix(cron:session): session closed for user root
Feb 21 08:17:01 sam-laptop CRON[26181]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 08:17:01 sam-laptop CRON[26181]: pam_unix(cron:session): session closed for user root
Feb 21 09:17:01 sam-laptop CRON[28576]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 09:17:01 sam-laptop CRON[28576]: pam_unix(cron:session): session closed for user root
Feb 21 10:17:01 sam-laptop CRON[30971]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 10:17:01 sam-laptop CRON[30971]: pam_unix(cron:session): session closed for user root
Feb 21 11:17:01 sam-laptop CRON[898]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 11:17:01 sam-laptop CRON[898]: pam_unix(cron:session): session closed for user root
Feb 21 12:17:01 sam-laptop CRON[3308]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 12:17:01 sam-laptop CRON[3308]: pam_unix(cron:session): session closed for user root
Feb 21 13:17:01 sam-laptop CRON[5809]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 13:17:01 sam-laptop CRON[5809]: pam_unix(cron:session): session closed for user root
Feb 21 13:53:36 sam-laptop gdm[10458]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Feb 21 13:53:36 sam-laptop gnome-keyring-daemon[7292]: adding removable location: volume_label_Ubuntu_8_04_1_i386 at /media/cdrom0
Feb 21 13:53:42 sam-laptop seahorse-daemon[7496]: Failed to send buffer
Feb 21 13:53:47 sam-laptop seahorse-daemon[7496]: Failed to send buffer
Feb 21 13:54:35 sam-laptop seahorse-daemon[7496]: left gtk_main 
Feb 21 13:54:35 sam-laptop gdm[10458]: pam_unix(gdm:session): session closed for user sam
Feb 21 13:56:38 sam-laptop gdm[5812]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Feb 21 13:56:52 sam-laptop seahorse-daemon[6300]: Failed to send buffer
Feb 21 13:57:12 sam-laptop seahorse-daemon[6300]: Failed to send buffer
Feb 21 13:57:12 sam-laptop gnome-keyring-daemon[6089]: adding removable location: volume_label_Ubuntu_8_04_1_i386 at /media/cdrom0
Feb 21 14:17:01 sam-laptop CRON[7641]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 14:17:02 sam-laptop CRON[7641]: pam_unix(cron:session): session closed for user root
Feb 21 15:17:01 sam-laptop CRON[10458]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 15:17:01 sam-laptop CRON[10458]: pam_unix(cron:session): session closed for user root
Feb 21 15:29:57 sam-laptop gdm[5812]: pam_unix(gdm:session): session closed for user sam
Feb 21 15:58:20 sam-laptop gdm[10986]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Feb 21 15:58:21 sam-laptop gnome-keyring-daemon[12152]: adding removable location: volume_label_Ubuntu_8_04_1_i386 at /media/cdrom0
Feb 21 15:58:27 sam-laptop seahorse-daemon[12358]: Failed to send buffer
Feb 21 15:58:33 sam-laptop seahorse-daemon[12358]: Failed to send buffer
Feb 21 16:02:54 sam-laptop gdm[10986]: pam_unix(gdm:session): session closed for user sam
Feb 21 16:03:13 sam-laptop gdm[12874]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Feb 21 16:03:13 sam-laptop gnome-keyring-daemon[12918]: adding removable location: volume_label_Ubuntu_8_04_1_i386 at /media/cdrom0
Feb 21 16:03:19 sam-laptop seahorse-daemon[13122]: Failed to send buffer
Feb 21 16:03:24 sam-laptop seahorse-daemon[13122]: Failed to send buffer
Feb 21 16:10:22 sam-laptop gdm[12874]: pam_unix(gdm:session): session closed for user sam
Feb 21 16:10:33 sam-laptop gdm[13756]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Feb 21 16:10:33 sam-laptop gnome-keyring-daemon[13798]: adding removable location: volume_label_Ubuntu_8_04_1_i386 at /media/cdrom0
Feb 21 16:10:36 sam-laptop seahorse-daemon[14009]: Failed to send buffer
Feb 21 16:10:36 sam-laptop seahorse-daemon[14009]: Failed to send buffer
Feb 21 16:12:17 sam-laptop gdm[13756]: pam_unix(gdm:session): session closed for user sam
Feb 21 16:12:29 sam-laptop gdm[14323]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Feb 21 16:12:29 sam-laptop gnome-keyring-daemon[14364]: adding removable location: volume_label_Ubuntu_8_04_1_i386 at /media/cdrom0
Feb 21 16:12:31 sam-laptop seahorse-daemon[14571]: Failed to send buffer
Feb 21 16:12:31 sam-laptop seahorse-daemon[14571]: Failed to send buffer
Feb 21 16:17:01 sam-laptop CRON[14993]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 16:17:01 sam-laptop CRON[14993]: pam_unix(cron:session): session closed for user root
Feb 21 17:17:01 sam-laptop CRON[17988]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 17:17:01 sam-laptop CRON[17988]: pam_unix(cron:session): session closed for user root
Feb 21 18:17:01 sam-laptop CRON[20893]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 18:17:01 sam-laptop CRON[20893]: pam_unix(cron:session): session closed for user root
Feb 21 18:54:20 sam-laptop gdm[14323]: pam_unix(gdm:session): session closed for user sam
Feb 21 18:56:08 sam-laptop gdm[22878]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Feb 21 18:56:08 sam-laptop gnome-keyring-daemon[22996]: adding removable location: volume_label_Ubuntu_8_04_1_i386 at /media/cdrom0
Feb 21 18:56:11 sam-laptop seahorse-daemon[23210]: Failed to send buffer
Feb 21 18:56:11 sam-laptop seahorse-daemon[23210]: Failed to send buffer
Feb 21 19:05:03 sam-laptop sudo:      sam : TTY=unknown ; PWD=/home/sam ; USER=root ; COMMAND=/usr/sbin/gdmsetup
Feb 21 19:05:03 sam-laptop sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Feb 21 19:05:03 sam-laptop sudo: pam_unix(sudo:session): session closed for user root
Feb 21 19:06:08 sam-laptop sudo:      sam : TTY=unknown ; PWD=/home/sam ; USER=root ; COMMAND=/usr/bin/hwtest-gtk
Feb 21 19:06:08 sam-laptop sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Feb 21 19:06:08 sam-laptop sudo: pam_unix(sudo:session): session closed for user root

---

