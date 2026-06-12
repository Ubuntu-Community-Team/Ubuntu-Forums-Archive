---
title: "Sharing a drive from linux to about 5 windows computers"
date: 2006-06-16
forum: Desktop Environments
---

### Post by CameronCalver on 2006-06-16
Hello at my dads work he has about 5 or 6 computer all running winxp but i am getting him to slowly migrate to linux so first he has a server all it does is share a partition which is the Z: drive and i want all the other winxps to be able to access that drive through the explorer and i dont want ftp.
Should i install ubuntu server or just normal ubuntu and i need some1 that will give me a how to one step at a time and i have never done this b4 so i might seem a bit stupid

---

### Post by el3ktro on 2006-06-16
Usually, this is actually pretty simple. Install an Ubuntu server, or if you prefer some GUI tools, you can also install a complete Ubuntu desktop, so you can also try Ubuntu as a desktop OS.

To give your Win XP machines access to the Ubuntu machine (as a file server), you have to install "samba". Then you need a directory on your Ubuntu machine which holds all the data for your Win XP machines, and you can "share" this directory. Depending on your security needs you can give all users access to this share without username/password, or you create one user for each Win XP machine, so the users can access the share with their username/password.

Well, install Ubuntu first, then you can continue to set up Samba ...

Tom

---

### Post by rado_london on 2006-06-16
Hi. You dont need server linux, you will be fine with normal installation. All you need though is samba- this is the protocol that will allow you to share partitions with windows as well as accessing already shared once. To install samba go to the terminal and type in:
```
sudo apt-get install samba
```
Then you have to configure it which is painfull. To get a good manual click [here]("http://www.linuxheadquarters.com/howto/networking/samba.shtml"). I haven't tested the above link if the solution works but as I read it looks OK and fits your needs.

Good luck and report the result.

---

### Post by CameronCalver on 2006-06-16
Ok im downloading now and i am doing everything you say on our home netowkr so when i know how to do it i can quickly set it up at work so it doesnt not have everthing down for too long and is it the same sharin /home/username/share as /media/partition

---

### Post by CameronCalver on 2006-06-16
k samba is installed 

next step plz

---

### Post by rado_london on 2006-06-16
You can create a share directory more than one user has permission to view. This is similar to a Linux/Unix group definition. The best way to explain this is to show an example:
[myshare]
comment = Share for John and Sam
path = /usr/share
valid users = john sam
public = no
writable = yes
printable = no
create mask = 0765

This shares the directory /usr/share for only the users john and sam. It is writable which means both john and sam have write permissions to the shared directory. Any files/directories created in the shared directory will have the permission 0765.

EDIT: Follow the link for full explanation. The link is in my previous post.

---

### Post by CameronCalver on 2006-06-16
i want a step to step like el3ktro is giving me and i dont want users to have to type in  name and password

---

### Post by CameronCalver on 2006-06-16
So i have installed samba now what

---

### Post by scxtt on 2006-06-16
i would have used NFS myself, you can have NFS shares mounted on startup, even "reconnect @ login" in XP ...

---

### Post by CameronCalver on 2006-06-16
I have a vfat already set up

---

### Post by CameronCalver on 2006-06-16
What do i do next i really need some help it is urgent that i set this up

---

### Post by scxtt on 2006-06-16
NFS is an alternative to SMB, not a disk format method (like vfat) ... it's much more universal than samba, meaning linux isn't using SMB cause that's what windows makes use of ...

i know that doesn't help you, but NFS would be easier to use than all the configs for SMB ... you could still do it, or even do both ...

---

### Post by tedt on 2006-06-16
Nautilus has built in controls to smb try right clicking on the folder and select share.  Otherwise set up the samba config file like you were show on the previous page,

---

### Post by CameronCalver on 2006-06-16
well scxtt if that nfs is easier ill use that but thats only if you can give me step by step

---

