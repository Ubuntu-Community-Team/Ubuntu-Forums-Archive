---
title: "Sharing USB HDD"
date: 2009-02-11
forum: General Help
---

### Post by detroit/zero on 2009-02-11
I have a 320GB external hard disk (formatted FAT32) I'm trying to share on LAN. 

When the device is connected and mounted, the computer it's attached to has full read/write access. In a root nautilus window, the device can be set to share no problem. It even shows up in the list of shared folders for the computer in the workgroup. However, when trying to access the drive via samba, the user on the remote computer is prompted for a password that doesn't correspond to the users' account on the computer, or the su/root password for that machine. 

I have two laptops, both running Hardy, and it works the same when the drive is mounted on either computer.

Both users have accounts on both computers, with identical usernames and passwords on each machine (i.e., user1's username and password is the same on laptop1 and on laptop2, and vice-versa). I tried changing the password and making sure the user was added to the samba group by using (in no particular order)```
smbpasswd -a *user2*
smbpasswd -m *user2hostname*
smbpasswd -r *user2hostname*
smbpasswd *user2*
```I did this on both computers fo each user, but no matter what, whenever either of us tries to acces that drive from a network share, we're prompted for a password that doesn't correspond to what passwords I have set.

I should add that other shared folders (and a printer) work flawlessly, and ssh/scp access works without a problem.

Can anybody guide me to set this external drive up properly for sharing? I keep most of my (our) media on this disk, and I don't see any good reason why I should have to keep plugging/unplugging/mounting/unmounting this drive between computers when a simple network share should enable me to stream media/work with documents & such while it's attached & mounted to either computer.

Thanks for any help.

---

### Post by detroit/zero on 2009-02-12
Well, since making this post, without changing any settings or doing anything I can think of, I've lost all file & printer sharing between my two Ubuntu boxes.

Here's smb.conf:```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;    wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

# Line added to "fix" usb sharing
    usershare owner only = False

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
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
    log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
    max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;    syslog only = no

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
;    security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;    encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
    passdb backend = tdbsam

    obey pam restrictions = yes

;    guest account = nobody
    invalid users = root

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

# This option controls how nsuccessful authentication attempts are mapped 
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
;    logon path = \\%n\%u\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;    logon home = \\%n\%u

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;    load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;    printing = cups
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
    socket options = TCP_NODELAYexternal

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;linpopup-removed    message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;    domain master = auto

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
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers
    guest ok = yes

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
    guest ok = yes
    read only = no
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
# External USB disk sharing
[disk]
    path = /media/disk
    available = yes
    browseable = yes
    guestok = yes
    writeable = yes
    guest ok = yes
    comment = USB Disk
# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[public-1]
    path = /home/zero/Public
    writeable = yes
    browseable = yes
    guest ok = yes
    comment = zero's public folder
```I'd include fstab, but I don't have this external drive (or any network drives) listed in fstab. Here's what testparm says:```
zero@zero-laptop:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[disk]"
Processing section "[public-1]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    socket options = TCP_NODELAYexternal
    dns proxy = No
    usershare allow guests = Yes
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d
    invalid users = root
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    read only = No
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[disk]
    comment = USB Disk
    path = /media/disk
    read only = No

[public-1]
    comment = zero's public folder
    path = /home/zero/Public
    read only = No
```

Anyone think they can help?

---

### Post by sr20ve on 2009-02-12
Are there any Windows computers that need access to the share? If not, I would recommend going with an NFS share instead of samba.

Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1067194](http://ubuntuforums.org/showthread.php?t=1067194)

---

### Post by detroit/zero on 2009-02-12
> **sr20ve said:**
> Are there any Windows computers that need access to the share? If not, I would recommend going with an NFS share instead of samba.

Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1067194](http://ubuntuforums.org/showthread.php?t=1067194)
Well, both laptops are dual-boot, so the possibility exists that something will have to be shared with a windows box somewhere along the line. Plus, for the life of me, I can't seem to make NFS work between the ubuntu computers. I think it's a problem with firewalls, but I'm not sure yet.

In all my reading, it seems to me the problem is that the drive is formatted FAT32 instead of NTFS or EXT. I'm considering trying to dump all my files somewhere and re-formatting. It'd be nice if I didn't have to, though.

---

### Post by scratman on 2009-02-17
This may not address all of your issues, but it's how I managed it.  Give it a whirl, and if you hit problems, let me know.

I had been banging my head against a wall as it appears that my HDD cannot be shared by Ubuntu, as it is FAT32, and not a Linux file system. I had managed to get access to my Public directory from another machine on the system via Firefox by typing smb://MY.IP.ADDRESS.X/ into the address bar, so I could see the machine. I copied the folder settings of my home/public/ folder to the folders I wished to share on my USB HDD. Nothing doing.

Then I had a brainwave. I opened up terminal and typed
Code:

sudo fdisk -l

This revealed that my external drive was mounted to /dev/sdb/.

I typed
Code:

sudo umount /dev/sdb1/

This made my hard drive disappear. I then typed
Code:

sudo mount /dev/sdb1/ /home/myusername/Public

I then browsed to my home/public/ folder, and voila, my folders appeared!!!

I opened Firefox and typed smb://MY.IP.ADDRESS.IN/ and I could access my shared folders!!! Clicking through I can access the folders and files that I have shared!

I then copied this address into Nautilus, and it still worked.

Navigating to my Hard Drive, I can set up write permissions for those that I wish to be fully accessed, and leave the remainder as read only. Any folders that are not shared remain invisible.

As I said, this is an ugly solution, but it does mean that I have access.

Does anybody have any better ideas, because this is complicated!

---

### Post by detroit/zero on 2009-02-18
> **scratman said:**
> This may not address all of your issues, but it's how I managed it.  Give it a whirl, and if you hit problems, let me know.
That's not too complicated, really.. Just mount the drive to a folder that's already being shared..

I'll give that a shot and post back when I get some time. I think it might just work, though. I'll let you know.

Thanks for the idea!

---

