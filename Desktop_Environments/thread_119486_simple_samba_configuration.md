---
title: "simple samba configuration?"
date: 2006-01-19
forum: Desktop Environments
---

### Post by moephan on 2006-01-19
Hello,

Our situation is that we have installed Ubuntu on a desktop machine connected to a printer. Ubuntu is working perfectly and the printer is working perfectly. The next step is to make it play nicely with family's XP laptop. We need to be able to use the printer connected to the desktop and also need to be able to access home directories on the desktop from the laptop. 

Before we invest a whole weekend day, could someone let me know if it looks like this solution will work? Here is what I think might be the right smb.conf file:
[global]
workgroup = OURWGNAME
netbios name = ubuntudesktop
printing = CUPS
printcap name = CUPS
map to guest = Bad User
show add printer wizard = No
wins support = yes

[printers]
comment = Print Temporary Spool Configuration
path = /var/spool/samba
printable = Yes
guest ok = Yes
use client driver = Yes
browseable = No

[homes]
comment = Home Directories
browseable = yes
writable = yes
create mask = 0700
directory mask = 0700

Then I think we need to take the following steps:
1. put this in the right directory
2. use sudo smbpasswd -a `whoami` to create passwords for everyone who will access files
3. restart samba (?)
4. on the XP laptop go \\OURWGNAME, click on homes, log in, and see your files
5. on the XP laptop use "add printer" choose network printer, and muddle through the wizard

Any help anticipating problems are providing better alternative solutions would be very much appreciated. Thanks much.

---

### Post by Azion on 2006-01-19
From what I can see everything is text book.
Of course it could be different in practice.

Try it, and post back with any errors

---

### Post by moephan on 2006-01-23
After some jiggering, it worked. We are able to print from all the laptops, and are able to browse home directories. We had to do some tweaks to get it to work like this:

1. To get printing to work we set the spool path to be "path = /var/spool/cups" since the directory was already there. Then I had to chmod the directory to give everyone read/write/execute permissions on it.

2. To get access to home directories on the desktop, we had to ensure that everyone had the same username and password on the ubuntu desktop, in samba, and on windows.

3. One of the windows usernames didn't work because it had a space in it, and we couldn't set up a user name like that in Ubuntu. Printing did work because we let guests print.

4. We twice ended up rebooting Ubuntu to get the windows laptops to see the new samba configurations.

5. We didn't include the "netbios name" setting because samba automatically picked up the name we gave when we installed Ubuntu.

The windows laptops don't really seem to notice that the Ubuntu desktop is not also windows. It has icons in all the same places, the printer shows up in all the same places, etc...  Please let me know if this is not an optimal solution for secutiry or maintenance reasons, etc... I will probably use this smb.conf and this process as a template for other home networking situations, so any feedback would be appreciated.

Cheers, Rick

---

### Post by lance bermudez on 2006-02-01
i have used the above config and added the users with smbpasswd. i have got the samba config set up and can see my printer and home folder but can not access my printer from my window 2000 computer or my home folder. the printer gives me the following error "the server on which the printer resides does not have the correct printer driver installed. if you want to install the driver on your local computer, click here" window 2000 does not have the driver i need for my printer but breezy does. and for my homes folder i receive the following error " the network name cannot be found" i also do not under stand the step that says "1. To get printing to work we set the spool path to be "path = /var/spool/cups" since the directory was already there. Then I had to chmod the directory to give everyone read/write/execute permissions on it." how do i add the read/write/execute part and where do i put them.  also from the windows 2000 box i do not have to give a user name or password any more i did it once when i first connected but not any more and i receive the same error no matter if i go to the network neighborhood icon or go to start and enter my Linux ip address. either way i don't have to enter a user name or password and still get the same errors. im new to Linux and samba. below is a copy of my smb.config please email me any help at [email]bermudezlance@hotmail.com[/email]
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
   workgroup = LBERMUDEZ

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes 

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

 map to guest = Bad User
 show add printer wizard = No

[homes]
   comment = Home Directories
   path = /home/lance
   browseable = yes
   writable = yes
   create mask = 0700
   directory mask = 0700

[printers]
   comment = All Printers
   path = /var/spool/cups
   printable = Yes
   guest ok = Yes
   use client driver = No
   browseable = No

---

### Post by lance bermudez on 2006-02-03
my printer is attached to my linux box and no mater if i change the ""use client driver" line to = yes or no i get the error "server does not have the corret printer driver click yes to install from the local computer. i was able to find my hp PSC-750 disk and install the windows 2000 printer driver but it will not print a test page but will install the network printer from the linux box. Also i recive the error that from my linux box when i connect to the windows shared folder that the contains of the folder can not be displayed. below is my new smb.conf
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = LBERMUDEZ

# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
wins support = yes

#authentication
security = share

# CUPS printing. See also the cupsaddsmb( manpage in the
# cupsys-client package.
printing = cups
printcap name = cups

map to guest = Bad User
show add printer wizard = No

[homes]
comment = Home Directories
path = /home/lance
browseable = yes
writable = yes
create mask = 0700
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/cups
printable = Yes
guest ok = Yes
use client driver = Yes
browseable = No

---

### Post by lance bermudez on 2006-02-05
First let that I’m printing from windows 2000 to Ubuntu breezy badger where my HP PSC 750 printer is attached. And the files can be shared from the Ubuntu breezy badger to the windows but not from the windows to the breezy badger. Make sure samba, samba-common, smbclient, smbfs, libsmbclient, and libsmbclient-dev are installed.  Also make sure the printer is installed by using system administraton printing then click add printer. Now to get started the commands that need to be typed in are surrounded by “” and have to be typed in terminal using “sudo su –“ to use super user the password will be you login password. Terminal is open by clicking applications then accessories then terminal. To get this to work you have to have all to the three user mathch user names and password they are windows user, Linux user, and samba user. With the “smbpasswd –a username” hit enter and put in the password also you will have to add the root user to samba “smbpasswd –a root” this is for administration use. Then edit the smb.conf file of samba with “vi /etc/samba/smb.conf” to match what is below. To add the changes press the insert key on the key board and make it look like what is below

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
   workgroup = LBERMUDEZ

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

#authentication
security = user


# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   load printers = yes
   printing = cups
   printcap name = cups

  show add printer wizard = No

[homes]
   comment = Home Directories
   path = /home/lance
   browseable = yes
   writable = yes
   create mask = 0700
   directory mask = 0700

[printers]
   comment = All Printers
   path = /tmp
   printable = Yes
   guest ok = Yes
  public = yes 
  use client driver = No
   browseable = Yes
  printer admin = root

[print$]
  comment = Printer Drivers
  path = /var/lib/samba/printer
  browseable = yes
  read only = yes
  guest ok = yes
  write list = root

