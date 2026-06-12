---
title: "File sharing - Linux-mac-winxp"
date: 2006-03-06
forum: Desktop Environments
---

### Post by pinkpanther_bc on 2006-03-06
Have been looking around for help but cant find a simlpe solution!
I run ubuntu on my laptop (and dual boot tower) I want to access my windows files on the tower from the laptop. Have wirless router (Dlink)
I have Samba installed, but when i click on network servers i get the windows network, clicking on it nothing happens I dont show any of my shared files. So I have to configure something. What do i have to do (step by step)

I can access my windows files from the MAC i have, without configuring anything.
But no access from Ubuntu to either my mac or tower (windows)
There must be simple solution to this issue or can anyone post a simple guide.

Thanks

"free your mind and your *** will follow"

---

### Post by skirkpatrick on 2006-03-06
Is your workgroup properly defined in /etc/samba/smb.conf?

---

### Post by pinkpanther_bc on 2006-03-06
my settings are
workgroup = MSHOME
That is what i have on the windows machine! Do I need to change this?

---

### Post by skirkpatrick on 2006-03-07
As long as they match, you should be fine.  All you should need is Samba installed.

When I click on Network Servers, I see all the machines on my network, just like Windows does.  Then click on the machine and I see all it's shared folders.

Just out of curiosity, can you ping the machine's IP address?

---

### Post by pinkpanther_bc on 2006-03-08
Yes I can ping the IP adress 192.168.0.103, no problem there.
Still no access to the folders.
What is my next move?

---

### Post by skirkpatrick on 2006-03-09
Hmm, just poking around in the dark here as I also set my Ubuntu machine up to share files so I'm not sure what specific parts you need.  I've also installed, with apt-get, smbfs and smbclient.  You should be able to use smbclient to connect directly to a Windows share using the commandline to make sure it's working.

Just as a side note, I assume you've either rebooted the Ubuntu machine or restarted the Samba service after you set your workgroup?

---

### Post by pinkpanther_bc on 2006-03-09
Yes done reboot etc. And have smbfs and smbclient installed.

How do i use the sbmclient to connect with the command line?

This is what I have in gedit

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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

What if anything do I need to add here?
Thanks

---

### Post by skirkpatrick on 2006-03-09
Well, here's a copy of my /etc/samba/smb.conf file.  I have been told by others not to use "security=share" but I haven't gotten around to changing it yet to require passwords.

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
	log file = /var/log/samba/log.%m
	load printers = yes
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n
	obey pam restrictions = yes
	preserve case = yes
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	null passwords = yes
	encrypt passwords = true
	public = yes
	passdb backend = tdbsam guest
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	netbios name = PapaBear
	server string = Scott's Computer
	printing = cups
	invalid users = root
	workgroup = CLANKIRKPATRICK
	printcap name = cups
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	short preserve case = yes
	max log size = 1000
	wins support = no
	security = share


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
	path = /var/spool/samba
	guest ok = Yes
	writable = yes
	printable = Yes
	use client driver = yes
	disable spoolss = yes
	browseable = no
	Print command = lpr -r -P %p %s -U %u -o raw
	lprm command = /usr/bin/lprm -P %p %j




# Windows clients look for this share name as a source of downloadable
# printer drivers
;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
;   guest ok = no
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


[Scott]
path = /home/scott
available = yes
browseable = yes
public = yes
writable = yes


---

### Post by stig on 2006-03-09
Try Nautilus-Share:
[http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil](http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil)

It's really easy - even I was able to do it!

---

### Post by Erik6543 on 2006-03-09
After editing /etc/samba/smb.conf and restarting samba, did you create a password with "sudo smbpasswd -a <username>"? That did the trick for me.:cool:

---

