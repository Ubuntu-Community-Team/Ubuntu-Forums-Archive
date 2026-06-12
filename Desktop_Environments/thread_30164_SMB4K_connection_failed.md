---
title: "SMB4K connection failed"
date: 2005-04-27
forum: Desktop Environments
---

### Post by sonny on 2005-04-27
When I fisrt installed Kubuntu I got smb4k to show and mount the share folder from the computers connected to my network, I had to re-installed Kubuntu when I tried to get opengl to work (I messed up the kernel. but now I have it enable), that was over a month now and I haven't tried samba, now I have to install it (for sharing school work with my team), but everytime I want to connec to my mothers pc (that pc is my testing box...  :grin: ) it say:

"Conection to MYMOTHERPC failed"

I'm using smb4k, it detects the workgroup automatically. If I stop the searching process it shows the pc and the ip, if I scan the pc the error apears, if I stop the scan it shows nothing. Everything is fine with my mom's pc, the problem is mine. What is wrong with my network???

I have samba, smb4k and smbfs install. Some help over here.

---

### Post by segrewb on 2005-04-27
We will need to see your smb.conf file.
 
Also have you checked yours and your mothers firewall.  Make sure the ports needed for Samba are open.

Segrewb

---

### Post by sonny on 2005-04-27
We don't have a firewall per se.. just a router and the protection it gives  :neutral: ... my samba.conf file is listed below, let me tell you that before i didn't do any configuration in the file and it was running fine, I just did the configuration option granted by the GUI, because I'm not wise when it comes to configuring myself...  :roll:  

#======================= Global Settings =======================

[global]

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
encrypt passwords = yes

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
restrict anonymous = no
domain master = no
preferred master = no
workgroup = CASA
max protocol = NT
ldap ssl = No
server signing = Auto

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
create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

---

### Post by segrewb on 2005-04-27
Is the workgroup set to 'workgroup = CASA' on your mom's computer?  Also have you checked the samba log 'log file = /var/log/samba/log.%m'?

Segrewb

---

### Post by segrewb on 2005-04-27
Another trick may be to modify your lmhosts file 'default location  usually at /usr/local/samba/lib/lmhosts' and add your mom's ip address and netbios name.

Example

192.168.1.1     Mom_Computer

---

### Post by sonny on 2005-04-27
Well for the first thing... yes my mom's pc has the workgroup set as CASA, and the result for the log file is shown below, wich is correct, unless you say otherwise. 

> [2005/04/27 13:00:54, 0] nmbd/nmbd.c:main(668)
  Netbios nameserver version 3.0.10-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1994-2004
[2005/04/27 14:25:23, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
  
  Samba name server ARWEN is now a local master browser for workgroup CASA on subnet 10.105.88.19
  
  ***** 


As for the other file lmhosts I don't have it in my system, I did a search for it and there was none. Couldn't be that???

---

