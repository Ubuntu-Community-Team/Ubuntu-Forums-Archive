---
title: "Sharing folder with samba"
date: 2005-12-27
forum: Desktop Environments
---

### Post by Dearhell on 2005-12-27
What I want is to have access from a Windows machine of my network to the Ubuntu Machine, I made this steps:

I edited the file /etc/samba/smb.conf and I uncommented this line:

```
guest account = nobody
```

And I added this other lines:

```
[emule]
   comment = Emule
   path = /home/myaccount/.aMule/Incoming
   read only = no
   guest ok = yes

```

Then I executed these commands through the console: 

```
testparm
/etc/init.d/samba restart
```

But when I'm on the Windows Machine and try to get access to the Ubuntu Machine, it request a name and a password, and I want that can get into the Ubuntu machine directly, without that

Anticipate thanks

---

### Post by pharcyde on 2005-12-27
Can you post your entire smb.conf file?

---

### Post by Dearhell on 2005-12-27
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
   workgroup = CASA

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
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

   guest account = nobody
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

[emule]
   comment = Emule
   path = /home/myaccount/.aMule/Incoming
   read only = no
   guest ok = yes

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

### Post by Dearhell on 2005-12-27
I think it's all right, so I can't understand why continues to request user and password

---

### Post by Zimmer on 2005-12-27
Hello.
Try adding a Samba User..
visit [http://ubuntuguide.org/#installsamba](http://ubuntuguide.org/#installsamba)
and start reading from
Q: How to add/edit/delete network users?
This will tell you to do the following...
#

sudo smbpasswd -a system_username
sudo gedit /etc/samba/smbusers

# Insert the following line into the new file

system_username = "network username"

I will translate this bit for you (cos it confused me at the start)
If your Ubuntu user name is called 'scribe'  ( substitute scribe with whatever your user name is...)
Then in the Terminal type:
sudo smbpassword -a scribe (and it will prompt you for a password, which does not have to be the same as your Ubuntu user password, and it will ask for confirmation)
then
sudo gedit /etc/samba/smbusers
...and type the following into the new file..
scribe = "network username"
save the file
You now have a Samba user called scribe    ..
Before you start messing with the smb.conf file re boot and have your Windows machines conected and running and see if you can access their shared folders . When(If) they prompt you for the user and password it is the user and password you have just set up for Samba.....
For Windows to see your Ubuntu folders you will need to go back and follow the instructions for setting up shares in the link above ...and if set up correctly Windows may ask for that very same Samba user and password to connect to the shared area..

---

### Post by Dearhell on 2005-12-27
I think I understand what you have explained, but what I want is to access from a Windows machine of my network to my Ubuntu machine shared folder without writing user and password

For that I have used the option "guest ok = yes"

```
[emule]
   comment = Emule
   path = /home/myaccount/.aMule/Incoming
   read only = no
   guest ok = yes
```

But I can't understand why doesn't work (with guest ok it doesn't need to add a user, don't?)

---

### Post by Zimmer on 2005-12-28
OK, I tried this and it works for me...
Add a proper user to your Ubuntu machine with the same name as your Windows user.
Add that user as a Samba user (as per previous post) with the same password as the Windows user password..
When you access the share from Windows Network Neighborhood it will no longer require user and password....

There is (yet) another way .... if you have a look at the methods here..
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
which may suit your particular requirements ...
Regards

---

### Post by Dearhell on 2005-12-28
Ok, i'm gonna try it then

---

### Post by Dearhell on 2005-12-28
Thx, now it works fine :D

---

### Post by christooss on 2005-12-28
Hello when I sudo smbpassword -a I get

sudo: smbpassword: command not found

---

### Post by christooss on 2005-12-28
Ok I have sudo smbpasswd -s working :)

---

### Post by Dearhell on 2005-12-28
I have another problem, I can access now from Windows to the folder I have shared with samba, but when I copy in Ubuntu any file to this shared folder, then from Windows I cannot get it because it has not enough permissions

