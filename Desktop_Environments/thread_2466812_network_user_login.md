---
title: "network user login"
date: 2021-09-06
forum: Desktop Environments
---

### Post by tommyfun on 2021-09-06
Hi,

I'm running 20.04 in a lab environment, using nis for now, but ldap next year and nfs mounted home directories.

Is it possible to configure gdm3 for the network logins or do I have to use lightdm?

I have it working with lightdm but I'd rather stick to gdm, I know gdm can be configured in fedora to accept network logins from nis or ldap.

thanks,
-tom

---

### Post by TheFu on 2021-09-07
NIS is easy and trivial to hack. Since around 1998, nobody should be using it.

I suspect the real issue for network logins is that Gnome3+ doesn't like providing a desktop over a network.  Almost any other DE can be used with x2go as a secure, remote, desktop with fairly good performance on the same LAN or halfway around the world.  I've used x2go from 5 continents.  No way would I use rdp or vnc-based remote desktops without a full VPN everywhere.

BTW, with 20.04 and later, there are many more snap packages, so if you intend to use snaps on the systems with end users, NFS isn't supported and NFS HOME directories will immediately fail with every snap package.  The Snap team has known about this failure since at least 2017 and decided that NFS should fix it for snaps to work.  [https://forum.snapcraft.io/t/snaps-and-nfs-home/438](https://forum.snapcraft.io/t/snaps-and-nfs-home/438)
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1662552](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1662552)
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1643706](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1643706)
The only solution for Gnome3 DEs to work over a remote desktop that I've heard actually works is with only the Gnome3 specific tool.   
[https://wiki.gnome.org/Projects/Mutter/RemoteDesktop](https://wiki.gnome.org/Projects/Mutter/RemoteDesktop)

For a number of years, I had an LDAP authentication server running with NFS HOME directories for all users across about 20 systems.  Sadly, the LDAP management tool was part of a larger, very ugly-to-integrate, project that required removing all POSIX user schemas from LDAP before any upgrade, then manually putting those POSIX user schema changes back post upgrade.  Training users to only change their passwords in the email webapp wasn't hard, but other applications still retained their "change password" options - though those would never work.

I really wish NIS had a drop in replacement that didn't mandate paying Oracle (i.e. NIS+) or MSFT (AD + CAL costs for each client).  It would be fantastic if a thick client LDAP management tool existed that hooked into all Linux desktops and servers by default for userids and groupids over 1000.  
FusionDirectory looks interesting to me. I avoid Php web-apps, so the most popular alternative isn't an option here.  Previously, I would have setup a CentOS FreeIPA system, but both those project seem to have been killed by Redhat and the FreeIPA server never really worked on Ubuntu - clients were fine, but not the server.

---

### Post by tommyfun on 2021-09-08
Yes, I discovered the nfs snap issue last week.  I was able to get tarballs of what I had installed with snap and stuck them on the nfs server using autofs to mount them and added application.desktop files to launch them.

I was also looking at freeipa but I think I'm going with openldap next summer.

I'm ok with lightdm, even though I can configure fedora's gdm to support network users, but my biggest problem right now is pulse audio.  I have another thread in the general help forum about that.  It seems that pulse audio can't write to the nfs home directory, so it crashes and there's no sound.  I fell like I've been thrown back to 1998, which under normal circumstances I would like.

It looks like I'm switching to fedora workstation, maybe over Christmas break.

1. Ubuntu doesn't support netbooting anymore, so I can't pxe deploy the lab
2. Sound doesn't work
3. Fedora supports network login in gdm


It's too bad.  I had a good run with Ubuntu.

---

### Post by ActionParsnip on 2021-09-09
Ubuntu isn't always the answer. Its why multiple distributions exist

---