when you have typed what is above save it by pressing the esc key to exit the insert mode then press shift q then type exit. Restart samba by typing “/etc/init.d/samba restart” then type “cupsaddsmb –U root –v –a “ hit enter then enter the password that you used for the samba root account. This will add the driver to samba for the printer.  If you need help understanding this part read this web page at [http://www.linuxdevcenter.com/pub/a/linux/2005/01/13/lnxckbk_samba.html](http://www.linuxdevcenter.com/pub/a/linux/2005/01/13/lnxckbk_samba.html)
after the drivers have been copied reedit the smb.conf file and change the “security = user” part to “security = share” under #authentication comment and save and restart samba. To get printing to work download the adobe program and adobe ppd toward the botton of page from the url to the windows 2000 box. on the Ubuntu box type “/etc/cups/ppd”  hit enter then type “ls” find your printer and whrite down its name they type “cp printer name /home/shared folder name” then type “cd /usr/share/cups/model/hplip” hit enter type “ls” find your printer then type “cp printer /home/shared folder name” on the windows 2000 box connect to the Ubuntu share and copy the printer files to windows 2000. unzip the adobe ppd program and where ever you copy it to past the printer files you copied from Ubuntu into it the run the adobe program and install the printer.

---

### Post by lance bermudez on 2006-02-06
does anyone know how i can get to my windows box folder i have set up to share from my linux box? i have tryed just the server address and folder name, also i have tryed  server address, folder name, and share name and i just get the same errors from both ways saying that the contents of the folder can not be displayed. and if i try to browse the server from the network neighborhood none of the password and user names work to access the windows box.

---

### Post by skirkpatrick on 2006-02-07
lance, check one of your other topics, I replied there.

moephan, if you set security=share, your Windows boxes don't have to have usernames/passwords to access the files.  I also found that XP has better response to the printer if you use Cups to share the printer and that 98 machines work better with Samba shared printers.  My machine shares the printer through both as my house has both XP and 98.  Here's a copy of my smb.conf:
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


and my cupsd.conf:
> 
#
# "$Id: cupsd.conf.in,v 1.17 2005/01/03 19:29:45 mike Exp $"
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.
#
#   Copyright 1997-2005 by Easy Software Products, all rights reserved.
#
#   These coded instructions, statements, and computer programs are the
#   property of Easy Software Products and are protected by Federal
#   copyright law.  Distribution and use rights are outlined in the file
#   "LICENSE.txt" which should have been included with this file.  If this
#   file is missing or damaged please contact Easy Software Products
#   at:
#
#       Attn: CUPS Licensing Information
#       Easy Software Products
#       44141 Airport View Drive, Suite 204
#       Hollywood, Maryland 20636 USA
#
#       Voice: (301) 373-9600
#       EMail: [email]cups-info@cups.org[/email]
#         WWW: [http://www.cups.org](http://www.cups.org)
#

########################################################################
#                                                                      #
# This is the CUPS configuration file.  If you are familiar with       #
# Apache or any of the other popular web servers, we've followed the   #
# same format.  Any configuration variable used here has the same      #
# semantics as the corresponding variable in Apache.  If we need       #
# different functionality then a different name is used to avoid       #
# confusion...                                                         #
#                                                                      #
########################################################################


########
######## Server Identity
########

#
# ServerName: the hostname of your server, as advertised to the world.
# By default CUPS will use the hostname of the system.
#
# To set the default server used by clients, see the client.conf file.
#

#ServerName myhost.domain.com

#
# ServerAdmin: the email address to send all complaints/problems to.
# By default CUPS will use "root@hostname".
#

#ServerAdmin [email]root@your.domain.com[/email]


########
######## Server Options
########

#
# AccessLog: the access log file; if this does not start with a leading /
# then it is assumed to be relative to ServerRoot.  By default set to
# "/var/log/cups/access_log"
#
# You can also use the special name "syslog" to send the output to the
# syslog file or daemon.
#

#AccessLog /var/log/cups/access_log

#
# Classification: the classification level of the server.  If set, this
# classification is displayed on all pages, and raw printing is disabled.
# The default is the empty string.
#

#Classification classified
#Classification confidential
#Classification secret
#Classification topsecret
#Classification unclassified

#
# ClassifyOverride: whether to allow users to override the classification
# on printouts. If enabled, users can limit banner pages to before or
# after the job, and can change the classification of a job, but cannot
# completely eliminate the classification or banners.
#
# The default is off.
#

#ClassifyOverride off

#
# DataDir: the root directory for the CUPS data files.
# By default "/usr/share/cups".
#

#DataDir /usr/share/cups

#
# DefaultCharset: the default character set to use. If not specified,
# defaults to "utf-8".  Note that this can also be overridden in
# HTML documents...
#

DefaultCharset notused

#
# DefaultLanguage: the default language if not specified by the browser.
# If not specified, the current locale is used.
#

#DefaultLanguage en

#
# DocumentRoot: the root directory for HTTP documents that are served.
# By default "/usr/share/cups/doc-root".
#

#DocumentRoot /usr/share/cups/doc-root

#
# ErrorLog: the error log file; if this does not start with a leading /
# then it is assumed to be relative to ServerRoot.  By default set to
# "/var/log/cups/error_log"
#
# You can also use the special name "syslog" to send the output to the
# syslog file or daemon.
#

#ErrorLog /var/log/cups/error_log

#
# FileDevice: determines whether the scheduler will allow new printers
# to be added using device URIs of the form "file:/foo/bar". The default
# is not to allow file devices due to the potential security vulnerability
# and due to the fact that file devices do not support raw printing.
#

#FileDevice No


#
# FontPath: the path to locate all font files (currently only for pstoraster)
# By default "/usr/share/cups/fonts".
#

#FontPath /usr/share/cups/fonts

#
# LogLevel: controls the number of messages logged to the ErrorLog
# file and can be one of the following:
#
#     debug2	Log everything.
#     debug	Log almost everything.
#     info      Log all requests and state changes.
#     warn      Log errors and warnings.
#     error     Log only errors.
#     none      Log nothing.
#

LogLevel info

#
# MaxLogSize: controls the maximum size of each log file before they are
# rotated.  Defaults to 1048576 (1MB).  Set to 0 to disable log rotating.
#

#MaxLogSize 0

#
# PageLog: the page log file; if this does not start with a leading /
# then it is assumed to be relative to ServerRoot.  By default set to
# "/var/log/cups/page_log"
#
# You can also use the special name "syslog" to send the output to the
# syslog file or daemon.
#

#PageLog /var/log/cups/page_log

#
# PreserveJobHistory: whether or not to preserve the job history after a
# job is completed, cancelled, or stopped.  Default is Yes.
#

#PreserveJobHistory Yes

#
# PreserveJobFiles: whether or not to preserve the job files after a
# job is completed, cancelled, or stopped.  Default is No.
#

#PreserveJobFiles No

#
# AutoPurgeJobs: automatically purge jobs when not needed for quotas.
# Default is No.
#

#AutoPurgeJobs No

#
# MaxCopies: maximum number of copies that a user can request. Default is
# 100.
#

#MaxCopies 100

#
# MaxJobs: maximum number of jobs to keep in memory (active and completed.)
# Default is 500; the value 0 is used for no limit.
#

#MaxJobs 500

#
# MaxJobsPerPrinter: maximum number of active jobs per printer. The default
# is 0 for no limit.
#

#MaxJobsPerPrinter 0

#
# MaxJobsPerUser: maximum number of active jobs per user. The default
# is 0 for no limit.
#

#MaxJobsPerUser 0

#
# MaxPrinterHistory: controls the maximum number of history collections
# in the printer-state-history attribute.  Set to 0 to disable history
# data.
#

#MaxPrinterHistory 10

#
# Printcap: the name of the printcap file.  Default is /etc/printcap.
# Leave blank to disable printcap file generation.
#

Printcap /var/run/cups/printcap

#
# PrintcapFormat: the format of the printcap file, currently either
# BSD or Solaris.  The default is "BSD".
#

#PrintcapFormat BSD
#PrintcapFormat Solaris

#
# PrintcapGUI: the name of the GUI options panel program to associate
# with print queues under IRIX.  The default is "/usr/bin/glpoptions"
# from ESP Print Pro.
#
# This option is only used under IRIX; the options panel program
# must accept the "-d printer" and "-o options" options and write
# the selected printer options back to stdout on completion.
#

#PrintcapGUI /usr/bin/glpoptions

#
# RequestRoot: the directory where request files are stored.
# By default "/var/spool/cups".
#

#RequestRoot /var/spool/cups

#
# RemoteRoot: the name of the user assigned to unauthenticated accesses
# from remote systems.  By default "remroot".
#

#RemoteRoot remroot

#
# ServerBin: the root directory for the scheduler executables.
# By default "/usr/lib/cups".
#

#ServerBin /usr/lib/cups

#
# ServerRoot: the root directory for the scheduler.
# By default "/etc/cups".
#

#ServerRoot /etc/cups


#
# ServerTokens: specifies what information in provided in the Server
# header of HTTP responses. The default is Minor.
#
# ServerTokens None
# ServerTokens ProductOnly       CUPS
# ServerTokens Major             CUPS/1
# ServerTokens Minor             CUPS/1.1
# ServerTokens Minimal           CUPS/1.1.23
# ServerTokens OS                CUPS/1.1.23 (uname)
# ServerTokens Full              CUPS/1.1.23 (uname) IPP/1.1
#

#ServerTokens Minor


########
######## Fax Support
########

#
# FaxRetryLimit: the number of times a fax job is retried.
# The default is 5 times.
#

#FaxRetryLimit 5

#
# FaxRetryInterval: the number of seconds between fax job retries.
# The default is 300 seconds/5 minutes.
#

#FaxRetryInterval 300


########
######## Encryption Support
########

#
# ServerCertificate: the file to read containing the server's certificate.
# Defaults to "/etc/cups/ssl/server.crt".
#

#ServerCertificate /etc/cups/ssl/server.crt

#
# ServerKey: the file to read containing the server's key.
# Defaults to "/etc/cups/ssl/server.key".
#

#ServerKey /etc/cups/ssl/server.key


########
######## Filter Options
########

#
# User/Group: the user and group the server runs under.  Normally this
# must be cupsys and lpadmin, however you can configure things for another
# user or group as needed.
#
# Note: the server must be run initially as root to support the
# default IPP port of 631.  It changes users whenever an external
# program is run, or if the RunAsUser directive is specified...
#

#User cupsys
#Group lpadmin

#
# RunAsUser: The RunAsUser directive controls whether the scheduler runs as the
# unpriviledged user account (usually cupsys). The default is No which
# leaves the scheduler running as the root user. However, the Debian package
# was prepared to work as user cupsys, which greatly reduces the impact of
# security holes.
#
# Note: Running as a non-priviledged user may prevent LPD and locally connected
# printers from working due to permission problems. The lpd backend will
# automatically use a non-priviledged mode that is not 100% compliant with RFC
# 1179. The parallel, serial, and usb backends will need write access to the
# corresponding device files.
#

RunAsUser No

#
# RIPCache: the amount of memory that each RIP should use to cache
# bitmaps.  The value can be any real number followed by "k" for
# kilobytes, "m" for megabytes, "g" for gigabytes, or "t" for tiles
# (1 tile = 256x256 pixels.)  Defaults to "8m" (8 megabytes).
#

#RIPCache 8m

#
# TempDir: the directory to put temporary files in.  This directory must be
# writable by the user defined above!  Defaults to "/var/spool/cups/tmp" or
# the value of the TMPDIR environment variable.
#

#TempDir /var/spool/cups/tmp

#
# FilterLimit: sets the maximum cost of all job filters that can be run
# at the same time.  A limit of 0 means no limit.  A typical job may need
# a filter limit of at least 200; limits less than the minimum required
# by a job force a single job to be printed at any time.
#
# The default limit is 0 (unlimited).
#

#FilterLimit 0

########
######## Network Options
########

#
# Ports/addresses that we listen to.  The default port 631 is reserved
# for the Internet Printing Protocol (IPP) and is what we use here.
#
# You can have multiple Port/Listen lines to listen to more than one
# port or address, or to restrict access:
#
#    Port 80
#    Port 631
#    Listen hostname
#    Listen hostname:80
#    Listen hostname:631
#    Listen 1.2.3.4
#    Listen 1.2.3.4:631
# 
# NOTE: Unfortunately, most web browsers don't support TLS or HTTP Upgrades
# for encryption.  If you want to support web-based encryption you'll
# probably need to listen on port 443 (the "https" port...)
#
# NOTE 2: In order for the command-line and web interfaces to work, you
# must have at least one Port or Listen line that allows access from the
# local loopback address (localhost).
#

#Port 80
#Port 443
Port 631
#
#Listen 127.0.0.1:631

#
# HostNameLookups: whether or not to do lookups on IP addresses to get a
# fully-qualified hostname.  This defaults to Off for performance reasons...
#

#HostNameLookups On

#
# KeepAlive: whether or not to support the Keep-Alive connection
# option.  Default is on.
#

#KeepAlive On

#
# KeepAliveTimeout: the timeout before Keep-Alive connections are
# automatically closed.  Default is 60 seconds.
#

#KeepAliveTimeout 60

#
# MaxClients: controls the maximum number of simultaneous clients that
# will be handled.  Defaults to 100.
#

#MaxClients 100

#
# MaxClientsPerHost: controls the maximum number of simultaneous clients that
# will be handled from a specific host.  Defaults to 10 or 1/10th of the
# MaxClients setting, whichever is larger.  A value of 0 specifies the
# automatic (10 or 1/10th) setting.
#

#MaxClientsPerHost 0

#
# MaxRequestSize: controls the maximum size of HTTP requests and print files.
# Set to 0 to disable this feature (defaults to 0.)
#

#MaxRequestSize 0

#
# Timeout: the timeout before requests time out.  Default is 300 seconds.
#

#Timeout 300


########
######## Browsing Options
########

#
# Browsing: whether or not to broadcast and/or listen for CUPS printer
# information on the network. For Ubuntu, this setting has been externalized to
# a separate configuration file cupsd-browsing.conf. This allows to change the
# browsing setting with /usr/share/cups/enable_browsing (or manually) without
# modifying this main configuration file, which avoids dpkg questions on
# conffile upgrades.

Include cupsd-browsing.conf

#
# BrowseProtocols: which protocols to use for browsing.  Can be
# any of the following separated by whitespace and/or commas:
#
#     all  - Use all supported protocols.
#     cups - Use the CUPS browse protocol.
#     slp  - Use the SLPv2 protocol.
#
# The default is "cups".
#
# NOTE: If you choose to use SLPv2, it is *strongly* recommended that
#       you have at least one SLP Directory Agent (DA) on your
#       network.  Otherwise, browse updates can take several seconds,
#       during which the scheduler will not respond to client
#       requests.
#

#BrowseProtocols cups

#
# BrowseAddress: specifies a broadcast address to be used.  By
# default browsing information is not sent!
#
# Note: HP-UX does not properly handle broadcast unless you have a
# Class A, B, C, or D netmask (i.e. no CIDR support).
#
# Note: Using the "global" broadcast address (255.255.255.255) will
# activate a Linux demand-dial link with the default configuration.
# If you have a LAN as well as the dial-up link, use the LAN's
# broadcast address.
#
# The @LOCAL address broadcasts to all non point-to-point interfaces.
# For example, if you have a LAN and a dial-up link, @LOCAL would
# send printer updates to the LAN but not to the dial-up link.
# Similarly, the @IF(name) address sends to the named network
# interface, e.g. @IF(eth0) under Linux.  Interfaces are refreshed
# automatically (no more than once every 60 seconds), so they can
# be used on dynamically-configured interfaces, e.g. PPP, 802.11, etc.
#

#BrowseAddress x.y.z.255
#BrowseAddress x.y.255.255
#BrowseAddress x.255.255.255
#BrowseAddress 255.255.255.255
BrowseAddress @LOCAL
#BrowseAddress @IF(name)

#
# BrowseShortNames: whether or not to use "short" names for remote printers
# when possible (e.g. "printer" instead of "printer@host".)  Enabled by
# default.
#

#BrowseShortNames Yes

#
# BrowseAllow: specifies an address mask to allow for incoming browser
# packets. The default is to allow packets from all addresses.
#
# BrowseDeny: specifies an address mask to deny for incoming browser
# packets. The default is to deny packets from no addresses.
#
# Both "BrowseAllow" and "BrowseDeny" accept the following notations for
# addresses:
#
#     All
#     None
#     *.domain.com
#     .domain.com
#     host.domain.com
#     nnn.*
#     nnn.nnn.*
#     nnn.nnn.nnn.*
#     nnn.nnn.nnn.nnn
#     nnn.nnn.nnn.nnn/mm
#     nnn.nnn.nnn.nnn/mmm.mmm.mmm.mmm
#     @LOCAL
#     @IF(name)
#
# The hostname/domainname restrictions only work if you have turned hostname
# lookups on!
#

#BrowseAllow address
#BrowseDeny address

#
# BrowseInterval: the time between browsing updates in seconds.  Default
# is 30 seconds.
#
# Note that browsing information is sent whenever a printer's state changes
# as well, so this represents the maximum time between updates.
#
# Set this to 0 to disable outgoing broadcasts so your local printers are
# not advertised but you can still see printers on other hosts.
#

#BrowseInterval 30

#
# BrowseOrder: specifies the order of BrowseAllow/BrowseDeny comparisons.
#

#BrowseOrder allow,deny
#BrowseOrder deny,allow

#
# BrowsePoll: poll the named server(s) for printers
#

#BrowsePoll address:port

#
# BrowsePort: the port used for UDP broadcasts.  By default this is
# the IPP port; if you change this you need to do it on all servers.
# Only one BrowsePort is recognized.
#

#BrowsePort 631

#
# BrowseRelay: relay browser packets from one address/network to another.
#

#BrowseRelay source-address destination-address
#BrowseRelay @IF(src) @IF(dst)

#
# BrowseTimeout: the timeout for network printers - if we don't
# get an update within this time the printer will be removed
# from the printer list.  This number definitely should not be
# less the BrowseInterval value for obvious reasons.  Defaults
# to 300 seconds.
#

#BrowseTimeout 300

#
# ImplicitClasses: whether or not to use implicit classes.
#
# Printer classes can be specified explicitly in the classes.conf
# file, implicitly based upon the printers available on the LAN, or
# both.
#
# When ImplicitClasses is On, printers on the LAN with the same name
# (e.g. Acme-LaserPrint-1000) will be put into a class with the same
# name. This allows you to setup multiple redundant queues on a LAN
# without a lot of administrative difficulties.  If a user sends a
# job to Acme-LaserPrint-1000, the job will go to the first available
# queue.
#
# Enabled by default.
#

#ImplicitClasses On

#
# ImplicitAnyClasses: whether or not to create "AnyPrinter" implicit
# classes.
#
# When ImplicitAnyClasses is On and a local queue of the same name
# exists, e.g. "printer", "printer@server1", "printer@server1", then
# an implicit class called "Anyprinter" is created instead.
#
# When ImplicitAnyClasses is Off, implicit classes are not created
# when there is a local queue of the same name.
#
# Disabled by default.
#

#ImplicitAnyCLasses Off

#
# HideImplicitMembers: whether or not to show the members of an
# implicit class.
#
# When HideImplicitMembers is On, any remote printers that are
# part of an implicit class are hidden from the user, who will
# then only see a single queue even though many queues will be
# supporting the implicit class.
#
# Enabled by default.
#

#HideImplicitMembers On


########
######## Security Options
########

#
# SystemGroup: the group name for "System" (printer administration)
# access.  The default varies depending on the operating system, but
# will be "sys", "system", or "root" (checked for in that order.)
#
# Debian: The default CUPS group is "lpadmin".
#

#SystemGroup lpadmin

#
# RootCertDuration: How frequently the root certificate is regenerated.
# Defaults to 300 seconds.
#

#RootCertDuration 300

#
# Access permissions for each directory served by the scheduler.
# Locations are relative to DocumentRoot...
#
# AuthType: the authorization to use:
#
#    None   - Perform no authentication
#    Basic  - Perform authentication using the HTTP Basic method.
#    Digest - Perform authentication using the HTTP Digest method.
#
#    (Note: local certificate authentication can be substituted by
#           the client for Basic or Digest when connecting to the
#           localhost interface)
#
# AuthClass: the authorization class; currently only "Anonymous", "User",
# "System" (valid user belonging to group SystemGroup), and "Group"
# (valid user belonging to the specified group) are supported.
#
# AuthGroupName: the group name for "Group" authorization.
#
# Order: the order of Allow/Deny processing.
#
# Allow: allows access from the specified hostname, domain, IP address,
# network, or interface.
#
# Deny: denies access from the specified hostname, domain, IP address,
# network, or interface.
#
# Both "Allow" and "Deny" accept the following notations for addresses:
#
#     All
#     None
#     *.domain.com
#     .domain.com
#     host.domain.com
#     nnn.*
#     nnn.nnn.*
#     nnn.nnn.nnn.*
#     nnn.nnn.nnn.nnn
#     nnn.nnn.nnn.nnn/mm
#     nnn.nnn.nnn.nnn/mmm.mmm.mmm.mmm
#     @LOCAL
#     @IF(name)
#
# The host and domain address require that you enable hostname lookups
# with "HostNameLookups On" above.
#
# The @LOCAL address allows or denies from all non point-to-point
# interfaces.  For example, if you have a LAN and a dial-up link,
# @LOCAL could allow connections from the LAN but not from the dial-up
# link.  Similarly, the @IF(name) address allows or denies from the
# named network interface, e.g. @IF(eth0) under Linux.  Interfaces are
# refreshed automatically (no more than once every 60 seconds), so
# they can be used on dynamically-configured interfaces, e.g. PPP,
# 802.11, etc.
#
# Encryption: whether or not to use encryption; this depends on having
# the OpenSSL library linked into the CUPS library and scheduler.
#
# Possible values:
#
#     Always       - Always use encryption (SSL)
#     Never        - Never use encryption
#     Required     - Use TLS encryption upgrade
#     IfRequested  - Use encryption if the server requests it
#
# The default value is "IfRequested".
#

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*
</Location>

#<Location /classes>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#</Location>

#<Location /classes/name>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#</Location>

<Location /jobs>
#
# You may wish to limit access to job operations, either with Allow
# and Deny lines, or by requiring a username and password.
#
AuthType Basic
AuthClass User
</Location>

#<Location /printers>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#</Location>

#<Location /printers/name>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#

## Anonymous access (default)
#AuthType None

## Require a username and password (Basic authentication)
#AuthType Basic
#AuthClass User

## Require a username and password (Digest/MD5 authentication)
#AuthType Digest
#AuthClass User

## Restrict access to local domain
#Order Deny,Allow
#Deny From All
#Allow From .mydomain.com
#</Location>

<Location /admin>
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks.  You can change
# the group name using the SystemGroup directive.
#

AuthType Basic
AuthClass System

## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
#Encryption Required
</Location>

#
# End of "$Id: cupsd.conf.in,v 1.17 2005/01/03 19:29:45 mike Exp $".
#


---

### Post by lance bermudez on 2006-02-07
thank you for your help with the printing but do what do you know about accessing a window 2000 share from my ubuntu breezy box. windows has nfts file system and ubuntu has ex2. do i need to set up a fat partinton on my windows 2000 box as a share? But i not shure if i need to becuse my windows box can access my ubuntu shares with on problem. i have the same user and password for ubuntu, samba and windows. i have tryied 

mount //192.168.3.2/wshare media/wshare -o username=mother,password=mom,dmask=777,famask=777

it gives me an error say that i need to say what the file system is so i look around the forms and tried this

mount -t smbts -o username=mother,password=mom,dmask=777,famask=777 //192.168.3.2/wshare media/wshare
and it errors out to but saying that the user is wrong or something like that im on my windows box because my my modem runs faster on windows then when on ubuntu because im to cheep to pay for the full driver

---

### Post by skirkpatrick on 2006-02-08
[QUOTE=lance bermudez]thank you for your help with the printing but do what do you know about accessing a window 2000 share from my ubuntu breezy box. windows has nfts file system and ubuntu has ex2. do i need to set up a fat partinton on my windows 2000 box as a share? But i not shure if i need to becuse my windows box can access my ubuntu shares with on problem. i have the same user and password for ubuntu, samba and windows. i have tryied 

mount //192.168.3.2/wshare media/wshare -o username=mother,password=mom,dmask=777,famask=777

it gives me an error say that i need to say what the file system is so i look around the forms and tried this

mount -t smbts -o username=mother,password=mom,dmask=777,famask=777 //192.168.3.2/wshare media/wshare
and it errors out to but saying that the user is wrong or something like that im on my windows box because my my modem runs faster on windows then when on ubuntu because im to cheep to pay for the full driver[/QUOTE]

Using Samba hides what file system is actually used on the machine.  The user message you are seeing is probably because the mount command only works for the root user or using sudo.  The command should be: **sudo mount -t smbfs -o username=mother,passwork=mom,dmask=0777,fmask=0777 //192.168.3.2/wshare /media/wshare**.

---

### Post by lance bermudez on 2006-02-08
i have been using sudo. but the only thing i have done differnert is install the program that lets windows browse the ext2 file system. the program is at [http://www.fs-driver.org/extendeddl.html](http://www.fs-driver.org/extendeddl.html) could this be a problem?

---

### Post by skirkpatrick on 2006-02-08
That program is used if you have a dual-boot system so that when you boot Windows, it can read your ext2/ext3 partitions.  It shouldn't have anything to do with networking.

---

### Post by lance bermudez on 2006-02-09
i have been using sudo but the error i get says "8316: session setup failed: ERRDOS- ERRnoaccess (Access deined) smb connectin failed" does this mean i have to do something to the windows share folder?

---

### Post by skirkpatrick on 2006-02-09
Are you sure your Windows machine is sharing?  Can you check it from another Windows machine?  You should also be able, in Ubuntu, to go to Places->Network Servers and find it there.

---

### Post by lance bermudez on 2006-02-09
my windows xp box can see the win2000 share but ubuntu ask for a password when i go their and no matter which user i use it can not access the windows 2000 share. all the user have been added using smbpasswd -a. and the windows user are the same for ubuntu and samba. from looking around the forms i see where some people have smbclient in their /etc/samba folder all i have is smb.conf somting for dhcp somthing else and a file called smbpasswd. should i have a smbclient? Also i have the ubuntu setup as a wins server is that why i can not access the window 2000 box and the windows xp is a dual boot with the  ubuntu breezybadger

---

### Post by skirkpatrick on 2006-02-10
I don't know if having Ubuntu setup as a WINS server is causing it or not.  I assume you tried the same username/password that worked with XP.  I have smbclient installed but nothing setup for it in /etc.

---

### Post by lance bermudez on 2006-02-10
when i use my windows xp pc to access the share on windows 2000 the share does not ask for a password. the windows 2000 needs a password and username to login and it hass been set to login automackly at startup. does that help

---

### Post by skirkpatrick on 2006-02-10
Not really, that just means that XP remembers the username/password and doesn't bother to ask you for it.  Have you tried disabling the WINS in Ubuntu?

---

### Post by lance bermudez on 2006-02-11
yes i disabled the wins and still could not get to the windows 2000 share

---

### Post by skirkpatrick on 2006-02-11
So exactly what happens on Ubuntu when you supply the username password you used on the XP box?  When you say you can't access it, can you see the server in Places->Network Servers?

---

### Post by lance bermudez on 2006-02-11
no i cant not see the window2000 box in places network servers with or without the wins sever enabled. it does ask for a password to access the windows 2000 box and the passwords and users names are not accespted. i have the linux, windows, samba passwords and usernames all the same. i can see the workgroup and whan i click on the workgroup i see the windows box and the unix box in the places network servers but when i click on the window i get the ask the password things.

---

### Post by skirkpatrick on 2006-02-12
Okay, I'm getting confused here.

1) Can Ubuntu see and access your Win2K box?

2) Can your Win2K box see and access Ubuntu?

