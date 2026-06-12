---
title: "Samba trouble in Breezy"
date: 2005-10-16
forum: Desktop Environments
---

### Post by unclben on 2005-10-16
I have two computers on a LAN, one running WinXP Pro and the other running Breezy (upgraded via Synaptic from Hoary). I set up smb.conf as outlined [here]("http://ubuntuforums.org/showthread.php?t=76647"). I've pasted my full smb.conf below, as well. I have added myself to smbusers and set a password.

I can see and browse my XP share from Breezy. I can see my Breezy share from both XP and Breezy, but if I try to connect to it I am rejected. When I try to connect through View Workgroup Computers in XP, I get '*\\Breezy2 is not accessible. You might not have permissions to use this network resource. The network path was not found*.' When I try to connect through the Connect to Server dialog in Nautilus, I get '*The folder contents could not be displayed. Sorry, couldn't display all the contents of "Windows Network: breezy2"'.*

I have restarted both machines several times. I can ping Breezy's IP from XP, but not the Samba name ('breezy2'). I never get any password requests from the Breezy share, just error messages. I am stumped.

```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = POA2

# server string is the equivalent of the NT Description field
;   netbios name = %h_breezy
   netbios name = breezy2

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
   security = user
   username map = /etc/samba/smbusers

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
server string = cortana_smb
[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

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

```

---

### Post by seldenthuis on 2005-10-16
I used to have the same problem, but I was able to fix it by setting "security = share" in smb.conf. This makes file sharing a little less secure since you don't need passwords anymore. If that's not a problem for you then this will probably do the trick.

---

