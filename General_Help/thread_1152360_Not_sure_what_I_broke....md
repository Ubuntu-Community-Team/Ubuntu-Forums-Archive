---
title: "Not sure what I broke..."
date: 2009-05-07
forum: General Help
---

### Post by knottshawk on 2009-05-07
I have a new install of Jaunty that I setup using WUBI. I started it up this morning... fixed some settings in mythtv, installed openSSH-server, installed WINE and played around with Gnucash. I restarted it and now it gets to the ubuntu progress bar but when it completes the screen goes blank. The monitor acts like it's asleep and there's no processor activity.

I've SSH'd into it, so I know it's not really frozen, but after getting a list of recent updates I have no clue where to start. I need someone to look at the list at the bottom of the thread and tell me what could cause this and what to do about it.

---

### Post by BslBryan on 2009-05-07
Hello, knottshawk. :-)

Hmm.  How strange.  :-k

Well, have you tried rebooting her again?

Also, Wubi had some problems when I first tried Ubuntu about a year ago, and wanted the easy and painless, fail-safe install route.  Wow, I was wrong! 

To even get the menu bar to load, I had to repeatedly press the space bar, for some reason, and apparently some people had to press Ctrl.  

Ubuntu, because of Wubi, left a terrible taste in my mouth back then!  I'm just glad that I read up quite a bit on it, because I consider myself rather knowledgeable on the subject of Unix, and certainly Ubuntu now. :-)

Anyway, Jaunty's Wubi is a brand-spanking new rewrite from the last code.  This being said, there are bound to be bugs.  If I were you, and you can't get this working, I'd suggest just uninstalling Wubi and downloading the .iso image.

Sorry I haven't been greater help, but do tell me what you decide to do?

Best to you, and good luck. :-)

---

### Post by knottshawk on 2009-05-07
Thanks man... I had it working so I'm not sure it's wubi related at this point. I have ubuntu on other machines (like the one I'm doing this on) with no problems.

Anyone have some diagnostic tips for me?

---

### Post by knottshawk on 2009-05-07
The latest: 

My display is now having issues too (thanks to me screwing with recovery mode)... but when the system appears to be frozen I can SSH into it.

What should I try to fix? The things I tampered with today before restarting (that I can remember) included:

1) disabled desktop effects
2) Set mythtv backend to accept remote connections
3) Installed WINE
4) Installed openSSH-server
5) Played with GnuCash (it was already installed)
6) Installed the updates I was presented (see my dpkg.log a couple posts down)

---

### Post by BslBryan on 2009-05-07
What exactly do you mean by "fix"? :P

---

### Post by knottshawk on 2009-05-07
I mean... somethings broken. I guess I should have said "how do I diagnose this now that I have a terminal?" followed by fixing it. 

A smart chap I've been dealing with suggested it sounded like an x windows problem. I've got no clue where to begin for ANY diagnosis though.

---

### Post by knottshawk on 2009-05-08
Looked at my dpkg.log and here are the changes I made yesterday which, I assume, are causing my problems. I have NO clue where to begin....