### Post by scxtt on 2006-06-16
carry on w/ SMB, and if it isn't working for you by the time i get in front of my computer (at work now, for 3+ hours more) i'll get you some directions for NFS ...

---

### Post by tedt on 2006-06-16
Did you try to right click on a directory in nautlius and select sharing

---

### Post by CameronCalver on 2006-06-16
Where is the smb.conf i want to edit the allow and deny stuff and the workgroup and server string

---

### Post by CameronCalver on 2006-06-16
[QUOTE=tedt]Did you try to right click on a directory in nautlius and select sharing[/QUOTE]

yeah i did but how do i access the shared folder on windows

---

### Post by CameronCalver on 2006-06-16
can some1 plz help me i really dont havwe clue where to start

---

### Post by peter1632 on 2006-06-16
I am working on a similar samba/xp situation.  Both my kids are on XP boxes, and I also have one.  I've also set up a Dapper/Ubuntu linux box with samba.  I can *see *the XP boxes from the linux box.  But cannot sign onto the linux box from the XP's.  And I also want the linux box to show up as a drive on the kid's pcs.  I suspect the problem may be that we don't use passwords on the XP machines at home.  Is that the source of the problem?  or is there some user/share issue in smb.conf I've not addressed.

---

### Post by rturner on 2006-06-16
You should read the links others have put up.  Here's another one:

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

You want to make sure you have the same workgroup as the Windows workgroup at the top of your smb.conf.  Put your netbios name in (name of your machine).  Share a directory according to the instructions.  Follow directions, restart samba.  See if the shared directory is showing up in the XP machines under My Network Places.

Follow the directions and try to connect.  Then post back here if it's not working and people can probably troubleshoot what the glitsch is.   Once set up, it's a breeze, but you have to get started first and troubleshoot anything that isn't functioning.

---

### Post by CameronCalver on 2006-06-16
how do i find out the netbios and the workgroup name on my windows machine i am a noob on windows i need to find out the name of the windows

---

### Post by rturner on 2006-06-16
[QUOTE=peter1632]I am working on a similar samba/xp situation.  Both my kids are on XP boxes, and I also have one.  I've also set up a Dapper/Ubuntu linux box with samba.  I can *see *the XP boxes from the linux box.  But cannot sign onto the linux box from the XP's.  And I also want the linux box to show up as a drive on the kid's pcs.  I suspect the problem may be that we don't use passwords on the XP machines at home.  Is that the source of the problem?  or is there some user/share issue in smb.conf I've not addressed.[/QUOTE]

I'm not sure about the lack of passwords, but I found it helpful to have user accounts on the linux box that correspond w/passwords to the user accounts on my Windows machines.  Create smbusers that correspond to the Windows machine users.

---

### Post by rturner on 2006-06-16
[QUOTE=CameronCalver]how do i find out the netbios and the workgroup name on my windows machine i am a noob on windows i need to find out the name of the windows[/QUOTE]
If you right-click My Computer on the Windows machines and select properties, it lists the workgroup on the first tab.  The netbios name is just the name of your linux machine.  For instance, my home soho LAN is part of a workgroup called ecg.  All machines are part of that workgroup, including the ubuntu machine, set at the top of smb.conf.  Without that basic step, you'll never see the ubuntu server.

---

### Post by peter1632 on 2006-06-17
In your post, rturner, you note that I should read other posts.  I appreciate the heads-up, understand such reminders, and very much appreciate the help from you and the community.  Do know that I've been reading these posts and anything else I can google for several weeks, as well as the SAMBA books that were installed with the program.  I seem to be missing some key point...

Here is some of the system data; the Ubuntu box is listed in /etc/hosts as 
   127.0.0.1 localhost
   127.0.1.1 desperaux

but if I run ifconfig I get a report that it is 192.168.1.6

On my desk I also have the XP box, and ipconfig tells me it is 192.168.1.4