---

### Post by slyder on 2006-02-12
Ok, I have gone over and over this forum as well as the unofficial users guide, and am stuck, I have finally gotten samba to the point that I can see my Ubuntu machine from Windows, however, even though I have configured user names and passwords for samba when I try and connect it asks for a username and password, I give it the username and password and it comes back and asks for it again......  I am beating my head off of the wall, this is the only thing that is keeping my windows partition alive since i have to go there anytime someone needs to print from another computer.  PLEASEEE  any suggestions, i am open!!
# Global parameters
[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        username map = /etc/samba/smbusers
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        hosts allow = 192.168.1.

[homes]
        comment = Home Directories
        read only = No
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[MyShared]
        path = /root
        read only = No
        guest ok = Yes
here's my Smb.conf settings, I'm sure at this point I am doing something really stupid, but i don't know what it is!!!!!
HELP:confused:

---

### Post by slyder on 2006-02-12
ok, I have since made a few changes and can now see the shared folder and the add printer option, however, when i try and add a printer it tells me that I don't have permission to do it, and gives me the option to run as a different user, but my XP login has admin rights, so I'm not sure where to go from here.  Any thoughts????

---

### Post by lance bermudez on 2006-02-12
on the linux box under places>network servers i can see the windows box but can not access it becuse my passwords do not work. have add the linux and windows users to samba and they are all three the same user and password. on the windows 2000 box i can see the linux box and access it. for the printer have you tried using the adobe postscript printer driver?

---

### Post by lance bermudez on 2006-02-12
set the printer to guest as in guest = ok and it will not ask for a password for the printer look at my smb.conf on page one for where to put the guest.

---

### Post by slyder on 2006-02-13
ok, got that, now when i try and connect to it,  i get " the server for the printer does not have the correct driver installed.........."  when i search for the driver it doesn't show the correct driver for my printer?  I have my smb.conf set to use client driver.  What else do i need to do?  
     BTW - thank you to those who have answered my posts and to those that have left such detailed posts regarding these issues.  I absolutely LOVE Ubuntu and as soon as this problem is resolved look forward to deleting my windows partition so thank you very very much!!!!!!!!!

---

### Post by slyder on 2006-02-13
here is my smb.conf file - I also need to know how to set just one shared folder, for some reason my home is shared and everything, including my desktop etc...  I just would like one shared file such as "shared Documents"

# Global parameters
[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spas sword:* %n\n .
        username map = /etc/samba/smbusers
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        printcap name = cups
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        hosts allow = 192.168.1.
        printing = cups
        print command =
        lpq command = %p
        lprm command =

[homes]
        comment = Home Directories
        read only = No
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        printer admin = root
        create mask = 0700
        guest ok = Yes
        printable = Yes
        use client driver = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        guest ok = Yes

[MyShared]
        path = /root
        read only = No
        guest ok = Yes

[Print]
        path = /root/smb4k/UBUNTU/print$
        read only = No
        guest ok = Yes

also anything else that you see that needs to be edited please let me know, I am still new to this so any help is greatly appreciated.

---

### Post by lance bermudez on 2006-02-13
for the printer down load the adobe driver installer for windows if you are going from windows to ubuntu. when you have the driver installer down loaded you need to copy the ubuntu driver from ubuntu to windows and have the adobe installer install it on windows. if you are going from ubuntu to window i was told that just setting up the printer in ubuntu using smb share and the network address to make it a network printer. and just to set up your folder share only turn off the home dir and leave the [share] tag in the smb.conf but set the path to only go to that folder like for example path = /home/lance/share if you leave guest = ok you will not have to use a password but if you take it out you will have to use a password

---

### Post by lance bermudez on 2006-02-13
the adobe program i keep talking about is with my smb.conf stuff on the first page. sorry i forgot to put it with last comment.

---

### Post by slyder on 2006-02-13
Thanks alot, I will attempt it when I get home!!!!

---

### Post by slyder on 2006-02-14
Lance - **_YOU ROCK!!! _** :D   Thank you so so so very much!!! Everything is working perfectly!!  I can't wait til my other half see this, so I can format my other HD!!!  I can't thank you enough!!  This is like Christmas for me!!  
     Thanks Again to everyone else who helped me make Ubuntu my Linux Home!!!! \\:D/

---

### Post by skirkpatrick on 2006-02-14
Lance, so your problem isn't smb.conf anymore.  That's good but it sounds like the problem is on your Windows 2000 side.  I don't have 2000 but I just did some playing around with XP and the sharing, I believe, is the same.  Here's what I had to do:

1) I shared a directory on XP.

2) Right-click the folder and go to Properties and select the Security tab.

