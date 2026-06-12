---
title: "Cant access samba shares"
date: 2009-06-19
forum: General Help
---

### Post by UltraDangerLord on 2009-06-19
Hello All,

I'm having a few problems accessing a samba share on a new server I'm putting together. I have samba working on a separate Ubuntu 7.10 server,I thought I had followed the procedure correctly, But I must be forgetting something somewhere.

I'm using a fresh install of Ubuntu Server 9.04 (64 bit). During the install options, I selected Samba Server. Now I'm trying to configure samba so I'm able to access it via my windows machine. I had followed a guide found from a google search that may be outdated.

I've set the IP to static and created 2 user accounts on Ubuntu, I have set the \home and sub-directories \home\user1 and \home\user2 to 777.

```
    
sudo useradd -d /home/user1 -m user1
sudo passwd user1

```

I have set the \home and sub-directories \home\user1 and \home\user2 to 777 to make sure permissions aren't a issue.

```

drwxrwxrwx  4 root root  4096 2009-06-19 10:38 home

```

```

drwxrwxrwx 2 user2 user2 4096 2009-06-19 10:38 user2
drwxrwxrwx 2 user1 user1 4096 2009-06-17 16:19 user1

```

I created 2 samba users with the same names/password as the Ubuntu users.

```

sudo smbpasswd -a user1

```

The problem may be within my smb.conf which I have posted below

```

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
   security = user

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
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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
[homes]
   comment = Home Directories
   browseable = no
   writable = yes
   create mask = 0700
   directory mask = 0700

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
   valid users = %S

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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


```
I also have Included a picture of the error I recieve from the windows machine.


Thank you for your time, Any suggestions or guidance would be helpful :D

---

### Post by jhannah on 2009-06-19
Are you even prompted to login to the server when you attempt to UNC to it? If so, it might just be a matter of cleaning up your smb.conf. 

You might want to try the below template replacing everything in bold to meet your needs:

```

[global]
  workgroup = **WORKGROUP**
  server string = %h (Samba)
  wins support = no

  security = user
  smb passwd file = /etc/smbpasswd
  log file = /var/log/samba/log.%m

  name resolve order = lmhosts host bcast

  netbios name = **servername**
  invalid users = root

[homes]
  comment = Home Directories
  browseable = no
  writable = yes
  create mask = 0700
  directory mask = 0700
  guest ok = no
  public = no
  valid users = user1, user2

```Let me know if that helps.

---

### Post by UltraDangerLord on 2009-06-19
**Edit**

>> almost did the trick, see below <<

Thank You Very Much! That did the trick! ):P

---

### Post by UltraDangerLord on 2009-06-19
Actually I'm still having problems with the user2 account. Im not able to view or connect to his share

---

### Post by swerdna on 2009-06-19
Check the Samba user database with this command:```
sudo pdbedit -L
```
Are they both there?

---

### Post by UltraDangerLord on 2009-06-19
This is what it shows

nobody:65534:nobody
ron:1000:ron,,,
freddy:1001:

ron is user1
freddy is user2

---

### Post by swerdna on 2009-06-19
> **UltraDangerLord said:**
> This is what it shows

nobody:65534:nobody
ron:1000:ron,,,
freddy:1001:

ron is user1
freddy is user2
See how freddy is different, as if the password didn't take? Looks like you should run freddy again through this:```
sudo smbpasswd -a freddy
```
Then oif you still have trouble, run this: ```
 sudo pdbedit -Lw
```

---

### Post by UltraDangerLord on 2009-06-23
I ran the commands but it seems that I'm still having the same problem with the second user as before. I also tried running these commands as root and restarted samba afterwards.


I ran the code below:

```
sudo smbpasswd -a freddy
```

I entered the password when prompted.

```
 sudo pdbedit -Lw
```

Which gave me this output

```
nobody:65534:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:[U          ]:LCT-00000000:
ron:1000:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:B5B97FC1017F420FF2033FF569B10037:[U          ]:LCT-4A412F10:
freddy:1001:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:033FF569B10037B5B97FC1017F420FF2:[U          ]:LCT-4A412FD7:

```

also I should note that running this command

```
sudo pdbedit -L
```

produces the same thing as before

```
nobody:65534:nobody
ron:1000:ron,,,
freddy:1001:

```

---

### Post by Celauran on 2009-06-23
The commas after the name in pdbedit aren't significant. If you look, you'll see they're in /etc/passwd as well. It's the difference between adding a user with adduser or useradd.

That aside, are you trying to connect as both users simultaneously? From the same Windows session? I know you have to unmount and unmap any mounted shares before being able to mount shares for another user, so it may well be something similar. (ie. if I map \\server\home\john to I:, I cannot map \\server\home\jack until I: is unmapped)

---

### Post by UltraDangerLord on 2009-06-23
> That aside, are you trying to connect as both users simultaneously? From the same Windows session? I know you have to unmount and unmap any mounted shares before being able to mount shares for another user, so it may well be something similar. (ie. if I map \\server\home\john to I:, I cannot map \\server\home\jack until I: is unmapped)

That was the problem, I was testing both of the accounts from one machine, I jumped on a seperate windows box and it connected with no problem.

To everyone that helped me

Thank You!

---

