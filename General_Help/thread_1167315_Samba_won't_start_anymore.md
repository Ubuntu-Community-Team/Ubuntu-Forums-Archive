---
title: "Samba won't start anymore"
date: 2009-05-22
forum: General Help
---

### Post by erik087 on 2009-05-22
I've had a FAT32 partition mounted and shared for a long time without any problems, but now samba isn't running, and I can't get it started.  Everything worked fine until my wife rebooted when I wasn't home...she's not sure if she did something else before/after rebooting.

Here's what I have:

[COLOR="Blue"]$ sudo /etc/init.d/samba start
 * Starting Samba daemons                                                                    [ OK ][/COLOR]

obviously, it's not starting correctly...
[COLOR="Blue"]
$ sudo /etc/init.d/samba status
 * nmbd is not running
 * smbd is not running[/COLOR]


tail of /var/log/samba/log.smbd:

[COLOR="Blue"]$ tail /var/log/samba/log.smbd
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/05/22 18:07:50,  0] lib/debug.c:reopen_logs(663)
  Unable to open new log file file:///var/log/samba/log.%25m: No such file or directory
[2009/05/22 18:07:50,  0] lib/debug.c:reopen_logs(663)
  Unable to open new log file file:///var/log/samba/log.%25m: No such file or directory
[2009/05/22 18:07:50,  0] lib/debug.c:reopen_logs(663)
  Unable to open new log file file:///var/log/samba/log.%25m: No such file or directory
[2009/05/22 18:07:50,  0] lib/pidfile.c:pidfile_create(127)
  ERROR: can't open file:///var/run/samba/smbd.pid: Error was No such file or directory
[/COLOR]

Here is some of my smb.conf:

[COLOR="Blue"]
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = MSHOME                                                          

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
log file = file:///var/log/samba/log.%25m                     

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
#   security = user                                                        

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
encrypt passwords = yes                                          

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.                             
passdb backend = tdbsam                                             

obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the  
# passdb is changed.                                                     
unix password sync = yes                                                 

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).          
passwd program = file:///usr/bin/passwd%20%25u                                      
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in   
# 'passwd program'. The default is 'no'.                             
pam password change = yes                                            

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections                                                
map to guest = Bad User                                                   

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
security = share                                                
guest account = alex                                            
restrict anonymous = no                                         
domain master = no                                              
logon home = %5C%5C%25N%5C%25U                                  
smb passwd file = file:///etc/samba/smbpasswd                   
pid directory = file:///var/run/samba                           
logon path = %5C%5C%25N%5C%25U%5Cprofile                        
private dir = file:///etc/samba
[/COLOR]

What am I missing?  Any ideas of what I should be looking at next?

---

### Post by Iowan on 2009-05-22
Have you run **testparm** to verify .config file?
This stuff looks a little... unusual:> logon home = %5C%5C%25N%5C%25U
smb passwd file = file:///etc/samba/smbpasswd
pid directory = file:///var/run/samba
logon path = %5C%5C%25N%5C%25U%5Cprofile
private dir = file:///etc/samba

---

### Post by gahia on 2009-05-31
Hello, 

I had the same problem in Jaunty Jackalope.

You only need

* Remove the "file://" from paths (file:///etc/samba --> /etc/samba)
* Replace these "unusual" lines by:

logon home = \\%N\%U
logon path = \\%N\%U\profile

Then samba init again...

---

### Post by KaiO on 2009-06-17
Thank you gahia ! :KS:D
That saved my day.
I could not get my KUbuntu computer samba'ed. And had a hard time understanding why.

Following you advice:
> 
* Remove the "file://" from paths (file:///etc/samba --> /etc/samba)
* Replace these "unusual" lines by:
  logon home = \\%N\%U
  logon path = \\%N\%U\profile

fixed my troubles.
But I fail to understand why my /smb.conf file contained these errors to begin with.

---

### Post by MadOrL on 2009-07-04
Tks... This answer fix my problem too.. I will share this with my friends...

---

### Post by sweetlandj on 2009-08-24
> **KaiO said:**
> Thank you gahia ! :KS:D
That saved my day.
I could not get my KUbuntu computer samba'ed. And had a hard time understanding why.

Following you advice:

fixed my troubles.
But I fail to understand why my /smb.conf file contained these errors to begin with.


Fixed the problem for me as well.

Evidently mucking about in the KDE file sharing dialogs will cause these errors.  I manually fixed them, then I tried to share a folder via KDE, hoping the KDE stuff would start working.  Immediately after changing some settings in the KDE dialogs, Samba would not restart, and I noticed that these artifacts had been re-introduced into the smb.conf file.

So, whatever you do, don't use the KDE samba configuration tools.  (I'm using Kubuntu 9.04, btw)

---

