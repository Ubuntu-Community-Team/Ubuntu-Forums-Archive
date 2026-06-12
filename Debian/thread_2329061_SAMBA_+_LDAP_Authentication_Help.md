---
title: "SAMBA + LDAP Authentication Help"
date: 2016-06-27
forum: Debian
---

### Post by Leo_Hernandez on 2016-06-27
Hi,

I have a Debian 8 server with Samba installed and configured.


# smbstatus
Samba version 4.2.10-Debian

...


In my lab, I have an Open Directory server (OS X).  My Debian server is bound to Open Directory for authentication.  I also have a Mac (OS X) client bound to Open Directory.  I've created a network login in Open Directory.  I've tested I can login to my Debian server and Mac client machine with that login without any problem.


I've configured Samba to authenticate with Open Directory (see configuration files below).  I initially had issues start Samba, but after I followed some articles on updating the samba schema in OD and "populating" LDAP using smbldap-populate, I got Samba running and seemingly connected to OD.  


Things seems to be working so far and I'm making progress.  In the steps below, I describe the stage I'm at and the issue I'm facing.  For some steps, I refer to attached log files, which are excepts from my smbd.log, that I've capture.  Hopefully this will help show what might be going on:


1.  I am able to start Samba without any issues.  I can see "its talking with OD."


2.  I created a network user called "smbuser" (in OD).  I am able to log into the Mac and Debian server with that account - so LDAP authentication is working.


3.  I have some basic shares set up in Samba.


4.  From the Mac client (logged in as smbuser) I try to access the Samba share (smb://[192.168.40.221]("http://192.168.40.221/"))  *That's the IP of my Debian server.  At this point, I get prompted to provide my login. 
See 01_smbuser_before_smbpasswd_at_login_prompt.txt


5.  I give it my OD login/password and it fails.  
See 02_smbuser_before_smbpasswd_with_OD_password_given.txt


6.  On the Debian server, I add smbuser with:  # smbpasswd -a smbuser
I intentionally provide a different password than what's in OD for smbuser.  
See 03_smbuser_add_via_smbpasswd_-a.txt
Honestly, I don't understand why I have to do this if Samba is authenticating againsts OD, but I do it anyway just to see what happens.  Perhaps once I understand the root cause of my issue, this step will go away as well.  Anyway... read on.



7.  I try to mount the Samba share again.  I'm prompted to provide my login.  Again, I give it my OD password and it fails (again).  
See 04_smbuser_after_smbpasswd_with_OD_password_given.txt


8.  I try to mount the Samba share again.  I'm prompted to provide my login.  This time, I give it the password I created during smbpasswd -a (Step 6).  This time, I am able to access the Samba share.  
See 05_smbuser_after_smbpasswd_with_SMB_password_given.txt


So from what I can tell, even though Samba is connected to OD, it seems to keep a separate password/security database and those password and is authenticating users against that (not OD).  I thought if Samba is configured to use LDAP, then the authentication will be against that directory (ie, the password to access Samba is same as password to login to machine).  


I am obviously a newbie to Samba, but can someone point in the right direction?  Was there a step I missed during my configuration?


Below are my config files for Samba and LDAP on the Debian server. 


smb.conf
```
[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = CP1P-RAW
security = user
map to guest = bad user
dns proxy = no


passdb backend =        ldapsam:ldap://[192.168.40.231/]("http://192.168.40.231/")
ldap suffix =           dc=elcapitan,dc=local
ldap machine suffix =   cn=computers
ldap user suffix =      cn=users
ldap group suffix =     cn=groups
ldap admin dn =         "uid=diradmin,cn=users,dc=elcapitan,dc=local"
ldap ssl = off


load printers = no
printing = bsd
printcap name = /dev/null
disable spoolss = yes


log level = 5



[allusers]
  comment = All Users
  path = /home/shares/allusers
  valid users = @users
  force group = users
  create mask = 0660
  directory mask = 0771
  writable = yes


[homes]
   comment = Home Directories
   browseable = no
   valid users = %S
   writable = yes
   create mask = 0700
   directory mask = 0700


[anonymous]
   path = /home/shares/anonymous
   force group = users
   create mask = 0660
   directory mask = 0771
   browsable =yes
   writable = yes
   guest ok = yes

```

ldap.conf
```
#
# LDAP Defaults
#


# See ldap.conf(5) for details
# This file should be world readable but not world writable.


BASE    dc=elcapitan,dc=local
URI     ldap://[192.168.40.231]("http://192.168.40.231/")
ldap_version 3


binddn uid=diradmin,cn=users,dc=elcapitan,dc=local
bindpw XXXXXXXX




#SIZELIMIT      12
#TIMELIMIT      15
#DEREF          never


# TLS certificates (needed for GnuTLS)
TLS_CACERT      /etc/ssl/certs/ca-certificates.crt


```

---

### Post by howefield on 2016-06-27
Thread moved to the "*Debian*" forum.

---

