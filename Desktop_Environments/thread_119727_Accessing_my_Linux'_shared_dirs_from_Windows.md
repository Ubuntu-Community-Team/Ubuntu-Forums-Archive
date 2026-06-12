---
title: "Accessing my Linux' shared dirs from Windows"
date: 2006-01-20
forum: Desktop Environments
---

### Post by behrangsa on 2006-01-20
Hi,

I have set up Samba on my Linux machine and here's my smb.conf:

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
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = behrang

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

wins support = no
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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

[Java]
path = /home/behrangsa/Java
comment = Ubuntu's Java Directory
available = yes
browseable = yes
public = yes
writable = yes

```

As it can be seen, I have shared my Java directory and I want to be able to access it from my Windows machine. But whenever I try to browse it via Windows Explorer, I am being asked for a password.

I added a password using smbpasswd -a but looks Samba doesn't recognize me when I want to login from a different machine.

Does anybody know what should I do inorder to be able to browse/read/write my shared Linux directories from my Windows machine?

Thanks in advance,
Behi

---

### Post by behrangsa on 2006-01-20
Solved :)

---

### Post by cvmostert on 2006-01-20
[QUOTE=behrangsa]Solved :)[/QUOTE]

It normally helps other people when you say HOW you solved your problem... :-)

thank you..

---

### Post by gullf1sk on 2006-01-20
I have the same problem, cant access my linux shares from a Windows machine, being asked for a password etc. Could you please post the solution you found to your problem?

---

### Post by LordBug on 2006-01-20
It's been a few years since I played with a Samba server, so I might be a tad off (rusty memory).

I believe NT/2K/XP will pop up a complete login box when connecting to a Samba share.  Just plug in valid information (from your linux accounts).  You should get the appropriate rights.

Alternatively, create an account on the Linux box with the same name you login to the Windows PC with.  Set a password on it (same as Windows if you want).  Connect with the Windows PC and plug in the new account information.  If the password is the same as the Windows PC account, you may just automatically connect.  I can't remember anymore.

---

### Post by cvmostert on 2006-01-20
[QUOTE=gullf1sk]I have the same problem, cant access my linux shares from a Windows machine, being asked for a password etc. Could you please post the solution you found to your problem?[/QUOTE]

Do you have a /etc/samba/smbusers file?

the file shoud have this inside:
> yourloginname = "network username"


restart samba by
sudo /etc/init.d/samba restart

and see if you can log on with your linux username and passwd.

the yourloginname should be your linux username. for example

chris = "network username"

---

### Post by Zimmer on 2006-01-20
[QUOTE=gullf1sk]I have the same problem, cant access my linux shares from a Windows machine, being asked for a password etc. Could you please post the solution you found to your problem?[/QUOTE]
You can see some of the answers to your problems at this thread
[http://ubuntuforums.org/showthread.php?t=114972](http://ubuntuforums.org/showthread.php?t=114972)

As a rule, to get networking right with XP I have a linux user name on the Ubuntu box , set up as a Samba user and it is the same name and Samba password as my user on XP .
If you follow the user instructions correctly here --posts#5 -#9
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)
and have shares mounted (via your config) there should not be a problem.
Try sharing the home directories in the config files by

[homes]
comment = Home Directories
browseable = yes

---

### Post by gullf1sk on 2006-01-20
Thanks for all the replys guys!
I'll try all this when i get home from work.
Cheers!

---

