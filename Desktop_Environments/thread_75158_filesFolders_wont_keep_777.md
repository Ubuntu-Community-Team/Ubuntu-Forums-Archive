---
title: "files/Folders wont keep 777"
date: 2005-10-13
forum: Desktop Environments
---

### Post by NXArmada on 2005-10-13
I have some file shares on my linux box that i share with SMB and the files are chmod 755 and i need them to be 777 everytime i change them to 777 in GUI and in Terminal they revert back to 755 and wont keep 777.  Is there way to mark them 777 and keep that setting.

---

### Post by KingBahamut on 2005-10-13
Have root make those permissions. What happens then?

---

### Post by NXArmada on 2005-10-13
i did sudo chmod 777 -R /path_to_folder    with verbose on
it says it changed them all to 777 but it reverts back to 755

---

### Post by NXArmada on 2005-10-13
bump

---

### Post by NXArmada on 2005-10-13
Im still haveing problems getting the folder/files to accept 777

---

### Post by NXArmada on 2005-10-14
bump again

---

### Post by drogoh on 2005-10-14
Sorry for your delay, but in your smb.conf what is the security mask?  It should be 0777 if it isn't.

---

### Post by NXArmada on 2005-10-14
its 777 also

---

### Post by drogoh on 2005-10-14
Hm.  Is there some chance I can get a look at your smb.conf?

---

### Post by NXArmada on 2005-10-14
Heres my smb.conf

> 
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
   workgroup = TENTEC
   netbios name = linux

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
   security = share

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
# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
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


[Bubba]
path = /home/linux1/Bubba/Bubba
available = yes
browseable = yes
public = yes
writable = yes

[Goldmine]
path = /home/linux1/Bubba/Goldmine
available = yes
browseable = yes
public = yes
writable = yes


---

### Post by drogoh on 2005-10-14
Hm.  I would go into swat (browse to localhost:901) and check your directory settings in your shares.  The manpage in there is quite descriptive.  I, for some reason, feel that the defaults have been changed out of security's sake.  I'd go into great detail, but I have to get back to work.

---

### Post by NXArmada on 2005-10-14
i keep getting connection refused and i reinstalled it twice and restarted, weird

---

### Post by NXArmada on 2005-10-17
BuMp i think thats what you say to move a topic up right its bUmP

---

### Post by NXArmada on 2005-10-18
could it be that the partition the files are in being that its a VFAt partition that the files wont mark as 777.

---

### Post by frodon on 2005-10-18
NXArmada, just a stupid question, did you set user rights in your fstab file for this partition ? if not it could be the problem.

---

### Post by NXArmada on 2005-10-18
/dev/hdb1   /home/linux/Bubba    vfat    rw,user,noauto     0       0

heres the FSTAB entry.

---

### Post by NXArmada on 2005-10-18
Problem Solved....

---

### Post by frodon on 2005-10-18
Cool, don't forget to tell how you solved the problem for those who got the same error.

---

### Post by NXArmada on 2005-10-18
i re wrote the FSTAB entry to look like this:
/dev/hdb1 /home/linux/Bubba vfat umask=0000 0 0

and then remounted the partition with:

sudo mount -a

---