### Post by unclben on 2005-10-16
[QUOTE=seldenthuis]I used to have the same problem, but I was able to fix it by setting "security = share" in smb.conf.[/QUOTE]I just tried that, no luck. :(

At the same time, I decided to change the server name so I could see if Breezy and/or XP was trying access the 'old' share or the 'changed' share. Well, both OSes see both shares, even after refreshing the network browsers and rebooting!

---

### Post by matw on 2005-10-16
I got similar messages when the username on the XP and Ubuntu systems were different.

---

### Post by unclben on 2005-10-16
[QUOTE=matw]I got similar messages when the username on the XP and Ubuntu systems were different.[/QUOTE]In smbusers, I have my XP username tied to my Ubuntu username:
```
ben = "Ben"
``` Also, remember that I can't access the share from within Ubuntu either. I can see it, but not access it.

---

### Post by matw on 2005-10-16
I set SAMBA up a while ago, and I just can't remember all the details. However, I recall that I pretty much followed

[http://us1.samba.org/samba/docs/using_samba/ch02.html](http://us1.samba.org/samba/docs/using_samba/ch02.html)

Only I used aptitude to install smbclient, smbfs, and swat.
I couldn't get SWAT to work until I created a root account; however, in hindsight I think I could have used my user account name instead of "root" as shown in "chapter 2, Using SWAT".
I had a problem with user names.

HTH

---

### Post by evanderburg on 2005-10-16
I have read a number of posts about connecting to Windows shares through Samba but I cannot get any of the commands to work.  I tried smbclient and smbmount and neither let me connect to the Windows box.  The shares are fine on the Windows box because I can connect via my Mac.  Can anyone tell me what command I should type.  Also, I would love to be able to access the shares though the GUI but every time I double click on my Windows machine I get this error.  "The filename indicates that this is a desktop configuration file.  The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

I tried opening it via the file browser but it did not work.  Any suggestions?

---

### Post by veehell on 2005-12-06
Dudes, samba is big lunch a lotta people spent times on it so don't be frustrated 
Basically, you need to define how you want your samba act. There are a lot of options and to be more chaotic more versions of samba (and also version of "samba" on M$ OSes). 
Focus on "security" option in smb.conf and choose the proper one for your situation. as i remember there are share,user,domain. Each one need another type of authentification and on this depend other options in smb.conf which have to be in corelation. So start on the unsecure level (share) if you have problem and follow up to more secure ways (user,domain)
You need to have created(samba) or synced (unix<>samba) users with valid passwords (you have to specify which "program" you want to use to generate/edit passwords for samba user and also how you store and where you store the passwords.
Now you also need to know if you have WINS server, if you wish to use Netbios or dns to resolve names, or how the resolve process will be executed (which methods), or if you wish to be local master, domain master ....and etc.

The rest  "how set share" is simply and a lot of guis or templates are there on internet, or check my other thread [post]("http://ubuntuforums.org/showpost.php?p=548872&postcount=3") there are several links which explain my hints more deeply.

SWAT and their DOCumentations are perfect, each option is there specified with full help. you can use it as gui man and for generating more smb.conf to test them separately.

Ad_gui: i don't why but sometimes it work sometime not. command line, smbfs mounting, winbox browsing work ok, temporarily mounting via ("connect to server" GNOME) or Knomba2 works after many succesfull dialogs for authentifiation or creating "keyring" and store it for nautilus. It is not comfortable. :(

Why this not work ?
Because M$ have quite lot options how to access, resolve names, authentificate and so on. So on some configuration you have to enable more ports on your firewall. (as i remember 137-139, and also 319 and some others). So if you force samba to ask via 137 and have not enabled, you have noaccess. So you have know what you have enabled and how to deliver service. Also IPC$ is the issue of the GUI troubles i mean guest account for listing the shares and touching the machines. Even if you specify your valid account, you been rejected or error message displayed (saying something about unreachable machine or non existing folder and etc...) this could be caused by IPC$, guest account, non synced user, non existing user, wrongly stored password...


I hate samba at all ;)) , ftp is much better and more efficient...
For example same file, same sources, ftp 7-9M/s and samba 3.5M(in)/4.5M(out) constantly before tuning, after tunning 4.6IN/6.6OUT. I tunning time was 2hours :(

Start proftpd. ? 1min. > one port, one service, defined and correct protocol. Samba is quite anoing service :( with a lotta hidden issues :( and you have to read a lot to have it worked, but it is challenge so that's why i am still interest in.

ok here is my re:edited global section from smb.conf to inspirate
it working for now for linux which is not wins server, nmbd lose election to any "master" i could list machine from winbox, and acces my shares (not listed bellow)
and homes via "map network drive" with correct account name/password provided to dialog. Reverse accessing work with problems, but finally after few retries it proceed.

> 
# VH (SAMBA.CONFIGURATION file) 
# source: deb.how2;wiki,samba.org
#---------------------------------[0.23]

[global]
	#where and how to log >>
	log file = /var/log/samba/log.%m
	#tunning the speed of samba >>
	socket options = IPTOS_LOWDELAY TCP_NODELAY SO_RCVBUF=4096 SO_SNDBUF=4096
	#authentification 
	obey pam restrictions = yes
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
	# use DNS or netbios 
	dns proxy = yes
	server string = %h server
	# who is not allowed to use samba
	invalid users = root
	# default service
	default = homes
	workgroup = NETWORK23
	# write to syslog or to own log 
	syslog = 0
	# security acting
	security = user
	# here is panic action ;) script
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	# nmbd acting as wins ?
	wins support = no
	# ok no wins so where is the wins ?
	wins server = 10.0.0.23
	# guest account used for IPC$ scanning ;))
	guest account = nobody
	# election level 0-lose 255force (65 is enought to force over win2000/NT)
	os level = 23
	# MASTER section
	domain master = no
	local master = no
	preferred master = no
	# how to resolve names ? 
	name resolve order = lmhosts host wins bcast

PS: if you don't like SWAT you can use WEBMIN-samba package it is ok too ;) 
PSS: sorry for overflood but i am actually working on samba...so full of emotions.

---

### Post by unclben on 2005-12-06
Yesterday, for the purpose of repartitioning my drives, I wiped Breezy (upgraded from Hoary via apt) and started over again. Sure enough, samba worked like a charm on the clean Breezy install. The problem is [effectively] solved, though I still wish I knew what was giving me trouble before.

---

