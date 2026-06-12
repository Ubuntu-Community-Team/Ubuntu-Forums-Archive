---
title: "deleted /var/lib/"
date: 2008-12-13
forum: General Help
---

### Post by oneadvent on 2008-12-13
What do I need to do to fix this issue?

(besides reinstall?) 

That is the only effected directory that I know of.

Also: What does this directory do really?

---

### Post by snova on 2008-12-13
Oh dear...

It's purpose: [http://www.pathname.com/fhs/2.2/fhs-5.8.html](http://www.pathname.com/fhs/2.2/fhs-5.8.html)

Mine is nearly 250 MB. I'm thinking reinstall. :(

Oh, there might be a way, but not an easy/simple one.

Edit: Given the importance of /var/lib/dpkg, there might not be a way at all.

And this is why you have to be careful with sudo. ;)

---

### Post by lensman3 on 2008-12-13
/var/lib is quite important.  A lot of running daemons keep there temporary data there.  I think, in most cases when a program is started it will create the files if they don't exist.   

Create the /var/lib as root using the command "mkdir -p /var/lib".  The -p will create all directories even if some are missing between the root and the "bottom".

change permissions to root by chown "root:root" /var/lib".
"chmod 755 /var/lib"

Then do a reboot and hopefully everything will be recreated.  

My /var/lib looks like the following but I have different packages than you installed.

drwxr-xr-x 34 root       root       4096 2008-10-12 12:29 .
drwxr-xr-x 23 root       root       4096 2007-12-02 16:41 ..
drwxr-xr-x  2 root       root       4096 2008-12-09 20:57 alternatives
drwxr-xr-x  4 torrent    torrent    4096 2008-08-22 08:25 bittorrent
drwxr-xr-x  2 root       root       4096 2008-07-10 08:06 bluetooth
drwx------  2 apache     apache     4096 2008-07-14 13:31 dav
drwxr-xr-x  2 root       root       4096 2008-02-27 21:40 dbus
drwxr-xr-x  2 root       root       4096 2008-10-05 21:08 dhclient
drwxr-xr-x  2 root       root       4096 2008-12-13 18:46 dhcpd
drwxr-x---  2 root       root       4096 2008-04-23 21:26 dhcpv6
drwxr-xr-x  3 root       root       4096 2008-09-14 21:52 dirmngr
drwxr-x---  2 dovecot    dovecot    4096 2008-12-08 00:15 dovecot
drwxr-xr-x  2 root       root       4096 2007-08-13 08:47 games
drwx------  2 haldaemon  haldaemon  4096 2008-12-01 00:17 hal
drwx------  2 ldap       ldap       4096 2008-07-02 04:24 ldap
-rw-r--r--  1 root       root       1154 2008-12-13 04:10 logrotate.status
drwxr-xr-x  2 root       root       4096 2007-12-09 01:00 misc
drwxr-x---  2 root       slocate    4096 2008-12-13 04:10 mlocate
drwxr-xr-x  2 root       root       4096 2007-02-05 13:50 multipath
drwxr-xr-x  5 root       root       4096 2008-05-24 12:47 nfs
drwxr-xr-x  2 ntp        ntp        4096 2008-08-17 15:17 ntp
drwxr-xr-x  3 root       root       4096 2008-05-08 06:56 php
drwxrwxr-x  2 polkituser polkituser 4096 2008-04-04 01:03 PolicyKit
-rw-------  1 root       root        512 2008-12-01 00:14 random-seed
drwx------  2 rpc        rpc        4096 2008-01-24 12:50 rpcbind
drwxr-xr-x  2 rpm        rpm        4096 2008-12-09 20:56 rpm
drwxr-xr-x  2 root       root       4096 2008-10-12 12:28 rpmrebuilddb.30253
drwxr-xr-x  5 root       root       4096 2008-11-27 05:58 samba
drwxr-xr-x  2 root       root       4096 2008-01-11 20:38 sepolgen
drwxr-xr-x  2 root       root       4096 2008-03-05 09:06 setroubleshoot
drwxr-xr-x  2 root       root       4096 2008-06-27 08:26 spamassassin
drwxr-xr-x  4 root       root       4096 2007-12-02 16:30 stateless
drwxrwxrwt  2 root       root       4096 2008-05-24 12:52 texmf
drwxr-xr-x  2 webalizer  root       4096 2008-02-15 04:55 webalizer
drwxr-xr-x  2 root       root       4096 2008-10-05 21:37 xkb

Good luck.  If you have to rebuild your system, backup your /home directory to a flash drive, re-install Linux, then copy the flash drive back.

---

### Post by lensman3 on 2008-12-13
Don't feel bad.  I once did a "rm -fr /usr/bin" on a Sun Sparc Station once and realized what I'd done about 3 seconds later.  About 20 percent of the OS programs were deleted before I did a cntl-c.  Luckily we (notice it is we now) had another sparc on the network and copied the deleted files from the other machine.

Oops.

---

### Post by oneadvent on 2008-12-13
I will definately try that. I was also thinking the repair option on the bootable cd's. what about getting a copy of someone elses?

---

### Post by snova on 2008-12-13
> Then do a reboot and hopefully everything will be recreated.

MySQL stores its databases in /var/lib. dpkg and apt put all their information there. How could that be recreated?

A nice thought, but that's not happening. ;)

I think there's nothing for it. :(

---

### Post by snova on 2008-12-13
> **oneadvent said:**
> I will definately try that. I was also thinking the repair option on the bootable cd's. what about getting a copy of someone elses?

It would invariably be different. Also, I don't know what the repair option does, but almost certainly nothing as far-reaching as this.

---

### Post by oneadvent on 2008-12-13
Well everything works fine except ssh and dkpg....maybe I can live without it. I have a lot of stuff I dont want to reconfigure, plus I have a webserver for my own personal use running which is heavily (for me anyway) modified.

---

### Post by lensman3 on 2008-12-13
Remove ssh and do a fresh install.  That should fix everything as before.  Same with the other program dkpg.

---