3) Click Add and enter "Everyone".  After you click Ok, then click Apply so that it gets applied to all the files and subdirectories.  This allows any user to access the share and doesn't care what the password is.  I used smbclient to access it with a password of "bogus" and had no problems.

**OR**

4) Click Add and enter the Windows user that you want to add.  Not the alias of the user but the actual username in Windows.  Make sure you click Apply.

5) Even though in the Security tab I gave my user Full Control, I could not delete a file unless I also went to the Sharing tab, clicked on Permissions and gave the user Full Control there.

6) When I used smbclient, this is the command I used (Guest was the user I created): **smbclient -user=Guest //192.168.0.203/Download**

---

### Post by lance bermudez on 2006-02-14
i have tried all the below uing sudo su - and it show the errors i have got. so far this is the cloest i have come thank you 


root@breezyBadger:~# smbclient -user=Everyone //192.168.3.2/wshare
Password:
Anonymous login successful
Domain=[LBERMUDEZ] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

or

smbclient -user=mother //192.168.3.2/wshare
Password:
Anonymous login successful
Domain=[LBERMUDEZ] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

or

root@breezyBadger:~# smbclient -username=mother //192.168.3.2/wshare Password:
Anonymous login successful
Domain=[LBERMUDEZ] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

---

### Post by lance bermudez on 2006-02-15
From my windows box I can see its share
C:\Documents and Settings\mother>net view 192.168.3.2
Shared resources at 192.168.3.2
Share name   Type         Used as  Comment
-------------------------------------------------------------------------------
wshare       Disk
The command completed successfully.

