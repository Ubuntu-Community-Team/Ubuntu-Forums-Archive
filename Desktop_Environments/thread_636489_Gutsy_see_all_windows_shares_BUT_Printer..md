---
title: "Gutsy see all windows shares BUT Printer."
date: 2007-12-09
forum: Desktop Environments
---

### Post by froyd on 2007-12-09
Hi all,

I have a samsung SCX4200 Laser installed in my XP machine on my desktop and im trying to add this printer to my Gutsy laptop.
I tried adding the printer from System -> Administration -> Printing , by adding a samba network printer, but it wont go.
Breaking down the troubleshooting the weird part is that everything is accessible both ways ( gutsy -> win and win -> gutsy ), all the shared folders and everything and YES my printer is shared on the windows box.
I added a fake printer to my gutsy to make sure windows could see it and YES, windows can see if i have a printer installed on gutsy but the other way just wont go.
Please could anybody help me, i have googled and searchd here in the forums but havent found anything like my problem. ( gutsy cant see shared windows printer ).

If it helps here are the contents of my cups config and my samba config.

```
#
# "$Id: cupsd.conf.in 6720 2007-07-25 00:40:03Z mike $"
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
# End of "$Id: cupsd.conf.in 6720 2007-07-25 00:40:03Z mike $".
#


```

and smb.conf

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

# "testparm" to check that you have not made any basic syntactic 

# errors. 

#



#======================= Global Settings =======================



[global]

	log file = /var/log/samba/log.%m

	load printers = yes

	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

	socket options = TCP_NODELAY

	obey pam restrictions = yes

	encrypt passwords = true

	passwd program = /usr/bin/passwd %u

	passdb backend = tdbsam

	dns proxy = no

	server string = %h UbuntuSambaServer

	printing = cups

	invalid users = root

	workgroup = Homenet

	os level = 20

	printcap name = cups

	syslog = 0

	panic action = /usr/share/samba/panic-action %d

	max log size = 1000



## Browsing/Identification ###



# Change this to the workgroup/NT-domain name your Samba server will part of



# server string is the equivalent of the NT Description field



# Windows Internet Name Serving Support Section:

# WINS Support - Tells the NMBD component of Samba to enable its WINS Server

;   wins support = no



# WINS Server - Tells the NMBD components of Samba to be a WINS Client

# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both

;   wins server = w.x.y.z



# This will prevent nmbd to search for NetBIOS names through DNS.



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

;   bind interfaces only = true







#### Debugging/Accounting ####



# This tells Samba to use a separate log file for each machine

# that connects



# Put a capping on the size of the log files (in Kb).



# If you want Samba to only log through syslog then set the following

# parameter to 'yes'.

;   syslog only = no



# We want Samba to log a minimum amount of information to syslog. Everything

# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log

# through syslog you should set the following parameter to something higher.



# Do something sensible when Samba crashes: mail the admin a backtrace





####### Authentication #######



# "security = user" is always a good idea. This will require a Unix account

# in this server for every user accessing the server. See

# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html

# in the samba-doc package for details.

;   security = user



# You may wish to use password encryption.  See the section on

# 'encrypt passwords' in the smb.conf(5) manpage before enabling.



# If you are using encrypted passwords, Samba will need to know what

# password database type you are using.  





;   guest account = nobody



# This boolean parameter controls whether Samba attempts to sync the Unix

# password with the SMB password when the encrypted SMB password in the

# passdb is changed.

;   unix password sync = no



# For Unix password sync to work on a Debian GNU/Linux system, the following

# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for

# sending the correct chat script for the passwd program in Debian Sarge).



# This boolean controls whether PAM will be used for password changes

# when requested by an SMB client instead of the program listed in

# 'passwd program'. The default is 'no'.

;   pam password change = no



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

;   logon path = \\%N\%U\profile



# The following setting only takes effect if 'domain logons' is set

# It specifies the location of a user's home directory (from the client

# point of view)

;   logon drive = H:

;   logon home = \\%N\%U



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



# lpr(ng) printing. You may wish to override the location of the

# printcap file

;   printing = cups

;   printcap name = /etc/printcap



# CUPS printing.  See also the cupsaddsmb(8) manpage in the

# cupsys-client package.



# When using [print$], root is implicitly a 'printer admin', but you can

# also give this right to other users to add drivers and set printer

# properties

;   printer admin = @lpadmin





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

;

; The following was the default behaviour in sarge

; but samba upstream reverted the default because it might induce

; performance issues in large organizations

; See #368251 for some of the consequences of *not* having

; this setting and smb.conf(5) for all details

;

;   winbind enum groups = yes

;   winbind enum users = yes



#======================= Share Definitions =======================



# Un-comment the following (and tweak the other settings below to suit)

# to enable the default home directory shares.  This will share each

# user's home directory as \\server\username

;[homes]

;   comment = Home Directories

;   browseable = no