There is anyway to copy files to my shared folder that can be get from Windows without changing permissions manually each time?

---

### Post by christooss on 2005-12-28
```
matic@ubuntu:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Unknown parameter encountered: "matic"
Ignoring unknown parameter "matic"
Processing section "[Glasba]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = MELOM
        server string = Melom
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Glasba]
        path = /home/matic/mp3/
        read only = No
        guest ok = Yes
        browseable = No

```

I have problem to. This is my testparm output. I can see printers in My network connections on Windows machine but I cannot see /home/matic/mp3 directory.

What is wrong

---

### Post by DJiNN on 2005-12-28
I've tried the links put on here, to try & get my two Ubuntu machines sharing files, i've installed both Samba & smbfs on BOTH machines, but i can't get them to see each other at all. 

Are there any other ways to get round this problem? I just need simple file sharing, no more or less, and am using a Firewall/router (Netgear). 

I would use Hamachi instead, but i can't even get that installed & working. (Yeah, there are times that i really miss XP... :) But i'm still staying with Ubuntu.... I'm sure i'll get it to work eventually) 

DJiNN

---

### Post by sciurus on 2005-12-28
[QUOTE=Dearhell]I think it's all right, so I can't understand why continues to request user and password[/QUOTE]

I think you needed to set security = share.

---

### Post by sciurus on 2005-12-28
[QUOTE=christooss]
Unknown parameter encountered: "matic"
Ignoring unknown parameter "matic"
[/QUOTE]

This suggests a syntax error. Also, don't you want browseable = yes?

---

### Post by Dearhell on 2005-12-28
[QUOTE=sciurus]I think you needed to set security = share.[/QUOTE]

Well, that was solved, the new problem I have it's also detailed in this same thread, thx anyway

---

### Post by Zimmer on 2005-12-28
[QUOTE=Dearhell]Well, that was solved, the new problem I have it's also detailed in this same thread, thx anyway

I have another problem, I can access now from Windows to the folder I have shared with samba, but when I copy in Ubuntu any file to this shared folder, then from Windows I cannot get it because it has not enough permissions

There is anyway to copy files to my shared folder that can be get from Windows without changing permissions manually each time?
[/QUOTE]
Hi Dearhell..
Let us have a look at the  ==== Share Definitions ======  sevtion of your smb.conf file to diagnose the problem...

Regards

---

### Post by voyageur_01 on 2005-12-28
Add this line to global section in /etc/samba/smb.conf

"map to guest = Bad User"

that will allow you access with guest account

set up 
"security user"

add to the share section, here is an example

[public]
comment = Public Folder
path = /home/public
guest ok = yes
public = yes
writable = yes
browsable = yes

You must have also permitions in file system to write to this folder by others

chmod 777 /home/public

and now you will hava access to write by guest to this public directory:)
Have a fun:D

---

### Post by Dearhell on 2005-12-28
I can write my Ubuntu shared directory from a windows machine of my network, but when from Ubuntu I put some file on my shared directory, it has no enough permissions, and then I can't copy that file from the Windows machine

And I don't want to give permissions to each file I put in my Ubuntu's shared folder

The share definitions of smb.conf: 

```
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

[emule]
   comment = Emule
   path = /home/casa/.aMule/Incoming
   public = yes
   writable = yes
   create mode = 0775
   directory mode = 0775
   read only = no
   public = yes
   browseable = yes
```

---

### Post by rplantz on 2005-12-28
Windows may be a little more forgiving, but Mac OS X Tiger does not like the version of samba (3.0.14) that comes with Breezy. I had to install samba 3.0.20 from the Dapper repositories. I describe what I did at [url]
http://www.ubuntuforums.org/showthread.php?p=585568#post585568[/url]. This allows me to browse for my Ubuntu machine from my Mac. With 3.0.14 I had to explicitly specify the machine in order to connect to it.