And still from my windows box I can see my Ubuntu shares
C:\Documents and Settings\mother>net view 192.168.3.3
Shared resources at 192.168.3.3
breezyBadger server (Samba, Ubuntu)
Share name   Type         Used as  Comment
-------------------------------------------------------------------------------
homes        Disk                  Home Directories
lshare       Disk
PSC-750      Print                 PSC-750
windows      Disk
The command completed successfully.

From the windows box I can ping both pc ip addresses and computer names.

From the Ubuntu box using the ip address of the computer name i get
 smbclient -L breezybadger
Password:
Domain=[LBERMUDEZ] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]
        Sharename       Type      Comment
        ---------       ----      -------
        homes           Disk      Home Directories
        lshare          Disk
        windows         Disk
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (breezyBadger server (Samba, Ubuntu))
        ADMIN$          IPC       IPC Service (breezyBadger server (Samba, Ubuntu))
        PSC-750         Printer   PSC-750
Domain=[LBERMUDEZ] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]
        Server               Comment
        ---------            -------
        BREEZYBADGER         breezyBadger server (Samba, Ubuntu)
        MOM

        Workgroup            Master
        ---------            -------
        LBERMUDEZ            MOM

and form the Ubuntu box for the window using the ip address and computer name i getting
root@breezyBadger:~# smbclient -L //192.168.3.2
Password:
Anonymous login successful
Domain=[LBERMUDEZ] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.3.2 failed (Called name not present)
session request to 192 failed (Called name not present)
Anonymous login successful
Domain=[LBERMUDEZ] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
        Server               Comment
        ---------            -------
        BREEZYBADGER         breezyBadger server (Samba, Ubuntu)
        GRASSHOPPER
        MOM
        Workgroup            Master
        ---------            -------
        LBERMUDEZ            MOM

