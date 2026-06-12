---
title: "mount permissions samba &amp; linux fs"
date: 2005-12-20
forum: Desktop Environments
---

### Post by dwanders on 2005-12-20
I have a second hard in my PC that I am using as my data drive. So I am mounting this drive with /etc/fstab and the following entry:

/dev/hdb1  /home/da/documents  ext3 defaults       0       0

Then I can use this drive as normal to store all of my data. This is working fine :D. I also have a need to share out this directory so that it gets backed up on a nightly basis. We have a Windows server :confused: that backs up our data folders every night so I have shared out this mounted drive with the following smb.conf:

# Global Settings =======================

[global]
dns proxy = no
wins support = no
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
ldap ssl = No
server signing = Auto
workgroup = CORP
server string = PC202

#### Debugging/Accounting ####
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

####### Authentication #######
security = share
##Backup Windows server IP Address 
hosts allow = 1.1.1.2

########## Printing ##########


######## File sharing ########


############ Misc ############
socket options = TCP_NODELAY

# Share Definitions =======================

# Nightly Backup

[work]
comment = PC202 Work
read only = no
locking = no
path = /home/da/documents
guest ok = yes
browseable = yes

When I try to access this share from the backup server (at ipaddress 1.1.1.2) I get:

\\PC202\work is not accessible
Network access is denied

:confused: 
I am sure that I have just missconfigured something, but I am not seeing the forest through the trees. Any help with this matter is greatly appreciated. 

Thanks in advance.

---

### Post by dcstar on 2005-12-20
[QUOTE=dwanders]I have a second hard in my PC that I am using as my data drive. So I am mounting this drive with /etc/fstab and the following entry:

/dev/hdb1  /home/da/documents  ext3 defaults       0       0
......
comment = PC202 Work
read only = no
locking = no
path = /home/da/documents
guest ok = yes
browseable = yes

When I try to access this share from the backup server (at ipaddress 1.1.1.2) I get:

\\PC202\work is not accessible
Network access is denied

:confused: 
I am sure that I have just missconfigured something, but I am not seeing the forest through the trees. Any help with this matter is greatly appreciated. 

Thanks in advance.[/QUOTE]
What are the RW permissions for the share?

---

### Post by dwanders on 2005-12-21
for the Linux file system? 
ls -la
drwxr--r--   7 danderson danderson    4096 2005-12-21 09:00 documents

for Samba, I think:
read only = no
guest ok = yes
browseable = yes

Are you asking for something else?

---