I took special care about mixing Dapper packages with Breezy. At one point I got a little carried away (on another issue) and broke things. I ended up reinstalling Breezy. Do be careful with this sort of thing.

---

### Post by Zimmer on 2005-12-29
[QUOTE=Dearhell]I can write my Ubuntu shared directory from a windows machine of my network, but when from Ubuntu I put some file on my shared directory, it has no enough permissions, and then I can't copy that file from the Windows machine

And I don't want to give permissions to each file I put in my Ubuntu's shared folder

The share definitions of smb.conf: 

[emule]
   comment = Emule
   path = /home/casa/.aMule/Incoming
   public = yes
   writable = yes
   create mode = 0775
   directory mode = 0775
   read only = no
   public = yes
   browseable = yes[/CODE][/QUOTE]

Check in Nautilus that the actual permissions of the folder .aMule  and Incoming are set to 755...and that there is NOT a tick in the box named 'sticky'  .
Linux directory access permissions say that if a user has write permissions on a directory, they can rename or remove files there,even if the files don't belong to them.
When the owner of the directory sets the sticky bit, renames/removals are only allowed by the files owner, the directories owner and the root user.

My Windows machine will not access folders with 700..

Regards

---

### Post by chaser001 on 2006-01-25
I'm having a similar problem however I can access my personal folder and desktop folder from my windows box however I cannot access my main shared folder that I set up in samba  any thoughts?

---

### Post by christooss on 2006-02-11
Hello Im having problems with sharing folders without password.

[Razno]
path = /razno
guest ok = yes
public = yes
writable = yes
browsable = yes   
force user = nobody
force group = nogroup

This is in my smb.conf and  security is set to share.

security = share

Now I can see and browse this dir but when I ty to copy or watch movie there is an error File is curently in use. But files are not in use :)

What can I do

---

### Post by mvyvoda on 2006-02-12
oh crap.... i am also trying to figure out write permission on my smb share (as i'm having difficulty... but that can wait now): 

[QUOTE=Zimmer]There is (yet) another way .... if you have a look at the methods here..
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
which may suit your particular requirements ...
Regards[/QUOTE]

i went to this site above, and started to follow the directions. somewhere, something went terribly wrong. i created the /root/.smbcredentials file, edited fstab and things started to die. i was going to restart samba, then everything started to crash. 

i couldn't open a terminal or nautilus (via panel), so i rebooted. now, i can't login, it says i have been logged out within 10 seconds of logging in (which obviously isn't the case). i looked at the error message on login, and it says i don't have permission for my home directory (i.e ~/) to start gnome. 

i logged in as root to a terminal and restored the old fstab and deleted the .smbcrendendials file. still nothing. 

i'm very new to linux and am hoping someone can please help me. 

thanks,
-m

---

### Post by Zimmer on 2006-02-12
did you accidentaly chmod your home directory, or the root , even ?

That might explain it . the permissions on the /home  and /home/yourusername should be 755

Read about permissions here..
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

---

### Post by mvyvoda on 2006-02-12
ah yes... rookie mistake. the only saving grace is that when i crashed last night, i thoguht to myself: "self, i bet you changed the permissions on my home directory."

thanks zimmer, you're the man now dog!

-m

---

### Post by Paloseco on 2006-06-13
Here are my settings:

> 

[global]
workgroup = campus
server string = Samba Server
log file = /var/log/samba3/samba3.log
max log size = 100

# hosts allow = 192.168.1. 192.168.2. 127. 192.168.0.
# Allow users to map to guest:
map to guest = bad user

encrypt passwords = true
smb passwd file = /etc/samba/private/smbpasswd
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
dns proxy = no

#============================ Share Definitions ==============================

[Music]
path = /media/hda9/mp3
guest ok = yes
read only = no
case sensitive = no
msdfs proxy = no


---

