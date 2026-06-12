---
title: "Can't share files"
date: 2009-03-04
forum: General Help
---

### Post by jmarks on 2009-03-04
I'm running 64 bit Intrepid. Trying to share a folder gives the error 
```
Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":  Permission denied Error loading services.
```If I edit /etc/samba/smb.conf, I see the following

```
[global]
   workgroup = markshome
   netbios name = jmarks-desktop
   server string = anonymous file server
   security = user # was security= share
usernamemap = /etc/samba/smbusers  # this line added for user-level share
   printing = cups
   printcap name = cups
   load printers = yes

[common_share]
   path = /sharedfiles
   comment = anonymous share for all users
   public = yes
   writeable = yes
   browseable = yes

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = no
   create mode = 0700

#==================================Share Definitions
==================================================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. this will share each
# user's home directory as \\server\username
[homes]
comment = Home Directories
browseable = yes
valid users = %S
writeable = yes
```my smbusers file contains one line that I don't understand:
```
jmarks = "jmarks"
```my smbpasswd file also contains one line, beginning 
jmarks: 1000:

Do I need to add something to one of these 3 files to enable me to share files? As is obvious from the smbpasswd file, I am the only user on this machine. My goal is to share a folder that Virtual Box running Windows XP can also access.

thanks for your help.

---