I have created a directory on the Dapper system called /usr/share/samba/tmp (similar to the Samba 3 book accessed via SWAT).  I had entered root when I did this, so the owner is root and the permissions are set to 777.

All computers in the house are members of the same workgroup (named after the kid's cat, who is named after a squirel who had his own cartoon show).

In samba.conf I have added

[test]
   comment = for testing share from XP box
   path = /sur/share/samba/tmp
   read only = No
   read ok = Yes
   browseable = Yes

then, from within SWAT, I restarted smbd and nmbd (winbindd is not running).

I then attempted to access the linux box.  I get as far as I have in the past ... I get the dialog asking for username and password.  This is where I am stuck.

[rturner] -- you have suggested building an smbuser list (right?) using the passwords of the XP boxes, but we don't use passwords.  I'm still suspecting that my XP to Samba login problem is that we don't use passwords (I'd like to keep it that way, if possible).

Thoughts?

---

### Post by CameronCalver on 2006-06-17
> **peter1632]In your post, rturner, you note that I should read other posts.  I appreciate the heads-up, understand such reminders, and very much appreciate the help from you and the community.  Do know that I've been reading these posts and anything else I can google for several weeks, as well as the SAMBA books that were installed with the program.  I seem to be missing some key point...

Here is some of the system data said:**
> 
   comment = for testing share from XP box
   path = /sur/share/samba/tmp
   read only = No
   read ok = Yes
   browseable = Yes

then, from within SWAT, I restarted smbd and nmbd (winbindd is not running).

I then attempted to access the linux box.  I get as far as I have in the past ... I get the dialog asking for username and password.  This is where I am stuck.

[rturner] -- you have suggested building an smbuser list (right?) using the passwords of the XP boxes, but we don't use passwords.  I'm still suspecting that my XP to Samba login problem is that we don't use passwords (I'd like to keep it that way, if possible).

Thoughts?

peter plz this is my thread and i need help so can you plz make your own thread

---

### Post by CameronCalver on 2006-06-17
ok the work group is called CALVER and my ubuntu computer is called cameron@ubuntu so so i di just cameron for netbios this is the conf

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup =CALVER

# server string is the equivalent of the NT Description field
   server string =????

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

can you fill it in for me

---

### Post by rturner on 2006-06-17
[QUOTE=CameronCalver]ok the work group is called CALVER and my ubuntu computer is called cameron@ubuntu so so i di just cameron for netbios this is the conf[/QUOTE]
I assume your login is cameron and your computer name is ubuntu.  If so, ubuntu would be your netbios name.  You can check by going to System/Administation/Networking.  Click on properties for your NIC, select General tab and see what it says for Hostname.  That's your netbios name.


Here's my Global Settings.  But keep in mind, it's for *my* LAN.  I have a computer running XP Pro as the file server.  I want *it* to be the master browser, so I've turned that off on my linux computer:

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = ECG

netbios name = dionysus

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
   name resolve order = lmhosts host wins bcast

os level = 0
lm announce = No
preferred master = No
local master = No
domain master = No

---

### Post by rturner on 2006-06-17
Peter, sounds like you could fix it with adding smbusers.  I don't recall, but you may be able to just hit the enter key when it asks for passwords.  Probably best to start a thread and get help w/smbusers.  The 192.168.1.x ip addresses sound fine, probably supplied by your router.  I have static IPs, but that's not really necessary.

---

### Post by blkish on 2006-06-17
[QUOTE=CameronCalver]Hello at my dads work he has about 5 or 6 computer all running winxp but i am getting him to slowly migrate to linux so first he has a server all it does is share a partition which is the Z: drive and i want all the other winxps to be able to access that drive through the explorer and i dont want ftp.
Should i install ubuntu server or just normal ubuntu and i need some1 that will give me a how to one step at a time and i have never done this b4 so i might seem a bit stupid[/QUOTE]

although this may be a little late to mention if you already have the hardware lined up, you might like to seriously consider some form of RAID setup for the hard disks, and backup system for the data they contain.