2009-05-07 07:05:21 startup archives unpack 
2009-05-07 07:05:33 install libmozjs0d <none> 1.8.1.16+nobinonly-0ubuntu1 
2009-05-07 07:05:33 status half-installed libmozjs0d 1.8.1.16+nobinonly-0ubuntu1 
2009-05-07 07:05:33 status unpacked libmozjs0d 1.8.1.16+nobinonly-0ubuntu1 
2009-05-07 07:05:33 status unpacked libmozjs0d 1.8.1.16+nobinonly-0ubuntu1 
2009-05-07 07:05:33 install gxine <none> 0.5.903-4ubuntu1 
2009-05-07 07:05:33 status half-installed gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:33 install gxine <none> 0.5.903-4ubuntu1 
2009-05-07 07:05:33 status half-installed gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:33 status triggers-pending man-db 2.5.5-1build1 
2009-05-07 07:05:33 status half-installed gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:33 status unpacked gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:33 status unpacked gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:33 trigproc man-db 2.5.5-1build1 2.5.5-1build1 
2009-05-07 07:05:33 status half-configured man-db 2.5.5-1build1 
2009-05-07 07:05:35 status installed man-db 2.5.5-1build1 
2009-05-07 07:05:35 startup packages configure 
2009-05-07 07:05:35 configure libmozjs0d 1.8.1.16+nobinonly-0ubuntu1 1.8.1.16+n$ 
2009-05-07 07:05:35 status unpacked libmozjs0d 1.8.1.16+nobinonly-0ubuntu1 
2009-05-07 07:05:35 status half-configured libmozjs0d 1.8.1.16+nobinonly-0ubunt$ 
2009-05-07 07:05:35 status installed libmozjs0d 1.8.1.16+nobinonly-0ubuntu1 
2009-05-07 07:05:36 status triggers-pending libc6 2.9-4ubuntu6 
2009-05-07 07:05:36 configure gxine 0.5.903-4ubuntu1 0.5.903-4ubuntu1 
2009-05-07 07:05:36 status unpacked gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:36 status unpacked gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:36 status unpacked gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:36 status unpacked gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:36 status unpacked gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:36 status unpacked gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:36 status unpacked gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:36 status unpacked gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:36 status half-configured gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:38 status installed gxine 0.5.903-4ubuntu1 
2009-05-07 07:05:38 trigproc libc6 2.9-4ubuntu6 2.9-4ubuntu6 
2009-05-07 07:05:38 status half-configured libc6 2.9-4ubuntu6 
2009-05-07 07:05:38 status installed libc6 2.9-4ubuntu6 
2009-05-07 07:13:51 startup archives install 
2009-05-07 07:13:51 install libdvdcss2 <none> 1.2.10-0.2medibuntu1 
2009-05-07 07:13:51 status half-installed libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:13:51 status unpacked libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:13:51 status unpacked libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:13:51 configure libdvdcss2 1.2.10-0.2medibuntu1 1.2.10-0.2medibun$ 
2009-05-07 07:13:51 status unpacked libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:13:51 status half-configured libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:13:51 status installed libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:13:51 status half-configured libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:13:51 status installed libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:13:51 status triggers-pending libc6 2.9-4ubuntu6 
2009-05-07 07:13:51 trigproc libc6 2.9-4ubuntu6 2.9-4ubuntu6 
2009-05-07 07:13:51 status half-configured libc6 2.9-4ubuntu6 
2009-05-07 07:13:51 status installed libc6 2.9-4ubuntu6 
2009-05-07 07:14:53 startup archives install 
2009-05-07 07:14:54 upgrade libdvdcss2 1.2.10-0.2medibuntu1 1.2.10-0.2medibuntu1 
2009-05-07 07:14:54 status half-configured libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:14:54 status unpacked libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:14:54 status half-installed libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:14:54 status half-installed libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:14:54 status unpacked libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:14:54 status unpacked libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:14:54 configure libdvdcss2 1.2.10-0.2medibuntu1 1.2.10-0.2medibun$ 
2009-05-07 07:14:54 status unpacked libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:14:54 status half-configured libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:14:54 status installed libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:14:54 status triggers-pending libc6 2.9-4ubuntu6 
2009-05-07 07:14:54 status installed libdvdcss2 1.2.10-0.2medibuntu1 
2009-05-07 07:14:54 status triggers-pending libc6 2.9-4ubuntu6 
2009-05-07 07:14:54 trigproc libc6 2.9-4ubuntu6 2.9-4ubuntu6 
2009-05-07 07:14:54 status half-configured libc6 2.9-4ubuntu6 
2009-05-07 07:14:54 status installed libc6 2.9-4ubuntu6 
2009-05-07 10:48:48 startup archives unpack 
2009-05-07 10:48:59 install openssh-server <none> 1:5.1p1-5ubuntu1 
2009-05-07 10:48:59 status half-installed openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 10:49:00 status triggers-pending ufw 0.27-0ubuntu2 
2009-05-07 10:49:00 status half-installed openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 10:49:00 status triggers-pending man-db 2.5.5-1build1 
2009-05-07 10:49:00 status half-installed openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 10:49:00 status unpacked openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 10:49:01 status unpacked openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 10:49:01 trigproc ufw 0.27-0ubuntu2 0.27-0ubuntu2 
2009-05-07 10:49:01 status half-configured ufw 0.27-0ubuntu2 
2009-05-07 10:49:02 status installed ufw 0.27-0ubuntu2 
2009-05-07 10:49:02 trigproc man-db 2.5.5-1build1 2.5.5-1build1 
2009-05-07 10:49:02 status half-configured man-db 2.5.5-1build1 
2009-05-07 10:49:02 trigproc man-db 2.5.5-1build1 2.5.5-1build1 
2009-05-07 10:49:02 status half-configured man-db 2.5.5-1build1 
2009-05-07 10:49:03 status installed man-db 2.5.5-1build1 
2009-05-07 10:49:04 startup packages configure 
2009-05-07 10:49:04 configure openssh-server 1:5.1p1-5ubuntu1 1:5.1p1-5ubuntu1 
2009-05-07 10:49:04 status unpacked openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 10:49:04 status unpacked openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 10:49:04 status unpacked openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 10:49:04 status unpacked openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 10:49:04 status unpacked openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 10:49:04 status unpacked openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 10:49:04 status half-configured openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 10:49:09 status installed openssh-server 1:5.1p1-5ubuntu1 
2009-05-07 15:11:01 startup archives unpack 
2009-05-07 15:11:10 install lib32nss-mdns <none> 0.10-3ubuntu2 
2009-05-07 15:11:10 status half-installed lib32nss-mdns 0.10-3ubuntu2 
2009-05-07 15:11:11 status unpacked lib32nss-mdns 0.10-3ubuntu2 
2009-05-07 15:11:11 status unpacked lib32nss-mdns 0.10-3ubuntu2 
2009-05-07 15:11:11 install wine <none> 1.0.1-0ubuntu6 
2009-05-07 15:11:11 status unpacked lib32nss-mdns 0.10-3ubuntu2 
2009-05-07 15:11:11 install wine <none> 1.0.1-0ubuntu6 
2009-05-07 15:11:11 status half-installed wine 1.0.1-0ubuntu6 
2009-05-07 15:11:12 status triggers-pending man-db 2.5.5-1build1 
2009-05-07 15:11:12 status half-installed wine 1.0.1-0ubuntu6 
2009-05-07 15:11:15 status unpacked wine 1.0.1-0ubuntu6 
2009-05-07 15:11:16 status unpacked wine 1.0.1-0ubuntu6 
2009-05-07 15:11:16 install wine-gecko <none> 0.1.0-0ubuntu1 
2009-05-07 15:11:16 status half-installed wine-gecko 0.1.0-0ubuntu1 
2009-05-07 15:11:16 status unpacked wine-gecko 0.1.0-0ubuntu1 
2009-05-07 15:11:16 status unpacked wine-gecko 0.1.0-0ubuntu1 
2009-05-07 15:11:16 install winbind <none> 2:3.3.2-1ubuntu3 
2009-05-07 15:11:16 status half-installed winbind 2:3.3.2-1ubuntu3 
2009-05-07 15:11:16 status half-installed winbind 2:3.3.2-1ubuntu3 
2009-05-07 15:11:16 status unpacked winbind 2:3.3.2-1ubuntu3 
2009-05-07 15:11:16 status unpacked winbind 2:3.3.2-1ubuntu3 
2009-05-07 15:11:16 trigproc man-db 2.5.5-1build1 2.5.5-1build1 
2009-05-07 15:11:16 status half-configured man-db 2.5.5-1build1 
2009-05-07 15:11:17 status installed man-db 2.5.5-1build1 
2009-05-07 15:11:16 status half-configured man-db 2.5.5-1build1 
2009-05-07 15:11:17 status installed man-db 2.5.5-1build1 
2009-05-07 15:11:18 startup packages configure 
2009-05-07 15:11:18 configure lib32nss-mdns 0.10-3ubuntu2 0.10-3ubuntu2 
2009-05-07 15:11:18 status unpacked lib32nss-mdns 0.10-3ubuntu2 
2009-05-07 15:11:18 status half-configured lib32nss-mdns 0.10-3ubuntu2 
2009-05-07 15:11:18 status installed lib32nss-mdns 0.10-3ubuntu2 
2009-05-07 15:11:18 status triggers-pending libc6 2.9-4ubuntu6 
2009-05-07 15:11:18 configure wine 1.0.1-0ubuntu6 1.0.1-0ubuntu6 
2009-05-07 15:11:18 status unpacked wine 1.0.1-0ubuntu6 
2009-05-07 15:11:18 status unpacked wine 1.0.1-0ubuntu6 
2009-05-07 15:11:18 status unpacked wine 1.0.1-0ubuntu6 
2009-05-07 15:11:18 status half-configured wine 1.0.1-0ubuntu6 
2009-05-07 15:11:19 status installed wine 1.0.1-0ubuntu6 
2009-05-07 15:11:19 configure wine-gecko 0.1.0-0ubuntu1 0.1.0-0ubuntu1 
2009-05-07 15:11:19 status unpacked wine-gecko 0.1.0-0ubuntu1 
2009-05-07 15:11:19 status half-configured wine-gecko 0.1.0-0ubuntu1 
2009-05-07 15:11:19 status installed wine-gecko 0.1.0-0ubuntu1 
2009-05-07 15:11:19 configure winbind 2:3.3.2-1ubuntu3 2:3.3.2-1ubuntu3 
2009-05-07 15:11:19 status installed wine-gecko 0.1.0-0ubuntu1 
2009-05-07 15:11:19 configure winbind 2:3.3.2-1ubuntu3 2:3.3.2-1ubuntu3 
2009-05-07 15:11:19 status unpacked winbind 2:3.3.2-1ubuntu3 
2009-05-07 15:11:19 status unpacked winbind 2:3.3.2-1ubuntu3 
2009-05-07 15:11:19 status unpacked winbind 2:3.3.2-1ubuntu3 
2009-05-07 15:11:19 status unpacked winbind 2:3.3.2-1ubuntu3 
2009-05-07 15:11:19 status half-configured winbind 2:3.3.2-1ubuntu3 
2009-05-07 15:11:20 status installed winbind 2:3.3.2-1ubuntu3 
2009-05-07 15:11:20 trigproc libc6 2.9-4ubuntu6 2.9-4ubuntu6 
2009-05-07 15:11:20 status half-configured libc6 2.9-4ubuntu6 
2009-05-07 15:11:20 status installed libc6 2.9-4ubuntu6 
2009-05-07 15:31:39 startup archives unpack 
2009-05-07 15:31:49 upgrade gnome-applets-data 2.26.0-0ubuntu4 2.26.1-0ubuntu1 
2009-05-07 15:31:49 status half-configured gnome-applets-data 2.26.0-0ubuntu4 
2009-05-07 15:31:51 status triggers-pending python-support 0.8.7ubuntu4 
2009-05-07 15:31:51 status unpacked gnome-applets-data 2.26.0-0ubuntu4 
2009-05-07 15:31:51 status half-installed gnome-applets-data 2.26.0-0ubuntu4 
2009-05-07 15:31:55 status half-installed gnome-applets-data 2.26.0-0ubuntu4 
2009-05-07 15:31:56 status unpacked gnome-applets-data 2.26.1-0ubuntu1 
2009-05-07 15:31:55 status half-installed gnome-applets-data 2.26.0-0ubuntu4 
2009-05-07 15:31:56 status unpacked gnome-applets-data 2.26.1-0ubuntu1 
2009-05-07 15:31:56 status unpacked gnome-applets-data 2.26.1-0ubuntu1 
2009-05-07 15:31:56 upgrade gnome-applets 2.26.0-0ubuntu4 2.26.1-0ubuntu1 
2009-05-07 15:31:56 status half-configured gnome-applets 2.26.0-0ubuntu4 
2009-05-07 15:31:56 status unpacked gnome-applets 2.26.0-0ubuntu4 
2009-05-07 15:31:56 status half-installed gnome-applets 2.26.0-0ubuntu4 
2009-05-07 15:31:56 status triggers-pending man-db 2.5.5-1build1 
2009-05-07 15:31:56 status half-installed gnome-applets 2.26.0-0ubuntu4 
2009-05-07 15:31:56 status half-installed gnome-applets 2.26.0-0ubuntu4 
2009-05-07 15:31:57 status unpacked gnome-applets 2.26.1-0ubuntu1 
2009-05-07 15:31:57 status unpacked gnome-applets 2.26.1-0ubuntu1 
2009-05-07 15:31:57 upgrade libnautilus-extension1 1:2.26.2-0ubuntu1 1:2.26.2-0$ 
2009-05-07 15:31:57 status half-configured libnautilus-extension1 1:2.26.2-0ubu$ 
2009-05-07 15:31:57 status unpacked libnautilus-extension1 1:2.26.2-0ubuntu1 
2009-05-07 15:31:57 status half-installed libnautilus-extension1 1:2.26.2-0ubun$ 
2009-05-07 15:31:57 status half-installed libnautilus-extension1 1:2.26.2-0ubun$ 
2009-05-07 15:31:58 status unpacked libnautilus-extension1 1:2.26.2-0ubuntu2 
2009-05-07 15:31:58 status unpacked libnautilus-extension1 1:2.26.2-0ubuntu2 
2009-05-07 15:31:58 status unpacked libnautilus-extension1 1:2.26.2-0ubuntu2 
2009-05-07 15:31:58 status unpacked libnautilus-extension1 1:2.26.2-0ubuntu2 
2009-05-07 15:31:58 upgrade libbrasero-media0 2.26.0-0ubuntu3 2.26.1-0ubuntu1 
2009-05-07 15:31:58 status half-configured libbrasero-media0 2.26.0-0ubuntu3 
2009-05-07 15:31:58 status unpacked libbrasero-media0 2.26.0-0ubuntu3 
2009-05-07 15:31:58 status half-installed libbrasero-media0 2.26.0-0ubuntu3 
2009-05-07 15:31:59 status half-installed libbrasero-media0 2.26.0-0ubuntu3 
2009-05-07 15:31:59 status unpacked libbrasero-media0 2.26.1-0ubuntu1 
2009-05-07 15:31:59 status unpacked libbrasero-media0 2.26.1-0ubuntu1 
2009-05-07 15:31:59 upgrade brasero 2.26.0-0ubuntu3 2.26.1-0ubuntu1 
2009-05-07 15:31:59 status half-configured brasero 2.26.0-0ubuntu3 
2009-05-07 15:32:01 status unpacked brasero 2.26.0-0ubuntu3 
2009-05-07 15:32:01 status half-installed brasero 2.26.0-0ubuntu3 
2009-05-07 15:32:01 status half-installed brasero 2.26.0-0ubuntu3 
2009-05-07 15:32:01 status triggers-pending shared-mime-info 0.60-1 
2009-05-07 15:32:01 status half-installed brasero 2.26.0-0ubuntu3 
2009-05-07 15:32:01 status half-installed brasero 2.26.0-0ubuntu3 
2009-05-07 15:32:01 status unpacked brasero 2.26.1-0ubuntu1 
2009-05-07 15:32:01 status unpacked brasero 2.26.1-0ubuntu1 
2009-05-07 15:32:01 status unpacked brasero 2.26.1-0ubuntu1 
2009-05-07 15:32:01 status unpacked brasero 2.26.1-0ubuntu1 
2009-05-07 15:32:01 upgrade gnome-app-install 0.5.24-0ubuntu1 0.5.24-0ubuntu1.1 
2009-05-07 15:32:01 status half-configured gnome-app-install 0.5.24-0ubuntu1 
2009-05-07 15:32:04 status unpacked gnome-app-install 0.5.24-0ubuntu1 
2009-05-07 15:32:04 status half-installed gnome-app-install 0.5.24-0ubuntu1 
2009-05-07 15:32:04 status half-installed gnome-app-install 0.5.24-0ubuntu1 
2009-05-07 15:32:04 status half-installed gnome-app-install 0.5.24-0ubuntu1 
2009-05-07 15:32:04 status unpacked gnome-app-install 0.5.24-0ubuntu1.1 
2009-05-07 15:32:04 status unpacked gnome-app-install 0.5.24-0ubuntu1.1 
2009-05-07 15:32:04 upgrade libmodplug0c2 1:0.8.4-3ubuntu1 1:0.8.4-3ubuntu1.1 
2009-05-07 15:32:04 status half-configured libmodplug0c2 1:0.8.4-3ubuntu1 
2009-05-07 15:32:04 status unpacked libmodplug0c2 1:0.8.4-3ubuntu1 
2009-05-07 15:32:04 status half-installed libmodplug0c2 1:0.8.4-3ubuntu1 
2009-05-07 15:32:04 status half-installed libmodplug0c2 1:0.8.4-3ubuntu1 
2009-05-07 15:32:04 status unpacked libmodplug0c2 1:0.8.4-3ubuntu1.1 
2009-05-07 15:32:04 status unpacked libmodplug0c2 1:0.8.4-3ubuntu1.1 
2009-05-07 15:32:04 upgrade libmpfr1ldbl 2.4.0-1ubuntu3 2.4.0-1ubuntu3.1 
2009-05-07 15:32:04 status half-configured libmpfr1ldbl 2.4.0-1ubuntu3 
2009-05-07 15:32:04 upgrade libmpfr1ldbl 2.4.0-1ubuntu3 2.4.0-1ubuntu3.1 
2009-05-07 15:32:04 status half-configured libmpfr1ldbl 2.4.0-1ubuntu3 
2009-05-07 15:32:04 status unpacked libmpfr1ldbl 2.4.0-1ubuntu3 
2009-05-07 15:32:04 status half-installed libmpfr1ldbl 2.4.0-1ubuntu3 
2009-05-07 15:32:04 status half-installed libmpfr1ldbl 2.4.0-1ubuntu3 
2009-05-07 15:32:05 status unpacked libmpfr1ldbl 2.4.0-1ubuntu3.1 
2009-05-07 15:32:05 status unpacked libmpfr1ldbl 2.4.0-1ubuntu3.1 
2009-05-07 15:32:05 upgrade libsoup2.4-1 2.26.0-0ubuntu2 2.26.0-0ubuntu3 
2009-05-07 15:32:05 status half-configured libsoup2.4-1 2.26.0-0ubuntu2 
2009-05-07 15:32:05 status unpacked libsoup2.4-1 2.26.0-0ubuntu2 
2009-05-07 15:32:05 status half-installed libsoup2.4-1 2.26.0-0ubuntu2 
2009-05-07 15:32:05 status half-installed libsoup2.4-1 2.26.0-0ubuntu2 
2009-05-07 15:32:05 status unpacked libsoup2.4-1 2.26.0-0ubuntu3 
2009-05-07 15:32:05 status unpacked libsoup2.4-1 2.26.0-0ubuntu3 
2009-05-07 15:32:05 upgrade libsoup-gnome2.4-1 2.26.0-0ubuntu2 2.26.0-0ubuntu3 
2009-05-07 15:32:05 status half-configured libsoup-gnome2.4-1 2.26.0-0ubuntu2 
2009-05-07 15:32:05 status unpacked libsoup-gnome2.4-1 2.26.0-0ubuntu2 
2009-05-07 15:32:05 status half-installed libsoup-gnome2.4-1 2.26.0-0ubuntu2 
2009-05-07 15:32:05 status half-installed libsoup-gnome2.4-1 2.26.0-0ubuntu2 
2009-05-07 15:32:05 status half-installed libsoup-gnome2.4-1 2.26.0-0ubuntu2 
2009-05-07 15:32:05 status half-installed libsoup-gnome2.4-1 2.26.0-0ubuntu2 
2009-05-07 15:32:05 status unpacked libsoup-gnome2.4-1 2.26.0-0ubuntu3 
2009-05-07 15:32:05 status unpacked libsoup-gnome2.4-1 2.26.0-0ubuntu3 
2009-05-07 15:32:05 upgrade nautilus-data 1:2.26.2-0ubuntu1 1:2.26.2-0ubuntu2 
2009-05-07 15:32:05 status half-configured nautilus-data 1:2.26.2-0ubuntu1 
2009-05-07 15:32:07 status unpacked nautilus-data 1:2.26.2-0ubuntu1 
2009-05-07 15:32:07 status half-installed nautilus-data 1:2.26.2-0ubuntu1 
2009-05-07 15:32:07 status half-installed nautilus-data 1:2.26.2-0ubuntu1 
2009-05-07 15:32:07 status half-installed nautilus-data 1:2.26.2-0ubuntu1 
2009-05-07 15:32:07 status unpacked nautilus-data 1:2.26.2-0ubuntu2 
2009-05-07 15:32:07 status unpacked nautilus-data 1:2.26.2-0ubuntu2 
2009-05-07 15:32:07 upgrade nautilus 1:2.26.2-0ubuntu1 1:2.26.2-0ubuntu2 
2009-05-07 15:32:07 status half-configured nautilus 1:2.26.2-0ubuntu1 
2009-05-07 15:32:07 status unpacked nautilus 1:2.26.2-0ubuntu1 
2009-05-07 15:32:07 status half-installed nautilus 1:2.26.2-0ubuntu1 
2009-05-07 15:32:08 status half-installed nautilus 1:2.26.2-0ubuntu1 
2009-05-07 15:32:08 status half-installed nautilus 1:2.26.2-0ubuntu1 
2009-05-07 15:32:08 status unpacked nautilus 1:2.26.2-0ubuntu2 
2009-05-07 15:32:08 status half-installed nautilus 1:2.26.2-0ubuntu1 
2009-05-07 15:32:08 status unpacked nautilus 1:2.26.2-0ubuntu2 
2009-05-07 15:32:08 status unpacked nautilus 1:2.26.2-0ubuntu2 
2009-05-07 15:32:08 upgrade splix 2.0.0-0.1ubuntu3 2.0.0-0.1ubuntu3.1 
2009-05-07 15:32:08 status half-configured splix 2.0.0-0.1ubuntu3 
2009-05-07 15:32:08 status unpacked splix 2.0.0-0.1ubuntu3 
2009-05-07 15:32:08 status half-installed splix 2.0.0-0.1ubuntu3 
2009-05-07 15:32:08 status half-installed splix 2.0.0-0.1ubuntu3 
2009-05-07 15:32:08 status unpacked splix 2.0.0-0.1ubuntu3.1 
2009-05-07 15:32:08 status unpacked splix 2.0.0-0.1ubuntu3.1 
2009-05-07 15:32:08 upgrade gnome-settings-daemon 2.26.0-0ubuntu4 2.26.1-0ubunt$ 
2009-05-07 15:32:08 status half-configured gnome-settings-daemon 2.26.0-0ubuntu4 
2009-05-07 15:32:10 status unpacked gnome-settings-daemon 2.26.0-0ubuntu4 
2009-05-07 15:32:10 status half-installed gnome-settings-daemon 2.26.0-0ubuntu4 
2009-05-07 15:32:10 status half-installed gnome-settings-daemon 2.26.0-0ubuntu4 
2009-05-07 15:32:11 status unpacked gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:32:11 status unpacked gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:32:11 install libamrnb3 <none> 7.0.0.2-0.1medibuntu1 
2009-05-07 15:32:11 status half-installed libamrnb3 7.0.0.2-0.1medibuntu1 
2009-05-07 15:32:11 install libamrnb3 <none> 7.0.0.2-0.1medibuntu1 
2009-05-07 15:32:11 status half-installed libamrnb3 7.0.0.2-0.1medibuntu1 
2009-05-07 15:32:11 status unpacked libamrnb3 7.0.0.2-0.1medibuntu1 
2009-05-07 15:32:11 status unpacked libamrnb3 7.0.0.2-0.1medibuntu1 
2009-05-07 15:32:11 install libamrwb3 <none> 7.0.0.3-0.0medibuntu1 
2009-05-07 15:32:11 status half-installed libamrwb3 7.0.0.3-0.0medibuntu1 
2009-05-07 15:32:11 status unpacked libamrwb3 7.0.0.3-0.0medibuntu1 
2009-05-07 15:32:11 status unpacked libamrwb3 7.0.0.3-0.0medibuntu1 
2009-05-07 15:32:11 upgrade mplayer 2:1.0~rc2-0ubuntu19 2:1.0~rc2-0ubuntu19+med$ 
2009-05-07 15:32:11 status half-configured mplayer 2:1.0~rc2-0ubuntu19 
2009-05-07 15:32:11 status unpacked mplayer 2:1.0~rc2-0ubuntu19 
2009-05-07 15:32:11 status half-installed mplayer 2:1.0~rc2-0ubuntu19 
2009-05-07 15:32:12 status half-installed mplayer 2:1.0~rc2-0ubuntu19 
2009-05-07 15:32:12 status half-installed mplayer 2:1.0~rc2-0ubuntu19 
2009-05-07 15:32:13 status unpacked mplayer 2:1.0~rc2-0ubuntu19+medibuntu1 
2009-05-07 15:32:13 status unpacked mplayer 2:1.0~rc2-0ubuntu19+medibuntu1 
2009-05-07 15:32:13 trigproc python-support 0.8.7ubuntu4 0.8.7ubuntu4 
2009-05-07 15:32:13 status half-configured python-support 0.8.7ubuntu4 
2009-05-07 15:32:16 status installed python-support 0.8.7ubuntu4 
2009-05-07 15:32:13 status half-configured python-support 0.8.7ubuntu4 
2009-05-07 15:32:16 status installed python-support 0.8.7ubuntu4 
2009-05-07 15:32:16 trigproc man-db 2.5.5-1build1 2.5.5-1build1 
2009-05-07 15:32:16 status half-configured man-db 2.5.5-1build1 
2009-05-07 15:32:17 status installed man-db 2.5.5-1build1 
2009-05-07 15:32:17 trigproc shared-mime-info 0.60-1 0.60-1 
2009-05-07 15:32:17 status half-configured shared-mime-info 0.60-1 
2009-05-07 15:32:18 status installed shared-mime-info 0.60-1 
2009-05-07 15:32:19 startup packages configure 
2009-05-07 15:32:19 configure gnome-applets-data 2.26.1-0ubuntu1 2.26.1-0ubuntu1 
2009-05-07 15:32:19 status unpacked gnome-applets-data 2.26.1-0ubuntu1 
2009-05-07 15:32:19 status unpacked gnome-applets-data 2.26.1-0ubuntu1 
2009-05-07 15:32:19 status unpacked gnome-applets-data 2.26.1-0ubuntu1 
2009-05-07 15:32:19 status half-configured gnome-applets-data 2.26.1-0ubuntu1 
2009-05-07 15:32:20 status installed gnome-applets-data 2.26.1-0ubuntu1 
2009-05-07 15:32:20 status triggers-pending python-support 0.8.7ubuntu4 
2009-05-07 15:32:20 configure gnome-applets 2.26.1-0ubuntu1 2.26.1-0ubuntu1 
2009-05-07 15:32:20 status unpacked gnome-applets 2.26.1-0ubuntu1 
2009-05-07 15:32:20 status half-configured gnome-applets 2.26.1-0ubuntu1 
2009-05-07 15:32:20 status unpacked gnome-applets 2.26.1-0ubuntu1 
2009-05-07 15:32:20 status half-configured gnome-applets 2.26.1-0ubuntu1 
2009-05-07 15:32:22 status installed gnome-applets 2.26.1-0ubuntu1 
2009-05-07 15:32:22 configure libnautilus-extension1 1:2.26.2-0ubuntu2 1:2.26.2$ 
2009-05-07 15:32:22 status unpacked libnautilus-extension1 1:2.26.2-0ubuntu2 
2009-05-07 15:32:22 status half-configured libnautilus-extension1 1:2.26.2-0ubu$ 
2009-05-07 15:32:22 status installed libnautilus-extension1 1:2.26.2-0ubuntu2 
2009-05-07 15:32:22 status triggers-pending libc6 2.9-4ubuntu6 
2009-05-07 15:32:22 configure libbrasero-media0 2.26.1-0ubuntu1 2.26.1-0ubuntu1 
2009-05-07 15:32:22 status unpacked libbrasero-media0 2.26.1-0ubuntu1 
2009-05-07 15:32:22 status half-configured libbrasero-media0 2.26.1-0ubuntu1 
2009-05-07 15:32:22 status installed libbrasero-media0 2.26.1-0ubuntu1 
2009-05-07 15:32:22 configure brasero 2.26.1-0ubuntu1 2.26.1-0ubuntu1 
2009-05-07 15:32:22 status unpacked brasero 2.26.1-0ubuntu1 
2009-05-07 15:32:22 status half-configured brasero 2.26.1-0ubuntu1 
2009-05-07 15:32:23 status installed brasero 2.26.1-0ubuntu1 
2009-05-07 15:32:23 configure gnome-app-install 0.5.24-0ubuntu1.1 0.5.24-0ubunt$ 
2009-05-07 15:32:23 status unpacked gnome-app-install 0.5.24-0ubuntu1.1 
2009-05-07 15:32:23 status half-configured gnome-app-install 0.5.24-0ubuntu1.1 
2009-05-07 15:32:23 status unpacked gnome-app-install 0.5.24-0ubuntu1.1 
2009-05-07 15:32:23 status half-configured gnome-app-install 0.5.24-0ubuntu1.1 
2009-05-07 15:32:45 status installed gnome-app-install 0.5.24-0ubuntu1.1 
2009-05-07 15:32:45 configure libmodplug0c2 1:0.8.4-3ubuntu1.1 1:0.8.4-3ubuntu1$ 
2009-05-07 15:32:45 status unpacked libmodplug0c2 1:0.8.4-3ubuntu1.1 
2009-05-07 15:32:45 status half-configured libmodplug0c2 1:0.8.4-3ubuntu1.1 
2009-05-07 15:32:45 status installed libmodplug0c2 1:0.8.4-3ubuntu1.1 
2009-05-07 15:32:45 configure libmpfr1ldbl 2.4.0-1ubuntu3.1 2.4.0-1ubuntu3.1 
2009-05-07 15:32:45 status unpacked libmpfr1ldbl 2.4.0-1ubuntu3.1 
2009-05-07 15:32:45 status half-configured libmpfr1ldbl 2.4.0-1ubuntu3.1 
2009-05-07 15:32:45 status installed libmpfr1ldbl 2.4.0-1ubuntu3.1 
2009-05-07 15:32:45 configure libsoup2.4-1 2.26.0-0ubuntu3 2.26.0-0ubuntu3 
2009-05-07 15:32:45 status unpacked libsoup2.4-1 2.26.0-0ubuntu3 
2009-05-07 15:32:45 status half-configured libsoup2.4-1 2.26.0-0ubuntu3 
2009-05-07 15:32:45 status installed libsoup2.4-1 2.26.0-0ubuntu3 
2009-05-07 15:32:45 configure libsoup-gnome2.4-1 2.26.0-0ubuntu3 2.26.0-0ubuntu3 
2009-05-07 15:32:45 status unpacked libsoup-gnome2.4-1 2.26.0-0ubuntu3 
2009-05-07 15:32:45 status half-configured libsoup-gnome2.4-1 2.26.0-0ubuntu3 
2009-05-07 15:32:45 status installed libsoup-gnome2.4-1 2.26.0-0ubuntu3 
2009-05-07 15:32:45 status half-configured libsoup-gnome2.4-1 2.26.0-0ubuntu3 
2009-05-07 15:32:45 status installed libsoup-gnome2.4-1 2.26.0-0ubuntu3 
2009-05-07 15:32:45 configure nautilus-data 1:2.26.2-0ubuntu2 1:2.26.2-0ubuntu2 
2009-05-07 15:32:45 status unpacked nautilus-data 1:2.26.2-0ubuntu2 
2009-05-07 15:32:45 status half-configured nautilus-data 1:2.26.2-0ubuntu2 
2009-05-07 15:32:45 status installed nautilus-data 1:2.26.2-0ubuntu2 
2009-05-07 15:32:45 configure nautilus 1:2.26.2-0ubuntu2 1:2.26.2-0ubuntu2 
2009-05-07 15:32:45 status unpacked nautilus 1:2.26.2-0ubuntu2 
2009-05-07 15:32:45 status half-configured nautilus 1:2.26.2-0ubuntu2 
2009-05-07 15:32:45 status installed nautilus 1:2.26.2-0ubuntu2 
2009-05-07 15:32:45 configure splix 2.0.0-0.1ubuntu3.1 2.0.0-0.1ubuntu3.1 
2009-05-07 15:32:45 status unpacked splix 2.0.0-0.1ubuntu3.1 
2009-05-07 15:32:45 status half-configured splix 2.0.0-0.1ubuntu3.1 
2009-05-07 15:33:02 status installed splix 2.0.0-0.1ubuntu3.1 
2009-05-07 15:33:02 configure gnome-settings-daemon 2.26.1-0ubuntu1 2.26.1-0ubu$ 
2009-05-07 15:33:02 status unpacked gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:33:02 status unpacked gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:33:02 status unpacked gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:33:02 status unpacked gnome-settings-daemon 2.26.1-0ubuntu1
2009-05-07 15:33:02 status unpacked gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:33:02 status unpacked gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:33:02 status unpacked gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:33:02 status unpacked gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:33:02 status unpacked gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:33:02 status unpacked gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:33:02 status half-configured gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:33:02 status installed gnome-settings-daemon 2.26.1-0ubuntu1 
2009-05-07 15:33:02 configure libamrnb3 7.0.0.2-0.1medibuntu1 7.0.0.2-0.1medibu$ 
2009-05-07 15:33:02 status unpacked libamrnb3 7.0.0.2-0.1medibuntu1 
2009-05-07 15:33:02 status half-configured libamrnb3 7.0.0.2-0.1medibuntu1 
2009-05-07 15:33:02 status installed libamrnb3 7.0.0.2-0.1medibuntu1 
2009-05-07 15:33:02 configure libamrwb3 7.0.0.3-0.0medibuntu1 7.0.0.3-0.0medibu$ 
2009-05-07 15:33:02 status unpacked libamrwb3 7.0.0.3-0.0medibuntu1 
2009-05-07 15:33:02 status half-configured libamrwb3 7.0.0.3-0.0medibuntu1 
2009-05-07 15:33:02 status installed libamrwb3 7.0.0.3-0.0medibuntu1 
2009-05-07 15:33:02 configure mplayer 2:1.0~rc2-0ubuntu19+medibuntu1 2:1.0~rc2-$ 
2009-05-07 15:33:02 status unpacked mplayer 2:1.0~rc2-0ubuntu19+medibuntu1 
2009-05-07 15:33:02 status unpacked mplayer 2:1.0~rc2-0ubuntu19+medibuntu1 
2009-05-07 15:33:02 status unpacked mplayer 2:1.0~rc2-0ubuntu19+medibuntu1 
2009-05-07 15:33:02 status unpacked mplayer 2:1.0~rc2-0ubuntu19+medibuntu1 
2009-05-07 15:33:02 status unpacked mplayer 2:1.0~rc2-0ubuntu19+medibuntu1 
2009-05-07 15:33:02 status unpacked mplayer 2:1.0~rc2-0ubuntu19+medibuntu1 
2009-05-07 15:33:02 status half-configured mplayer 2:1.0~rc2-0ubuntu19+medibunt$ 
2009-05-07 15:33:03 status installed mplayer 2:1.0~rc2-0ubuntu19+medibuntu1 
2009-05-07 15:33:03 trigproc python-support 0.8.7ubuntu4 0.8.7ubuntu4 
2009-05-07 15:33:03 status half-configured python-support 0.8.7ubuntu4 
2009-05-07 15:33:03 status installed python-support 0.8.7ubuntu4 
2009-05-07 15:33:03 trigproc libc6 2.9-4ubuntu6 2.9-4ubuntu6 
2009-05-07 15:33:03 status half-configured libc6 2.9-4ubuntu6 
2009-05-07 15:33:03 status installed libc6 2.9-4ubuntu6

