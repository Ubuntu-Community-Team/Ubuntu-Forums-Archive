---
title: "External Firewire Fat32 + SAMBA"
date: 2005-02-06
forum: Desktop Environments
---

### Post by FAST on 2005-02-06
Hi everyone.

I've tried discussing this in #ubuntu but have had little success.

Here's the situation:

-I have an external firewire hard drive (FAT32 formatted)
---(note: the drive is automatically mounted when powered on. i'm letting it use the default mount point ->  /dev/sda1 to /media/sda1)
-I would like to share one of the drive's subfolders to a winxp computer

Here's the problem:

-I cannot access the folder via the winxp machine

In my smb.conf file:
(stuff commented out with ; will not be pasted here)
_____________________________________________________________________________

workgroup = MSHOME
server string = %h
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

security = share
obey pam restrictions = yes
invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
pam password change = no

socket options = TCP_NODELAY

[homes]
   comment = Home Directories
   browseable = no
   writable = no
   create mask = 0700
   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[folder]
comment = folder info
writeable = no
path = /media/sda1/folder
public = yes
_______________________________________________________________


For testing purposes, I did change the path for [folder] to '/home/FAST/folder'
and was able to access the folder (and a file in it) from the winxp machine.

Sidenote: I was prompted with 'name / domain / pass screen' , but just clicked okay and got in.

When I changed path back to above, I could not access the folder or contents.

Sidenote: I was prompted with 'name / domain / pass screen' , but just clicked okay and could NOT get in & error message was "Contents of folder could not be displayed."



What can I do !?????!?

---

### Post by FAST on 2005-02-08
have tried several things, including adding entry in fstab for the drive, and setting permissions through that

still no luck accessing via samba

---

### Post by jo. on 2005-02-11
Try mounting the partition using the mount-option "umask=0".

greetings
jo.

---

