---
title: "Help with setting up a home network"
date: 2005-10-20
forum: Desktop Environments
---

### Post by mrmcctt on 2005-10-20
I have been trying most of the afternoon to set up a home network between my Ubuntu laptop and my three WinXP systems.

I have looked at several "how-to's" and the Ubuntu guide.  I have followed all the the stuff I read (I think) and am still unable to either see any of my WinXP systems from the Ubuntu laptop or see the Ubuntu laptop from the WinXP systems.  All of the WinXP systems can see each other.

I have installed samba and smbfs per the user guide.  My smb.conf looks like this.
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
   workgroup = HOMENET
netbios name = ubuntu

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



[Home]
path = /home/rlodge
available = yes
browseable = yes
public = yes
writable = yes

```

When I do a sudo testparm, I get this output:
```
rlodge@ubuntu:~$ sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Home]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = HOMENET
        server string = %h server (Samba, Ubuntu)
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

[homes]
        comment = Home Directories
        read only = No
        create mask = 0700
        directory mask = 0700

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Home]
        path = /home/rlodge
        read only = No
        guest ok = Yes

```

I have done the sudo /etc/init.d/samba restart after editing the config file.

I have shared my home folder by using the System>Administration>Shared Folders menu.

I have looked at some sample smb.conf files from a google search and one that was recommended on this forum.  

What am I missing?  Can anyone see a problem with the smb.conf file?  I have "Firestarter" installed but as far as I can tell it isn't blocking the connections.

I am able to ping the computers on my network but can't see them.

Any help is appreciated.

---

### Post by migueljacq on 2005-10-20
Hmm all looks pretty good. I had a similar problem which turned out to be firestarter: I think under 'policies' tab, I needed to allow Samba smb's. But if you've covered this, then I am not sure. Since you can ping them, I won't suggest it's the eth0 settings. Strange

---

### Post by mrmcctt on 2005-10-20
You may be on to something.  I just looked at the events log and found blocked connections that were Samba (SMB) with IP addresses from my network.  

I right clicked on one and allowed access and now I get one of my computers to show in the Places>Network Server link.

Well, it disappeared now but it's a start.  At least I've got a direction to look in.

Thank you very much.

---

### Post by mrmcctt on 2005-10-20
That was the problem (Firestarter).  For some reason I could ping the machines but not connect to them.

I added policies to allow services and now I can see all systems from all systems and can access files from my WinXP systems.  Now I just need to restrict the policies a little (they're set to allow "everyone" right now) and I'll be happy.

If someone could correctme if I'm wrong here....I *shouldn't* be able to open the shared folder on my Ubuntu laptop from the WinXP systems because they won't recognize the file system.  I tried to connect to my shared folders in Ubuntu from a Windows machine and was told that I may not have permission to view the folder.  I was given no box to allow me to input a username and password.

---

### Post by skirkpatrick on 2005-10-20
Samba hides the filesystem.  Since I'm behind a NAT/router, I set my security to share instead of user.

---

### Post by Dr. Nick on 2005-10-20
The type of filesystem shouldnt matter I dont think, samba interrupts the files. thats why you are able to write to your XP box from Ubuntu even though your XP is ntfs which linux doenst usually "safely" write to.

You said you can access files from ubuntu on XP? If so that should prove that file systems dont matter as XP doesnt recgonize ext2/3 or other linux FS's 

When you shared your folder did you hit the "allow browsing folder" checkbox? It should ask for a user/pass but may be sorta flaky and unpredictable. Hopefully someone who has done it more recently can help you as is been a few months since i've gone linux <-> windows. 

Thats what happens when you put Ubuntu on your laptop aswell as Desktop :p ;)


Its possible to ping and not be abe to connect. Since samba acts on a specific port (139 I believe) Firestarter has to be setup to allow imbound/outbound connections on that port. When you ping it doesnt look for a specfic port as much, all it cares about is that something replies. Sorta hard to explain for me.

---

### Post by mrmcctt on 2005-10-20
> When you shared your folder did you hit the "allow browsing folder" checkbox? It should ask for a user/pass but may be sorta flaky and unpredictable.

Yes I did.  I will have to revisit the procedures for "security=share" vs. "security=user" and set that up.  I'm also behind a router/NAT and shouldn't have too much to worry about.  

In one of the how-to's I read (maybe even the Ubuntu guide) I was instructed to set up a /etc/samba/smbusers folder.  I did this and now I'll just have to edit smb.conf for security=share and remove my smbuser account (if that makes any sense).  I have not even been able to get to my Ubuntu shared folder from Ubuntu.  It shows a login screen (userid & password) but everytime I input the password it won't allow me access.


> Thats what happens when you put Ubuntu on your laptop aswell as Desktop  

I know.  I would love to have it on all of them.  Especially since my wife stole my other laptop ("The company gave you one so I'm taking yours!!!" to which I replied "Yes, Ma'am." and drive on.)

My youngest daughter won't give up her Launch videos on Yahoo so that's that.  Firefox used to have an extension thatallowed you to watch these videos in Firefox but I can't find it now.  My daughter told me that if I can get Launch to work in Linux she'll try it.

My oldest loves Windows too much to even try.  To each their own I guess.

---

### Post by Dr. Nick on 2005-10-20
I had it working without the smbuser file I think, In my smb.conf I have security=user but no username map. Have you tried playing with the "places - Connect to server" menu and trying to connect to your Xp from their. 

I just realized I misread your above post above about filesystemsso my reply sounds stupid :-)
I hope you can get it working right. Unfortunately I cant test my configuration anymore to see how exactly to get it to connect.

Also have you seen this link concerning launch videos
[http://ubuntuforums.org/showthread.php?t=43058&highlight=launch+yahoo](http://ubuntuforums.org/showthread.php?t=43058&highlight=launch+yahoo)
havent done so myself but it may work and may lead to a convert :)

---

### Post by f1dave on 2005-11-01
Somehow I got mine working remarkably easily :S

This link here might be helpful...
[http://www.samba.netfirms.com/index.htm](http://www.samba.netfirms.com/index.htm)

---

### Post by manicka on 2005-11-01
[http://ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure](http://ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure)

---

### Post by mrmcctt on 2005-11-01
Thanks to all your help I have everything working.  It does require a lot of passwords to access the network such as one to access the computer, one to access the share and one to access a subfolder of the share but it's working.

> 
Somehow I got mine working remarkably easily :S

This link here might be helpful...
[http://www.samba.netfirms.com/index.htm](http://www.samba.netfirms.com/index.htm)


I'll check that link out as soon as I can get access to the internet through Ubuntu in this hotel.  I'm haveing problems with this as seen in [this thread.]("http://www.ubuntuforums.org/showthread.php?t=84569")

> [http://ubuntuforums.org/showthread.p...t=samba+secure](http://ubuntuforums.org/showthread.p...t=samba+secure)

Thanks but that's the post that got me started.  It looked pretty straight forward and I still think I was doing something wrong on my end.  After following that post and all the suggestions above, I have this monster beat. 

Thank you to everyone who took a little (or a lot) of time helping.

---