i don't know how 'important' the data that will be contained on this server will be, but consolidating it onto a linux box provides many ways to simply increase the reliability of this data storage.

software raid 1 (mirrored disks) or better a 3ware hardware raid card would both work well.

you might like to consider an uninteruptible power supply (UPS) especially if you are using software raid with write-caching on the discs turned on. APC models are a sound choice.

all the above items are available reasonably cheaply on ebay.

good luck!

blkish

---

### Post by stoneguy on 2006-06-17
Cameron,

I hate to say it, but it sounds like you don't know a lot about server-side Linux. And you say you don't know much about Windows. If that's the case, you're not the right person to undertake this, particularly in a business environment where time is money.

As people have pointed out, info is available. Terpstra's _Samba 3 By Example_ discusses everything needed. But get some experience where you have time and freedom to screw things up. And tell your Dad to hire a professional if he really wants to do this. It's a day's work to set up a peer-networked server for someone who knows what s/he's doing.

---

### Post by peter1632 on 2006-06-17
rturner -- thanks.  I will look more into the smbuser.
cameron -- I jumped into your thread b/c it seemed so similar to the problems I was having, in hopes that between the two of us asking questions we might get some sort of synergy going.  My appologies.

Peter

---

### Post by scxtt on 2006-06-17
hey cameron, post the contents of your /etc/samba/smb.conf and we'll see if we can edit it as a team to get it working ... looking @ the one on a box @ work, it doesn't seem to complicated ...

---

### Post by CameronCalver on 2006-06-17
ok my ubuntu computer is cameron@ubuntu and my windows comp is calver and the work group is called HOME

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
workgroup = HOME

netbios name = ubuntu

# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
; wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
; wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
name resolve order = lmhosts host wins bcast

os level = 0
lm announce = No
preferred master = No
local master = No
domain master = No
rturner is offline Report Bad Post   	Reply With Quote Quick reply to this message Multi-Quote with this Post


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

---

### Post by scxtt on 2006-06-17
try this:

first, move your current smb.conf to a backup:
[indent]sudo mv /etc/samba/smb.conf /etc/samba/smb.conf_backup[/indent]

then do:
[indent]sudo vi /etc/samba/smb.conf[/indent]

and paste this in:
```
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options (perhaps too
# many!) most of which are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored. In this example we will use a #
# for commentry and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command "testparm"
# to check that you have not made any basic syntactic errors.
#
#======================= Global Settings =====================================
[global]
        dns proxy = no
        log file = /var/log/samba/%m.log
        #printer = 
        netbios name = ubuntu
        #load printers = yes
        server string = Camerons_Server
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        workgroup = HOME
        os level = 20
        #comment = 
        encrypt passwords = yes
        public = yes
        security = share
        max log size = 50
        kernel oplocks = No

[homes]
        browseable = yes
        comment = Home Directories
        writeable = yes

[public]
        revalidate = yes
        writeable = yes
        public = yes
        path = /public

#[printers]
        #printable = yes
```and after you've done this, samba should be restarted to reload the config file:
[indent]sudo /etc/init.d/smb restart[/indent]then get on a windows box and see what you've got in "network neighborhood" -- note: my "finicky" comment still applies (i.e. maybe restart XP) ...

---

### Post by CameronCalver on 2006-06-17
i have been editing /usr/share/samba/smb.conf lol does that matter

and when i do sudo /etc/init.d/smb restart it says  command not found

---

### Post by CameronCalver on 2006-06-17
YES success i did it it shows up as Camerons_server(ubuntu) yes yes i am so happy  but now i need to make it the z drive  is that hard

---

### Post by CameronCalver on 2006-06-17
Ok i did it i would like to thanks you sxctt and everyone that helped me get it up and running now my dad can slowly migrate to ubuntu

---

### Post by scxtt on 2006-06-17
cool man, glad to hear it worked ...

---

