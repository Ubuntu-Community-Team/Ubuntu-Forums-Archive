---
title: "Samba/SMB4K displays wrong IP address"
date: 2006-08-27
forum: Desktop Environments
---

### Post by jswhite on 2006-08-27
[samba n00b]

Teh setup:

1 laptop running SimplyMEPIS 6.0 (based on Dapper), static IP 192.168.1.20, Samba installed by default (automagically set up for me by Mepis) w/SMB4K.

1 desktop running WinXP, static IP 192.168.1.30

Teh problems:

Don't know how much of an actual issue this is, but it's been bugging me.  I store files, backups, etc. on my wife's desktop.  She also has a scanner attached to her computer that I use, then use Samba to transfer the scanned documents over to my computer.  My normal procedure for this is to open SMB4K, click on my wife's computer, and mount her shared directory.

PROBLEM #1: Samba can't seem to recognize an IP address for her computer.  It doesn't actually stop me from mounting her shares, but things seem to move REALLY slowly when getting the shares list (and mounting the appropriate directory).  SMB4K just lists her IP address as "unknown."  I'd love to find out how to correct this.

PROBLEM #2: Samba/SMB4K is displaying the WRONG IP address for my computer.  Instead of my proper static IP (192.168.1.20), it displays my IP as 192.168.1.100.  That would have been my IP address briefly after installing Mepis, as it's the first DHCP address my router would have leased.  After my first boot, I changed to the aforementioned static IP.  For some reason, Samba still lists me at the old DHCP address.  If I try to access a list of the shares on my computer through SMB4K, I get a "can't connect to server" error.  Not shocking, since there's no computer with that IP address on my network.  Oddly, though, I can still properly access my shared directories from my wife's computer.  Anyone know how to get Samba to properly recognize the IP address for my computer?

In case it's needed, here's my smb.conf file:

```

;*******************section global*****************
[global]

# Do something sensible when Samba crashes: mail the admin a backtrace
panic action = /usr/share/samba/panic-action %d
printing = cups
workgroup = mepisgrp
server string = %h server (Samba %v)
hosts allow = 192.168.0. 192.168.1. 192.168.2. 192.168.79. 127.
socket options = IPTOS_LOWDELAY TCP_NODELAY
log level = 1
dead time = 15
wins support = yes
hide unreadable = yes
passdb backend = tdbsam guest
dns proxy = no
max log size = 1000
security = share
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
ldap ssl = No
server signing = Auto
oplocks = No
level2 oplocks = No
;*******************section jswhite*****************
[jswhite]
comment = /home/jswhite
path = /home/jswhite
guest ok = yes
read only = no
;*******************section homes*****************
[homes]
comment = Home Directories
browseable = no
read only = no
;*******************section printers*****************
[printers]
comment = All Printers
path = /tmp
browseable = no
printable = yes
guest ok = yes
create mode = 0700


```
[/samba n00b]

---

### Post by dgray_from_dc on 2007-01-11
I'm experiencing the exact same problem.  I set up a server and I didn't start with the static IP address I'm now using.  I set up smb4k to remount shares on startup and it's looking for the wrong IP address.  My work-around is to rescan my network after startup.  After that, all is well (though annoying).

  The oddest thing about this is that I recently had a system failure during my upgrade to Edgy and was able to salvage my home directory (now on a separate partition).  Before I restored it, the old IP address didn't show up.  Now it does and I can't figure out where the file containing the old IP is hiding.

I could kill my username and start over but it's just too inconvenient.  I'd rather fix the problem than work around it.

---

