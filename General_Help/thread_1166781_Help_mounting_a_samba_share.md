---
title: "Help mounting a samba share"
date: 2009-05-22
forum: General Help
---

### Post by abo999 on 2009-05-22
Ubuntu 9.04, I'm trying to mount a samba share at boot, so that I can make Banshee see the music I have on there. I've created the folder

```
/media/music
```

The samba is a NAS enclosure, the music is in the folder PUBLIC/Music

So after googling for what to add to fstab I found an article on Ubuntugeek which suggested:

```
//192.168.0.4/PUBLIC/Music /media/music smb defaults 0 0
```

It does not mount on boot. If I try to mount it myself in the terminal using

```
sudo mount /media/music
```

I get the error

```
mount: unknown filesystem type smb
```

Can someone please suggest what the fstab entry *should* read in order for me to be able to mount the share?

Thanks

---

### Post by abo999 on 2009-05-22
Update to this:

After a bit more googling, it has been suggested to install smbfs which I have done, and I've changed the line in fstab to:
```

//192.168.0.4/PUBLIC/Music /media/music smb defaults 0 0
```

But it still won't mount. Now, if I try mounting in the terminal it asks me for a password (the share isn't password protected), then gives an error:

```
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

---

### Post by Paul41 on 2009-05-22
This link has some information about samba shares in fstab.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by abo999 on 2009-05-22
Thanks for that; I've tried a few tweaks as suggested at the link but nothing seems to yield different results.

It's frustrating because I can access the files on the share through 'Network' in Nautilus, I just can't mount the share so that Banshee can see it :(

---

### Post by Paul41 on 2009-05-22
Could you post your samba configuration file? It's at /etc/samba/smb.conf

As a side note if you are just wanting to listen to music off another computer you can use Firefly (mt-daap) to serve up the music and Banshee can see/play it.

```
sudo apt-get install mt-daap
```

---

### Post by abo999 on 2009-05-22
> **Paul41 said:**
> Could you post your samba configuration file? It's at /etc/samba/smb.conf

As a side note if you are just wanting to listen to music off another computer you can use Firefly (mt-daap) to serve up the music and Banshee can see/play it.

```
sudo apt-get install mt-daap
```

Ah yeah, it's just an external hard drive enclosure with a built-in samba server and ethernet port to plug into the router. One of these, no-name Chinese things:
[URL="http://www.computervitals.com/forum/nas_100_network-t11358.html?"][HTML]
http://www.computervitals.com/forum/nas_100_network-t11358.html?[/HTML][/URL]

Here is the Samba config file:

```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

---

### Post by abo999 on 2009-05-22
Ah hang on, that's the smb.conf on the machine wishing to mount the share. Do you mean the file on the actual share device? That could be a bit tricky.

---

### Post by Paul41 on 2009-05-22
I was just going to ask about that, it would be the file from the drive. Since this is just a drive I am not sure how samba would work. You need to set samba up to share the drive and add users to samba.

---

### Post by abo999 on 2009-05-22
> **Paul41 said:**
> I was just going to ask about that, it would be the file from the drive. Since this is just a drive I am not sure how samba would work. You need to set samba up to share the drive and add users to samba.

It appears to configure itself mainly. There is a web console in which you can define different shares, and set passwords but the rest is done for you.

It does seem to work, my share (PUBLIC) can be accessed from the three Ubuntu and two Windows machines we have.

There is no password set, BTW

---

### Post by Paul41 on 2009-05-22
Have you given this drive a static IP address? Is it possible that the IP was assigned by DHCP and has changed now?

---

### Post by abo999 on 2009-05-22
First thing I did after formatting the drive. Incidentally, it gives itself the hostname 'STORAGE-0A1D' which I can see in 'Networks' in Nautilus. I've tried configuring with both the hostname and IP address, with the same result.

---

### Post by Paul41 on 2009-05-22
Are you able to connect to the share with smbclient?

[https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html](https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html)

---

### Post by gooligan on 2009-05-22
Are you using WD MyBook World Edition as your share?
I use mine, and I am able to mount to jaunty with this entry in my fstab:

```

//MyBookWorld/PUBLIC	/mnt/MyBookWorld		cifs	defaults,user,noauto		0	0

```

---

### Post by abo999 on 2009-05-22
I tried this:

```

neal@neal-laptop:~$ sudo smbclient //192.168.0.4/PUBLIC
[sudo] password for neal: 
Enter root's password: 
Domain=[&#519;] OS=[] Server=[&#65533;&#65533;&#65533;]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: SUCCESS - 0
neal@neal-laptop:~$ 

```

---

### Post by abo999 on 2009-05-22
> **gooligan said:**
> Are you using WD MyBook World Edition as your share?
I use mine, and I am able to mount to jaunty with this entry in my fstab:

```

//MyBookWorld/PUBLIC	/mnt/MyBookWorld		cifs	defaults,user,noauto		0	0

```

No, it's a Chinese no-name. I've tried mounting with similar commands to that, but no banana :(

---

### Post by Paul41 on 2009-05-22
> **abo999 said:**
> I tried this:

```

neal@neal-laptop:~$ sudo smbclient //192.168.0.4/PUBLIC
[sudo] password for neal: 
Enter root's password: 
Domain=[&#519;] OS=[] Server=[&#65533;&#65533;&#65533;]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: SUCCESS - 0
neal@neal-laptop:~$ 

```

I have seen people that have been able to fix this by adding the following to their smb.conf file in the global section but since you can't get to the file I am not sure how much this helps

```
client lanman auth = Yes
lanman auth = Yes 
```

There is also a nautilus bug in launchpad about this. [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/208531](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/208531)

Not sure if any of this will help though.

---

### Post by abo999 on 2009-05-22
Yeah, pain that I can't edit it... There is the facility to update the firmware which I'll have a bash at, otherwise I'll have to have a rethink about how I get media on to my iPod.

---