this is because i just changed from my window xp to my Ubuntu other wise grasshopper is the computer name for my win xp. if i restart then from my Ubuntu using the Ubuntu ip address or computer name i get

root@breezyBadger:~# smbclient -L \\192.168.3.3
Password:
Domain=[LBERMUDEZ] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]
        Sharename       Type      Comment
        ---------       ----      -------
        homes           Disk      Home Directories
        lshare          Disk
        windows         Disk
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (breezyBadger server (Samba, Ubunt u))
        ADMIN$          IPC       IPC Service (breezyBadger server (Samba, Ubunt u))
        PSC-750         Printer   PSC-750
Domain=[LBERMUDEZ] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]
        Server               Comment
        ---------            -------
        BREEZYBADGER         breezyBadger server (Samba, Ubuntu)
        MOM
        Workgroup            Master
        ---------            -------
        LBERMUDEZ            BREEZYBADGER

and for the windows from the Ubuntu i get 

root@breezyBadger:~# smbclient -L \\mom
Password:
Anonymous login successful
Domain=[LBERMUDEZ] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[LBERMUDEZ] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
        Server               Comment
        ---------            -------
        Workgroup            Master
        ---------            -------

and working from the window after the restart i still get what i had from the top. the Ubuntu and Windows xp pc is a dual boot. i think the problem is on the Ubuntu because i can see both from the windows 2000 pc. but im not shure what the problem is or where it is.

