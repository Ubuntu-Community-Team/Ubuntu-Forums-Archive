---
title: "KDM, WDM, and GDM login screen loops"
date: 2009-05-30
forum: Desktop Environments
---

### Post by SagaciousKJB on 2009-05-30
Something has gone wrong with my Linux installation.  Any login-screen from any of the managers I've tried will simply display a black screen, and then present me with the login-screen over and over again.

I know that it is not a problem with Xorg or my drivers in any way because I can su to root and use "startx" to open up xfce.  I haven't tested whether KDE works with this method because I don't know how to specify window managers with startx, but everything works just the way it should in xfce.

I've tried several things that have been in "[SOLVED]" threads on Ubuntu forums that haven't helped, and they mostly revolve around moving one's .kde directory to a backup, using dpkg-reconfigure to reconfigure xorg-server, using the recovery console to use the xfix, etc.  None of that works however.  I've tried to install and reinstall *dm (kdm, wdm, and gdm) already and this does nothing to solve the problem, and I've also got my distribution packages upgraded.

My system is a little "weird" in that I'm running Linux 2.6.29.3 on Ubuntu 8.04.1 because I want to use KDE3 but the default kernel's don't run well on my hardware.

I'm trying to avoid a reinstall, but I'm not sure if I should, because this problem occurred after a system failure.  I had to hard reset the computer, and nothing seemed wrong for a few days, until I noticed that my encrypted hard-drive was corrupted and couldn't be mounted with LUKS any more.  It was causing the system to hang at boot because aes_i568 would lock up and complain about unknown symbols.  So I formatted the drive to stop the system hangs, and the looping login-screen problem began.  

This caused a problem initially because /tmp was originally a symlink to a /tmp folder on this encrypted drive, but even after I made a directory /tmp, the looping problem persisted; could there be a /tmp file I lost causing all of this though?

Could it possibly be a problem with my /home/ disk?  I'm running all of my files and application settings off of it just fine, so I don't see why it would be.  I ran disk checks and all of my other disks were fine.

The only clues of a problem I have are these...

/var/log/auth.log
```

May 30 17:14:37 amd kdm: :0[7556]: pam_unix(kdm:session): session opened for user sagacious by (uid=0)
May 30 17:14:37 amd kdm: :0[7556]: pam_unix(kdm:session): session closed for user sagacious

```

This is the auth.log from when I try to log in.  Clearly it shows a successful login, but immediately it just logs out.  The only other log entry that matches this timestamp is from a daemon

```

/var/log/syslog:May 30 17:14:37 amd console-kit-daemon[6637]: WARNING: Unable to activate console: No such device or address

```

Here are log entries from everything in /var/log/ matching May 30 17:14:xx

```
/var/log/acpid:[Sat May 30 17:14:02 2009] client connected from 6024[0:0]
/var/log/acpid:[Sat May 30 17:14:02 2009] 1 client rule loaded
/var/log/acpid:[Sat May 30 17:14:02 2009] client connected from 6024[0:0]
/var/log/acpid:[Sat May 30 17:14:02 2009] 1 client rule loaded
/var/log/acpid:[Sat May 30 17:14:02 2009] client connected from 6024[0:0]
/var/log/acpid:[Sat May 30 17:14:02 2009] 1 client rule loaded
/var/log/acpid:[Sat May 30 17:14:07 2009] client connected from 6024[0:0]
/var/log/acpid:[Sat May 30 17:14:07 2009] 1 client rule loaded
/var/log/acpid:[Sat May 30 17:14:07 2009] client connected from 6024[0:0]
/var/log/acpid:[Sat May 30 17:14:07 2009] 1 client rule loaded
/var/log/acpid:[Sat May 30 17:14:07 2009] client connected from 6024[0:0]
/var/log/acpid:[Sat May 30 17:14:07 2009] 1 client rule loaded
/var/log/acpid:[Sat May 30 17:14:31 2009] client connected from 6024[0:0]
/var/log/acpid:[Sat May 30 17:14:31 2009] 1 client rule loaded
/var/log/acpid:[Sat May 30 17:14:31 2009] client connected from 6024[0:0]
/var/log/acpid:[Sat May 30 17:14:31 2009] 1 client rule loaded
/var/log/acpid:[Sat May 30 17:14:31 2009] client connected from 6024[0:0]
/var/log/acpid:[Sat May 30 17:14:31 2009] 1 client rule loaded
/var/log/acpid:[Sat May 30 17:14:38 2009] client connected from 6024[0:0]
/var/log/acpid:[Sat May 30 17:14:38 2009] 1 client rule loaded
/var/log/acpid:[Sat May 30 17:14:38 2009] client connected from 6024[0:0]
/var/log/acpid:[Sat May 30 17:14:38 2009] 1 client rule loaded
/var/log/acpid:[Sat May 30 17:14:38 2009] client connected from 6024[0:0]
/var/log/acpid:[Sat May 30 17:14:38 2009] 1 client rule loaded
/var/log/auth.log:May 30 17:14:07 amd kdm: :0[7491]: pam_unix(kdm:session): session opened for user sagacious by (uid=0)
/var/log/auth.log:May 30 17:14:07 amd kdm: :0[7491]: pam_unix(kdm:session): session closed for user sagacious
/var/log/auth.log:May 30 17:14:37 amd kdm: :0[7556]: pam_unix(kdm:session): session opened for user sagacious by (uid=0)
/var/log/auth.log:May 30 17:14:37 amd kdm: :0[7556]: pam_unix(kdm:session): session closed for user sagacious
/var/log/daemon.log:May 30 17:14:07 amd console-kit-daemon[6637]: WARNING: Unable to activate console: No such device or address
/var/log/daemon.log:May 30 17:14:37 amd console-kit-daemon[6637]: WARNING: Unable to activate console: No such device or address
/var/log/syslog:May 30 17:14:07 amd console-kit-daemon[6637]: WARNING: Unable to activate console: No such device or address
/var/log/syslog:May 30 17:14:37 amd console-kit-daemon[6637]: WARNING: Unable to activate console: No such device or address

```

Anyway, that's the most descriptive narrative of the problem I can give, and the only information I can really ascertain.  Here is some more info about my system, just to cover some bases...

Distro: Kubuntu 8.04.1
Linux Kernel: Linux 2.6.29.3
Hardware:
DFI LP JR 790GX-M2RS
AMD Phenom X4 9950 BE
2GB OCZ DDR2-800 RAM
XFX GeForce 9800GT 512MB PCI-E
Creative SoundBlaster Live PCI SoundCard
2 x SATA II WD500* 500 GB Western Digital HDDs
1 x SATA II WD1000* 1000 GB Western Digital HDD
1 x IDE WD60* 60 GB Western Digital HDD
1 x USB2.0 250 GB Maxtor OneTouch HDD


The system is usable thanks to startx, but I would really like to be able to get this fixed so I can use it properly.  If worse comes to worse, is there at least a way to run startx as my own user account until I can reinstall?

---

### Post by uboltun on 2009-06-01
I have a similar problem. My root partition ran out of space at one point and ever since I have to start KDE session using startx. The login screen does show up if I restart kdm , but cant go past that. Still looking for a solution ...

---

