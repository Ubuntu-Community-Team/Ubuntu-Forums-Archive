---
title: "Browsing from windows"
date: 2005-12-11
forum: General Help
---

### Post by Braveheart on 2005-12-11
I have just setup my pc with ubuntu but have a problem
I can get it to show up on windows network , i have setup samba , all looks good, But when i try to surf to my ubunto computer from win it asks me for a user name and password, Every name and password i enter is wrong,I Have tried everything with no success.I can see all my Win pc's from ubunt and there is no other networking problems, 
Here is my smb file , What if anyone knows do i need to change?

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
   workgroup = Leesnetwork

# server string is the equivalent of the NT Description field
   server string = lounge_ubuntu

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = yes

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
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = smbpasswd

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


[desktop]
path = /root/Desktop
available = yes
browseable = yes
public = yes
writable = yes

Its must be a password and user name thing but it has me stumped Please help me.... aaaaahhhhhhhhhhhhh:razz:

---

### Post by sabitha on 2005-12-11
create a SMB user, make sure this account exists on your Ubuntu Linux.

Code:

sudo smbpasswd -a `whoami`


and set your password ;)

---

### Post by Weman on 2005-12-21
Hi
I'm new to Ubuntu and Linux and had the same problem.

I read:
[http://ubuntuguide.org/#sharepublicfoldersreadsecurityshare](http://ubuntuguide.org/#sharepublicfoldersreadsecurityshare)
and followed these instructions, it did work fine.

I can access public folder i Ubuntu from winXP and all shared folders in XP from Ubuntu.

Note that you can choose method if you want read/write or to log in or not.

//weman

---

### Post by palmiter on 2005-12-23
The link in the previous post isn't working for me.  I just installed Ubuntu for my dad, and we are having the exact same problem as the original poster.  Any ideas on what password and username we should use from the Windows computer to access samba-shared files in Ubuntu (or, better asked, how I go finding/setting up this info)?

---

### Post by rcerreto on 2005-12-23
I agree with sabitha's suggestion.
You could also have to enable the created user:

sudo smbpasswd -e `whoami`

---

### Post by palmiter on 2005-12-23
awesome!! thank you everyone! after signing on through windows as "nameofcomputer/username" rather than simply "username" it worked flawlessly (and after enabling and setting up the password). This legitimizes linux for my dad, at least.

---

### Post by Braveheart on 2006-01-03
Cheers guys, Im the original poster, It worked perfect.
I went back to windows on my laptop now that i have this im a happy Ubuntu Traveler..
Thanks again:)

I used these commands

sudo smbpasswd -a `whoami`

sudo smbpasswd -e `whoami`

sudo testparm
sudo /etc/init.d/samba restart

Sign in with

nameofcomputer/username
Then Password

---

### Post by drraf on 2006-01-03
In my case this one helped when added to **/etc/samba/smb.conf**:
```

guest account = nobody
guest ok = yes

```
This allow guest browsing, so there is no user/password required when accessing your Ubuntu from Windows.
Dont forget to restart your samba after that change.

---

### Post by moon2js on 2006-01-11
[QUOTE=drraf]In my case this one helped when added to **/etc/samba/smb.conf**:
```

guest account = nobody
guest ok = yes

```
This allow guest browsing, so there is no user/password required when accessing your Ubuntu from Windows.
Dont forget to restart your samba after that change.[/QUOTE]

What if I want certain directories guest browsable and/or guest writable (like a dropbox)? Can I do that, but leave home directories private and only accessible to respective username/passwords?

---

### Post by moon2js on 2006-01-15
I'm trying to setup an ubuntu file server on a home network. I'd like to give access to home directories to users based on their login/password.

But I would also like to make some folders completely public and accessible to visitors without a username or password.

I don't want home directories accessible/viewable by visitors, but I'd like visitors to be able to browse public directories without being prompted for a password. Is that possible?

---

### Post by LxP on 2006-01-29
[QUOTE=moon2js]I'm trying to setup an ubuntu file server on a home network. I'd like to give access to home directories to users based on their login/password.

But I would also like to make some folders completely public and accessible to visitors without a username or password.

I don't want home directories accessible/viewable by visitors, but I'd like visitors to be able to browse public directories without being prompted for a password. Is that possible?[/QUOTE]
I would like to politely second moon2js' request for help. I would very much like to allow the users of our Ubuntu machine to access their home directories from Windows computers on the same network (all of which have no login procedures themselves), while at the same time offering uninhibited access to 'public' folders such as music and wallpaper collections.

From what I've read both on the forums and at [ubuntuguide.org]("http://ubuntuguide.org/") and from what I've tried, it doesn't seem very easy to both have credentials required for home directories *and* have completely free access to shared public resources (with no bothering login screens).

---

### Post by gatorbrit on 2006-01-29
An alternative approach on a dual boot machine is to install this:
[http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html")
in windows.  It automatically maps all linux drives when you start winxp and they appear in my computer automatically.  Its incredibly easy and requires no set up in ubuntu.

---

### Post by moon2js on 2006-02-10
[QUOTE=gatorbrit]An alternative approach on a dual boot machine is to install this:
[http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html")
in windows.  It automatically maps all linux drives when you start winxp and they appear in my computer automatically.  Its incredibly easy and requires no set up in ubuntu.[/QUOTE]

Yeah, I've played with this and it's cool for dual booting, but that doesn't solve the problem of browsing samba shares on an Ubuntu box from Windows/Mac boxen with the user setup mentioned a couple posts ago.

Anyone have ideas? [bump]

---

