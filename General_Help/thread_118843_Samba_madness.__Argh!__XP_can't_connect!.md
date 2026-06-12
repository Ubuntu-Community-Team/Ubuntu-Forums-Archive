---
title: "Samba madness.  Argh!  XP can't connect!"
date: 2006-01-17
forum: General Help
---

### Post by briguy on 2006-01-17
I'm trying to share my server with my XP box.  The box sees it fine under MSHOME (so does my Ubuntu laptop) however when I click on the server I can't access the files, XP says:

```
\\Bwserver is not accessible.  You might not have the permission to use this network resource.  Contact the administrator yadda yadda...

The network path was not found.
``` 
My smb.conf file is:

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
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h

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

[public]
   comment = Public Folder
   path = /home/storage/files
   public = yes
   writable = no
   create mask = 0777
   directory mask = 0777
   force user = nobody
   force group = nogroup
``` 

This is direct from ubuntuguide, I've just changed settings to suite my server.  I want to be able to connect without passwords etc.

I've checked the firewall (under firestarter) and the IP address is allowed, and I can FTP in.  I have a new (Cisco OS) WRT54G router, I can't see it being the problem but there it is if you think it's significant.  The XP box is connected via wireless, server is hard wired.

I can connect TO the XP box no problems.

Please, help me so the madness ends! ](*,)

---

### Post by dickohead on 2006-01-17
Use the IP address of the machine instead of the name:

\\192.168.1.5
not
\\bwserver

---

### Post by briguy on 2006-01-17
It sees Bwserver under network places.  Where would I enter the IP address?

---

### Post by briguy on 2006-01-17
Ok, I mapped the drive using the ip address and my username like so: \\192.168.2.2\username and it seems to work.  Thanks.

---

### Post by Granduke on 2006-02-02
I'm having the same problem, how did you map the drive using the ip address?

---

### Post by mrcbrown on 2006-02-02
In XP you can go under the file manager and on the top menu: Tools -> "Map Network Drive..."

I too have used the IP method, as even with my iBook it locks up hard on the Samba setup, but I have a few more tweaks on mine since I am just barely getting back to setting it up again.

---

### Post by jamie_alexander on 2007-09-14
> **dickohead said:**
> Use the IP address of the machine instead of the name:

\\192.168.1.5
not
\\bwserver

Thanks for that - I mapped a drive in XP using IP address and was able to connect (after I shared a drive in UBUNTU and connected to the correct share),  had to log in using my Ubuntu username and password but it worked a treat!

Does anyone have any idea if it's possible to see the Ubuntu machine in XP's network places? I've a few shares set up on Ubuntu but I don't want to have to map a network drive to each, nor do I want to share the root of the drive, I just want to browse from a laptop running XP and see the ubuntu machine in my network places.

I've a few more questions - viruses et al. - windows was plagued and decent antivirus/firewall/Security software was required - Nothing like that scale in Linux land I believe - any advice anyone?

Remote Access - through a browser, is it possible? I think it is but not to sure of what's best practice - again, I'd love to hear for anyone who can advise.


Aside from that,  I'm loving Ubuntu, only installed it a few days ago and slowly finding my way around, so apologies if the terminology isn't what it should be. No doubt I'll have some more questions but I'm not too sure I should be posting in here - kinda got off on a tangent after the networking bits! Anyway, thanks -  so far, so good!

lang may yer lum reek!

Slàinte mhor,

Jamie

---

### Post by JBAlaska on 2007-09-14
> I've a few more questions - viruses et al. - windows was plagued and decent antivirus/firewall/Security software was required - Nothing like that scale in Linux land I believe - any advice anyone?

I believe viruses are few and far between in the Linux world, but after having it ingrained in us in windoze I for one felt kinda naked without a high powered virus scanner installed (With a nice GUI to boot) Check out the free version of Avast for linux, I used Avast with great success in winblows and the Linux version is nice as well.
```
http://www.avast.com/eng/download-avast-for-linux-edition.html
```
Just fill out a short form and you'll get a key by e-mail.

As far as a Firewall Ubuntu comes pre-configured with iptables, an easy way to manage them with a GUI interface is FireStarter.

> Remote Access - through a browser, is it possible? I think it is but not to sure of what's best practice - again, I'd love to hear for anyone who can advise.

When you installed Ubuntu the web server software should have been installed by default and accessing on a LAN is as simple as entering your URL in a browser, If you want to access from the internet you will have to either have a static external IP or use a free service like no-ip.com.

If you want to remote access another computer from Ubuntu, use Terminal Server Client (in the internet menu)

---