---

### Post by skirkpatrick on 2006-02-15
No, I think it's on the Windows side.  If your Windows box can access your Ubuntu shares, then smb.conf is good and working.

When I tried to access a Windws share from Ubuntu, I also got the error "NT_STATUS_ACCESS_DENIED" when smbclient tried to access the Windows box.  Doing steps 4, 5, 6 of the previous post is what it took to fix the problem.  And those steps are on the Windows box.

---

### Post by lance bermudez on 2006-02-16
i have done steps 4-6 and i still get the "NT_STATUS_ACCESS_DENIED" i have edited the hosts files on both ubuntu and linux and only the lmhost file on windows becuse it is the only pc to have the lmhost file and now i can ping both computer from ubuntu and linux using the computer name.

---

### Post by skirkpatrick on 2006-02-16
Well, I can tell you that smb.conf is what Ubuntu uses as a Samba server.  So if your Win2000 box can access your Ubuntu shares, then it is fine.  Since Ubuntu is having problems accessing the Win2000 shares, then that is something else entirely.  At this point I don't know what.

---

### Post by lance bermudez on 2006-02-16
here is everything working fin thaks to all that helped me

First let that I’m printing from windows 2000 to Ubuntu breezy badger where my HP PSC 750 printer is attached. And the files can be shared from the Ubuntu breezy badger to the windows but not from the windows to the breezy badger. Make sure samba, samba-common, smbclient, smbfs, libsmbclient, and libsmbclient-dev are installed.  Also make sure the printer is installed by using system administraton printing then click add printer. Now to get started the commands that need to be typed in are surrounded by “” and have to be typed in terminal using “sudo su –“ to use super user the password will be you login password. Terminal is open by clicking applications then accessories then terminal. To get this to work you have to have all to the three user mathch user names and password they are windows user, Linux user, and samba user. With the “smbpasswd –a username” hit enter and put in the password also you will have to add the root user to samba “smbpasswd –a root” this is for administration use. Then edit the smb.conf file of samba with “vi /etc/samba/smb.conf” to match what is below. To add the changes press the insert key on the key board and make it look like what is below

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
   workgroup = LBERMUDEZ

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

#resole host names to ip addresses
name resolve order = lmhosts host wins bcast
bind interfaces only = yes
hosts deny = all
hosts allow =192.168.3.0/24 127.
interfaces = eth0 lo

#authentication
security = user

# encrpyt password in the smb.conf
encrypt passwords = yes
smb passwd file  = /etc/samba/smbpasswd
local master = no
dns proxy = no

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   load printers = yes
   printing = cups
   printcap name = cups
   show add printer wizard = No