# By default, \\server\username shares can be connected to by anyone

# with access to the samba server.  Un-comment the following parameter

# to make sure that only "username" can connect to \\server\username

# This might need tweaking when using external authentication schemes

;   valid users = %S



# By default, the home directories are exported read-only. Change next

# parameter to 'yes' if you want to be able to write to them.

;   writable = no



# File creation mask is set to 0700 for security reasons. If you want to

# create files with group=rw permissions, set next parameter to 0775.

;   create mask = 0700



# Directory creation mask is set to 0700 for security reasons. If you want to

# create dirs. with group=rw permissions, set next parameter to 0775.

;   directory mask = 0700



# Un-comment the following and create the netlogon directory for Domain Logons

# (you need to configure Samba to act as a domain controller too.)

;[netlogon]

;   comment = Network Logon Service

;   path = /home/samba/netlogon

;   guest ok = yes

;   writable = no

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





[homes]

```

---

### Post by froyd on 2007-12-10
anyone please ?

---

### Post by mcouture on 2007-12-10
I seem to have the same issue.

I have a Windows printer that is shared.  All my Windows boxes can print to it and see it when browsing.

My 2 Ubuntu Gutsy boxes cannot see that printer while browsing.  However if I use SMBCLIENT, I can connect and actually issue a print command.

Any suggestions would be greatly apprieciated!

---

### Post by NZ-Wanderer on 2007-12-10
Adds name to the list..

I too have the same problem on my network... While Gutsy can see and be seen (file-wise), it doesn't want to even see the printer on my vista machine, yet my 2 other vista machines can talk to the printer with no problems...

A little more info...

If I try to setup the printer in System Settings/Printer/"add Printer/Class" - choosing the smb shared printer, 

if I use the name/password option, I see the MSHOME workgroup, but nothing inside it...
if I use the Guest option, I see the MSHOME workgroup AND my other computers names, however, if I click on the computer that has the printer I get "error returning browse list: NT_STATUS_DENIED"
if I use the anonymous option, I see the MSHOME workgroup AND my other computers names, however, if I click on the computer that has the printer I get "error returning browse list: NT_STATUS_DENIED"


and yes I know the printer is being shared, as my other windows machines quite happily print files form them through the network.

---

### Post by NZ-Wanderer on 2007-12-11
UPDATE - It WORKS :)

Hokay, I got it working... - tried something I didn't think would work, but it did, so here is the exact steps I did incase it works for anyone else :)...

1) Goto System Settings, choose Printer, then choose "add Printer/Class" (Or whever you go to add a printer in-case it's different in other flavours of K/Ubuntu)
2) Click "next" at the wizard welcome
3) Choose "smb shared printer (Windows)" and click "next"
4) Choose "normal" account, and type in your user name and Password of the Windows machine, click "next" to continue
5) In "workgroup" window, type your workgroup (EG: mine is MSHOME on both K/Ubuntu and Windows)
6) In "server" window type your server/computers name (EG: My Windows machine that has the printer is called "Server-chick"
7) In the  "Printer Window" type the name of your printer (as windows says it is on the windows machine (EG: Windows says my Printer is: "EPSON Stylus CX5900 Series" so that is what I type EXACTLY into this window (Upper and lower case matter)
8) Click "Next" to carry on, do NOT hit "scan"
9) Choose your printer out of the list that appears (Even tho I have the CX5900 it isn't in the list, so I chose the nearest to it which was the CX5800) and click "Next" to continue
10) Choose your driver selection, I just choose the top option as I didn't know any better :)
11) On the next screen, hit the "Test" button, and if you put everything in properly you should get a test page just like I am getting printing out now :) :)
12) After that, just carry on with the wizard till it finishes...

Hope this might be of some help to someone, as I said, it works for me :)

---

### Post by Tweenk on 2007-12-12
Things of mention:
1. You need to use your username and password for the Windows computer (the same you use to log in).
2. I didn't know the exact printer name also works, I have put in the share name of my printer. This is what you enter when you share a printer in Windows. I recommend to use a share name with only A-Z letters, digits and underscores. Also try to give your workgroup a sane name.

I think that missing authentication data is the problem for most people here. Windows printers are not accessible for unauthenticated users by default.

---

### Post by froyd on 2007-12-12
Thank you all for your support,

Yah, i believe that its found out that unauthenticaded users wont be able to print then. Kinda weird because dapper was not like that. Never had to input a user and password for it.


Thx anyway!!

I Wish all the best for this holiday season!

---

### Post by techieguy_100 on 2007-12-16
I have the same problem however, when I add a new class I get the attached screen, with a blank list of printers to add to the class, no option to type anything in, no browse just cancel or back.  :(  Help would be great!
OK, I figured it out, chalk it up to Linux newbie!  I found where to set my workgroup name and changed it to match my windows boxes and everything was cool!  :guitar:

Glen

---