---

### Post by knottshawk on 2009-05-08
I'm wondering if, at this point, I should just SSH in and back it up and reinstall. I'm getting no ideas and I'm stuck.

---

### Post by BslBryan on 2009-05-08
While it can be fun after you've fixed a problem, getting stuck in one place with no guidance at all can be very frustrating.

It's obviously up to you, but I will say that it would probably be a lot easier to reinstall.

Best to you, mate, and good luck. :-)

---

### Post by knottshawk on 2009-05-08
What's .xsession-errors file for? It's got a lot of information in it. Is that relevant?

---

### Post by BslBryan on 2009-05-08
It might be.  It would take forever to figure out what caused the problem, though, as .xsessions-errors stores errors that occur when a graphical user session is started with X Windows.

---

### Post by knottshawk on 2009-05-08
It doesn't seem that complicated if a fella knew what he was doing.. Here it is:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. $
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have n$
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges$
GNOME_KEYRING_SOCKET=/tmp/keyring-WQQQRf/socket
SSH_AUTH_SOCK=/tmp/keyring-WQQQRf/socket.ssh
Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Checking screen 1x-session-manager[4127]: WARNING: Application 'gnome-wm.desktop' failed to register before ti$
Comparing resolution (1920x1200) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: not present.
Checking for FBConfig: present.
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present.
** (gnome-panel:4348): DEBUG: Adding applet 0.
** (gnome-panel:4348): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:4348): DEBUG: Adding applet 1.
** (gnome-panel:4348): DEBUG: Adding applet 2.
** (nm-applet:4383): DEBUG: applet_common_device_state_changed
** (gnome-panel:4348): DEBUG: Adding applet 3.
** (gnome-panel:4348): DEBUG: Adding applet 4.