[homes]
   comment = Home Directories
   path = /home/lance
   browseable = yes
   writable = yes
   create mask = 0700
   directory mask = 0700

[lshare]
  path = /home/lance/lshare
  available = yes
  browseable = yes
  public = yes
  writable = yes
  guest ok = yes

[windows]
  path = /media/windows
  available = yes
  browseable = yes
  writable = yes
  guest ok = yes

[printers]
   comment = All Printers
   path = /tmp
   printable = Yes
   guest ok = Yes
  public = yes 
  use client driver = No
   browseable = Yes
  printer admin = root

[print$]
  comment = Printer Drivers
  path = /var/lib/samba/printer
  browseable = yes
  read only = yes
  guest ok = yes
  write list = root

when you have typed what is above save it by pressing the esc key to exit the insert mode then press shift q then type exit. Restart samba by typing “/etc/init.d/samba restart” then type “cupsaddsmb –U root –v –a “ hit enter then enter the password that you used for the samba root account. This will add the driver to samba for the printer.  If you need help understanding this part read this web page at [http://www.linuxdevcenter.com/pub/a/linux/2005/01/13/lnxckbk_samba.html](http://www.linuxdevcenter.com/pub/a/linux/2005/01/13/lnxckbk_samba.html)
after the drivers have been copied reedit the smb.conf file and change the “security = user” part to “security = share” under #authentication comment and save and restart samba. To get printing to work download the adobe program and adobe ppd toward the botton of page from the url to the windows 2000 box. on the Ubuntu box type “/etc/cups/ppd”  hit enter then type “ls” find your printer and whrite down its name they type “cp printer name /home/shared folder name” then type “cd /usr/share/cups/model/hplip” hit enter type “ls” find your printer then type “cp printer /home/shared folder name” on the windows 2000 box connect to the Ubuntu share and copy the printer files to windows 2000. unzip the adobe ppd program and where ever you copy it to past the printer files you copied from Ubuntu into it the run the adobe program and install the printer.   The [window] is a fat32 part of my hard drive i use to share files with the dual boot and the network and the [lshare] is for network sharing they both allow access without needing user name and password but [home] needs user name and access. the #resole host names to ip addresses line is for security so that only my network pc can use my linux samba server and the # encrpyt password in the smb.conf line is for win 2000 and above because windows encrpyt passwords with these version but is not needed for version below. now the winows will talk to the linux but the linux will not talk to the windows tell you fix the window and linux some more. this part will not work with dhcp and may not be a problem but needs to be done on static network for computer names to be pinged in linux. on the window edit the lmhosts and hosts. for the windows hosts  should be ip space computer name
127.0.0.1       localhost
192.168.3.2	mom
192.168.3.3	breezyBadger
and for the lmhosts on the winows  should be ip address netbios name
192.168.3.3 breezybadger #PRE
192.168.3.2 mom #PRE
and for the linux hosts ip computer name
127.0.0.1 localhost.localdomain localhost breezyBadger
192.168.3.3 breezyBadger
192.168.3.2 MOM
to connect to the windows computer form linux the user must have the sharing permissions set and the windows user added to both the sharing permission and security tab. does not need a password unless your user has one for security use 
smbclient //ip address/folder share name -U username%password
example 
smbclient //192.168.3.2/wshare -U lance%bermudez
to browse the windows computer for shares use
smbclient -L //192.168.3.2 -N -U lance%bermudez

rembember to be in the command line directory you want to send files to the windows or save the files because it acts like an ftp. for a gui mount it with 
 mount //192.168.3.2/wshare /media/wshare -t smbfs -o username=lance,password=bermudez,dmask=777,fmask=777

also edit /etc/gnome-vfs-2.0/modules/smb-module.conf change the line
smb: [daemon] libsmb
to read
smb: libsmb.so
but i did
smb: libsmb
and it seems to work fine

---

### Post by tedius on 2006-02-18
I have followed this thread and I have shared two folders on my linux box.  But I can get the printer to work on my WinXP laptop.

my smb.con looks like this. (With the comments removed)

> 
#======================= Global Settings =======================

[global]

workgroup = BEEHIVE
server string = %h server (Samba, Ubuntu)
wins support = yes
security = user

# CUPS printing. See also the cupsaddsmb( manpage in the
# cupsys-client package.
load printers = yes
printing = cups
printcap name = cups

show add printer wizard = No

[Music]
comment = Home Directories
path = /mnt/music
browseable = yes
writable = yes
create mask = 0700
directory mask = 0700

[Share]
path = /home/torben/download
comment = Shared Files
browseable = yes
writable = yes
create mask = 0700
directory mask = 0700

[printers]
comment = All Printers
browseable = yes
use client driver = no
path = /tmp
printable = yes
guest ok = yes
public = yes
writable = no
create mode = 0700
printer admin = root

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no
write list = root


And an `ls -r /var/lib/samba/printers` gives me the following
> 
.:
W32X86  WIN40

./W32X86:
2             ADOBEKOR.NTF  ADOBEPSU.DLL  ADOBEZHT.NTF   MDIGRAPH.DLL
3             ADOBEPS5.DLL  ADOBEPSU.HLP  ADOBOEJPN.NTF  MDIUI.DLL
ADBOEPS5.DLL  ADOBEPS5.NTF  ADOBEZHS.NTF  DEFPTR2.PPD

./W32X86/2:
ADOBEPS5.DLL  ADOBEPS5.NTF  ADOBEPSU.DLL  ADOBEPSU.HLP  DEFPRTR2.PPD

./W32X86/3:
DEFPRTR2.BPD  HP5000_7.BPD  PSCRIPT.HLP   defprtr2.ppd
HP4050_7.BPD  HP5000_7.PPD  PSCRIPT.NTF   mdigraph.dll
HP4050_7.PPD  PS5UI.DLL     PSCRIPT5.DLL  mdiui.dll

./WIN40:
0            ADOBEPS4.DRV  DEFPRTR2.PPD  PSMON.DLL
ADFONTS.MFM  ADOBEPS4.HLP  ICONLIB.DLL

./WIN40/0:
ADFONTS.MFM  ADOBEPS4.DRV  ADOBEPS4.HLP  DEFPRTR2.PPD  ICONLIB.DLL  PSMON.DLL


The printer I have is a Styles-C62

When I try to add the printer on the WinXP laptop I get a box up saying that the server doesn't have the drivers and do I want to look for them.  I though that when I had added the adobe .dll to /var/lib/samba/printers it would download them.

If any one can give me any help I would be very pleased.

---

### Post by skirkpatrick on 2006-02-18
I have never successfully gotten the drivers to work from a Linux print server, I always install the drivers locally on each machine.

---

