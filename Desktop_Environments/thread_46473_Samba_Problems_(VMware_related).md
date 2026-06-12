---
title: "Samba Problems (VMware related?)"
date: 2005-07-04
forum: Desktop Environments
---

### Post by otherdave on 2005-07-04
Ok, I've read almost every post here about Samba, I've read Samba.org. I've played around but I've got some basic samba problems that I can't seem to nail.

My machine is running Ubuntu (Hoary) and I've got VMWare installed with Windows XP. I was following the scenarios at Samba.org for the [No Frills](http://us4.samba.org/samba/docs/man/Samba-Guide/simple.html) setup.

I'll post my smb.conf below but here's the quick summary:

1) No matter what I do, my Windows XP virtual machine has NEVER been able to see my Ubuntu Samba shares in network neighborhood.

2) going to \\hocus-pocus (my Samba netbios name) never works

3) going to \\192.168.1.123 (the samba machine's ip) works, but always opens up a blank window.

4) going to \\192.168.1.123\some_share_name sometimes works, but when it prompts me for a username and password, it never works. I've added a user with smbpasswd -a user_name, but to no avail.

5) my Virtual machine is set to the same workgroup as my smb.conf

Here's my smb.conf. I tried to make it as minimal as possible. I know this board is FULL of Samba questions (Like I said, I read most of them :) ) but if anyone notices anything glaring that I might have missed, or knows about quirks with VMWare that could cause it, I'd love to hear them.

Thanks!

[global]

workgroup = MYGROUP
netbios name = hocus-pocus 

 server string = %h is really cool

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

socket options = TCP_NODELAY

wins support = yes

[homes]
   comment = Home Directories
   browseable = yes
   writable = yes
   create mask = 0700
   directory mask = 0700

[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700
   use client driver = yes
   guest only = yes

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes

[DaveShared]
path = /home/dave/Desktop/Shared
comment = Daves Stuff!
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes

---

### Post by t2kburl on 2005-07-05
I have read that VMWare Workstation 5.0 no longer supports Samba ( Linux-host -> Win guest )

I would very much like to have this enabled also since e-mailing files to myself is unbearably slow.

---

### Post by otherdave on 2005-07-05
[QUOTE=t2kburl]I have read that VMWare Workstation 5.0 no longer supports Samba ( Linux-host -> Win guest )

I would very much like to have this enabled also since e-mailing files to myself is unbearably slow.[/QUOTE]

Are you kidding? This is the dumbest thing ever!

I've had it (somewhat) working before where user dave could log in from Windows to Linux (Samba) (via vmware) but it was always read only and only my 'dave' user's home directory. Ugh...

---

### Post by otherdave on 2005-07-05
I just found [this information about VMWare and Samba](http://www.vmware.com/support/ws5/doc/network_samba_ws.html.html). Unfortunately I'm at work right now but I'll try it out tonight and see if it works and if it helps anyone.

---

### Post by sundancer on 2005-07-05
Perhaps you should set
```

Map To Guest = Bad User

```
to test the shares. If it works, the problem is user related.

Another problem could be the node type of the windows machine.
It must be set to "hybrid". You can see the current setting by executing
```

ipconfig /all

```
on the windows machine.

---

### Post by otherdave on 2005-07-06
Adding:

interfaces = eth1 vmnet1

Fixed the problem. Hopefully this helps someone else :)

I still can't get the VMWare machine to get to it via \\hocus-pocus but by using \\192.168.1.123 it works fine.

---

### Post by t2kburl on 2005-07-06
where did you add the interfaces line?

I tried it at the end of my smb.conf   no joy   ](*,)

---

### Post by t2kburl on 2005-07-06
I found where to pu it now ... under global ... still no joy


in my vmware system I can map a network folder only as //.host/Shared Folders but I can't do anything with it ... access denied
and it doesn't show anything in it so it is not the folder I am intending to share via samba


I'm lost  

here is the my smb.conf if anyone can tell me whats wrong with it I'll be happy

[global]
socket address = 192.168.183.1
interfaces = eth1 vmnet1
bind interfaces only = yes
netbios name = localhost.localdomain
server string = VMware host-only

security = user
encrypt passwords = yes

# Note: Printers not loaded in this example. Resource definitions commented
# below.
; load printers = yes

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

# VMware extension to use a different shared memory access key on each
# Samba server running on this host
sysv shm key = /dev/vmnet1