(gnome-panel:4348): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and h$
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
(gnome-panel:4348): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and h$
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
** (gnome-panel:4348): DEBUG: Adding applet 5.
** (gnome-panel:4348): DEBUG: Adding applet 6.
** (gnome-panel:4348): DEBUG: Adding applet 7.
** (gnome-panel:4348): DEBUG: Adding applet 8.
I/O warning : failed to load external entity "/home/norris/.compiz/session/10661e3240561c104a12417013362848460$
Starting gtk-window-decorator
** (gnome-panel:4348): DEBUG: Adding applet 9.

** (nautilus:4370): WARNING **: Unable to add monitor: Not supported
** (gnome-panel:4348): DEBUG: Adding applet 10.
** (gnome-panel:4348): DEBUG: Adding applet 11.
** (gnome-panel:4348): DEBUG: Adding applet 12.

(gnome-panel:4348): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:4348): DEBUG: Adding applet 13.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net use$
Please ask your system administrator to enable user sharing.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net use$
Please ask your system administrator to enable user sharing.

evolution-alarm-notify-Message: Setting timeout for 39417 1241740800 1241701383
evolution-alarm-notify-Message:  Thu May  7 18:00:00 2009

evolution-alarm-notify-Message:  Thu May  7 07:03:03 2009

** (update-notifier:4374): DEBUG: /usr/lib/update-notifier/apt-check returned 3 (security: 0)
** (update-notifier:4374): DEBUG: crashreport_check

** (update-notifier:4374): DEBUG: /usr/lib/update-notifier/apt-check returned 3 (security: 0)
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is d$
  import sha
** Message: no file info
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
Please send bug report - no VTS_TMAPT ??
*** Zero check failed in ifo_read.c:1786
    for pgcit->zero_1 = 0xff3c

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1790 ***
*** for pgcit->nr_of_pgci_srp < 10000 ***

```

Ok, that's it.. the page ends with a few hundred of the last error there regarding libdvdread.

---