; log file = /etc/vmware/vmnet1/smb/var/log.smb
; log level = 1
; max log size in KB
; max log size = 50

lock directory = /etc/vmware/vmnet1/smb/var/locks

smb passwd file = /etc/vmware/vmnet1/smb/private/smbpasswd

codepage dir = /usr/lib/vmware/smb/codepages

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = MSHOME

# server string is the equivalent of the NT Description field
server string = %h Kubuntu (Samba, Ubuntu)

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
max protocol = NT
ldap ssl = No
server signing = Auto
map to guest = Bad User
guest account = ted
guest ok = yes
security = share

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
case sensitive = no
msdfs proxy = no

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

### Post by otherdave on 2005-07-07
I'm sorry I don't have more time to post my smb.conf file and provide some links but I noticed that your netbios name is a word<dot>anotherword. Try making it just one word.

Also, check the VMWare site, they have a lot of sample config files. A few things:

1) Your VM and Samba have to have the same workgroup
2) Every user on linux that will use the VM share MUST have an account on the VM with the same password and name. I think this is very important
3) I am using bridged networking, so I'm not sure of your setup or how this changes things.

---

### Post by t2kburl on 2005-07-07
thanks ...  I copied several lines from the sample smb.conf on the vmware site. I also changed my netbios name ...  haven't had a chance to reboot (is there another way to "restart samba"?)
to test the new settings.
I have removed all the doubled up lines also.
I am using host only netwrking. Maybe I'll re-run vmware-config and make it a bridged network instead

---

### Post by otherdave on 2005-07-08
[QUOTE=t2kburl]haven't had a chance to reboot (is there another way to "restart samba"?)[/QUOTE]

There sure is:

$ sudo /etc/init.d/samba restart

I know there are two services that need to be restarted and this command does both of them, I'm not sure what the other one is (besides samba)

---

### Post by otherdave on 2005-07-08
[QUOTE=t2kburl]thanks ...  I copied several lines from the sample smb.conf on the vmware site. I also changed my netbios name ...  haven't had a chance to reboot (is there another way to "restart samba"?)
to test the new settings.
I have removed all the doubled up lines also.
I am using host only netwrking. Maybe I'll re-run vmware-config and make it a bridged network instead[/QUOTE]

Before I forget: Make sure you do the bit about the usernames. I think that's pretty important. If your Linux username is 'dave' then make sure you WindowsXP username is 'dave' and that they have the same password.

Then do the 'smbpasswd -a dave' command and use the same password there. When I get home tonight I'll try to re-post my smb.conf file.

---

### Post by t2kburl on 2005-07-08
this was interesting .... maybe a problem ????

when I restarted samba I got this message :

Failed to terminate process 8449 : No such process   [ok]

When I try to check my samba (using Remote Places in KDE) I get a message stating that no workgroups can be found.

 ](*,)

---

### Post by otherdave on 2005-07-08
hehe, I have no idea what that means :) I also don't use KDE so I'm not sure about the network neighborhood bit. In fact, I haven't tried to browse FROM linux TO my vmware (Win XP) yet :)

Maybe you should edit that config file and then reboot? 

Here's my smb.conf file, by the way. If you followed the VMWare pages, they had you set up a user mapping in /etc/samba/smbusers I think. Mine looks like:

dave="dave"

(yes, the quotes are there on the right side).
And I added a password for dave with smbpasswd.

[global]

workgroup = MYGROUP
netbios name = hocus-pocus 

server string = %h is a fuzzy critter

load printers = yes

printing = cups
printcap name = cups

log file = /var/log/samba/log.%m
max log size = 50

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

wins support = yes

hosts allow = all
interfaces = eth1 vmnet1

security = user
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd

dns proxy = no

preserve case = yes
short preserve case = yes
default case = lower

[homes]
comment = Home Directories
browseable = yes
writable = yes

[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700
   use client driver = yes
   guest only = yes

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes

[DaveShared]
path = /home/dave/Desktop/Shared
comment = Daves Stuff!
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes

---

### Post by t2kburl on 2005-07-09
i don't know ...   I've done it all  ... my smb.conf looks almost exactly like yours now (just changed everything to the values I use)
did the passwd thing in XP and with smb ...
I'm not sure I have my netbios right
How can you find out what it is supposed to be?

because it still isn't working     ](*,)

---

### Post by otherdave on 2005-07-11
Can you post your smb.conf again? Also, did you switch it to use Bridged networking? Are you sure 'VMNET 1' is the network that VMWare is using?

---

