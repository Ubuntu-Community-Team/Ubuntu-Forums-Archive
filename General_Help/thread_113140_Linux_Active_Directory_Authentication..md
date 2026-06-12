---
title: "Linux Active Directory Authentication."
date: 2006-01-05
forum: General Help
---

### Post by Mattj on 2006-01-05
Hi all, 

This isnt really an ubuntu specific question, but ive been told this place has some of the most helpful and knowlageable people compared to a lot of linux forums, so im going to ask (Out of desperation really)

I am trying to get my linux PC to allow logons from my windows 2003 active directory domain, Have followed many many howto's all along a general theme, *

*Setup Kerberos, test, then winbind and samba. And suddenly everyrthing will work....*

Or not!

Anyway, Have setup kerberos, heres my /etc/krb5.conf file:

```
# krb5.conf

[libdefaults]
 ticket_lifetime = 24000
 default_realm = HSLPRODUCTIONS.LOCAL
# dns_lookup_realm = true
# dns_lookup_kdc = true
 dns_fallback = yes

[realms]
 HSLPRODUCTIONS.LOCAL = {
  kdc = masterad.hslproductions.local
  default_domain = hslproductions.local
 }

[domain_realm]
masterad.hslproductions.local = HSLPRODUCTIONS.LOCAL


[appdefaults]
 pam = {
   debug = false
   ticket_lifetime = 36000
   renew_lifetime = 36000
   forwardable = true
   krb4_convert = false
 }

[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

#[kdc]
# profile = /var/kerberos/krb5kdc/kdc.conf

```


And my /etc/samba/smb.conf file is as follows:
```
# smb.conf
# SAMBA CONFIG FILE
# SADMS
# 2005-06-20

[global]

# netbios name
        netbios name = LinuxTS

# server string is the equivalent of the NT Description field
        server string = Samba Server LinuxTS

# realm = Kerberos realm
        realm = HSLPRODUCTIONS.LOCAL

# workgroup = NT-Domain-Name or Workgroup-Name
        workgroup = HSLPRODUCTIONS

# Security mode.
        security = ADS

# Use password server option only with security = server
        password server = *

# Password encryption
        encrypt passwords = yes

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network.
        hosts allow = 172.16.0.0/255.255.0.0 127.
        hosts deny = 0.0.0.0/0.0.0.0

# Uncomment this if you want a guest account, you must add this to /etc/passwd
# otherwise the user "nobody" is used
        guest account = nobody

# this tells Samba to use a separate log file for each machine
# that connects
;       log file = /var/log/samba/%m.log;
        log file = /var/log/samba/samba.log

# The following are needed to allow password changing from Windows to
# update the Linux system password also.
# NOTE: Use these with 'encrypt passwords' and 'smb passwd file' above.
# NOTE2: You do NOT need these to allow workstations to change only
#        the encrypted SMB passwords. They allow the Unix password
#        to be kept in sync with the SMB password.
;       unix password sync = Yes
;       passwd program = /usr/bin/passwd %u
;       passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*

# Unix users can map to different SMB User names
        username map = /etc/samba/user.map
# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;       include = /etc/samba/smb.conf.%m

# Most people will find that this option gives better performance.
# See speed.txt and the manual pages for details
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

# All NetBIOS names must be resolved to IP Addresses
# 'Name Resolve Order' allows the named resolution mechanism to be specified
# the default order is "host lmhosts wins bcast". "host" means use the unix
# system gethostbyname() function call that will use either /etc/hosts OR
# DNS or NIS depending on the settings of /etc/host.config, /etc/nsswitch.conf
# and the /etc/resolv.conf file. "host" therefore is system configuration
# dependant. This parameter is most often of use to prevent DNS lookups
# in order to resolve NetBIOS names to IP Addresses. Use with care!
# The example below excludes use of name resolution for machines that are NOT
# on the local network segment
# - OR - are not deliberately to be known via lmhosts or via WINS.
;       name resolve order = wins lmhosts bcast

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable it's WINS Server
;       wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
#       Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;       wins server =

# if you want to automatically load your printer list rather
# than setting them up individually then you'll need this
        printcap name = /etc/printcap
        load printers = yes

# It should not be necessary to spell out the print system type unless
# yours is non-standard. Currently supported print systems include:
# bsd, sysv, plp, lprng, aix, hpux, qnx
;       printing = lprng

# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The built-in default for versions 1.9.17 is yes,
# this has been changed in version 1.9.18 to no.
        dns proxy = no

# PAM-related
        obey pam restrictions = Yes
        pam password change = Yes

# Winbind separator
        winbind separator = /
# Winbind use default domain
# This parameter specifies whether the winbindd daemon should
# operate on users without domain component in their username.
# Users without a domain component are treated as is part of
# the winbindd server's own domain. While this does not benefit
# Windows users, it makes SSH, FTP and e-mail function in a way
# much closer to the way they would in a native unix system.
# Default: winbind use default domain = no
   winbind use default domain = yes

# RID to UID map
;       idmap backend = idmap_rid:HSLPRODUCTIONS=10000-60000

# RID idmap does not work with trusted domains
;       allow trusted domains = no

# Domain user id range
        idmap uid = 10000-60000

# Domain group id range
        idmap gid = 10000-60000

# Allow enumeration of domain users and groups
;       winbind enum users = no
;       winbind enum groups = no

# Allow nested groups
;       winbind nested groups = yes

# Winbind templates
# When filling out the user information for a Windows NT user, the
# winbindd(8) daemon uses this  parameter  to  fill  in  the  home
# directory  for that user. If the string %D is present it is sub-
# stituted with the userâs Windows NT domain name. If  the  string
# %U  is present it is substituted with the userâs Windows NT user
# name.
        template homedir = /home/%U

# This option defines the default primary group for each user cre-
# ated  by winbindd(8)âs local account management functions (simi-
# lar to the âadd user scriptâ).
;       template primary group = "HSLPRODUCTIONS/Domain Users"
;       template primary group = "Domain Users"

# When filling out the user information for a Windows NT user, the
# winbindd(8)  daemon  uses  this  parameter  to fill in the login
# shell for that user.
        template shell = /bin/bash

# Services
        default service = homes
        preload = global homes printers

# Default share values
        valid users = @"HSLPRODUCTIONS/Domain Users"
        admin users = "HSLPRODUCTIONS/administrator"
#==================


 write list =
        template primary group = users
[homes]
        comment = Home Directory
        browseable = no
        writable = yes
        valid users = @"HSLPRODUCTIONS/Domain Users"
;       read only = No
;       create mask = 0664
;       directory mask = 0775

[users]
        path = /home
        comment = All Home Directories
        browseable = yes
        writable = yes
        valid users = @"HSLPRODUCTIONS/Domain Users"
        admin users = "HSLPRODUCTIONS/administrator"
        read list = @"HSLPRODUCTIONS/Domain Users"
        write list = @"HSLPRODUCTIONS/Domain Users"

[data]
        path = /data
        comment = Data
        browseable = yes
        writable = yes
        valid users = @"HSLPRODUCTIONS/Domain Users"
        admin users = "HSLPRODUCTIONS/administrator"
        read list = @"HSLPRODUCTIONS/Domain Users"
        write list = @"HSLPRODUCTIONS/Domain Users"

;[tmp]
;       comment = Temporary file space
;       path = /tmp
;       read only = no
;       public = yes

# NOTE: If you have a BSD-style print system there is no need to
# specifically define each individual printer
[printers]
        comment = All Printers
        path = /var/spool/samba
        browseable = no
        guest ok = no
        writable = no
        printable = yes
        ;public = yes
        ;to allow user 'guest account' to print

```

The whole point of this is to allow my windows users to log onto this linux box using their active directory usernames and passwords.

I joined the domain using 'net join ads'

To which the system replied fine. (on running it a second time i get):
```
[root@LinuxTS ~]# net ads join
[2006/01/06 01:11:01, 0] libads/ldap.c:ads_add_machine_acct(1405)
  ads_add_machine_acct: Host account for linuxts already exists - modifying old account
Using short domain name -- HSLPRODUCTIONS
Joined 'LINUXTS' to realm 'HSLPRODUCTIONS.LOCAL'
[root@LinuxTS ~]# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: administrator@HSLPRODUCTIONS.LOCAL

```

i can now list all users and groups in active directory using 'wbinfo -u' (for showing users) and 'wbinfo -g' (for groups) and the information it returns is correct.

But according to everything ive been reading, the real test is running 'getent passwd' and i should see the contents of my /etc/passwd file, plus domain users.

However, i only see contents of /etc/passwd ... and i still cant log onto the linux machine using an AD account, neither can i authenticate to samba using  [email]administrator@HSLPRODUCTIONS.LOCA[/email]L

could someone PLEASE help, any suggestions, comments etc etc, Have tried many manual configs, automated programs that are meant to make this work, the lot. Need help, anyone??

Would be so so so useful. Just cant think what could be wrong.

Cheers
-Matt

(i hope people are still up lol :P)

---

### Post by mikeyman on 2006-04-24
Try resetting the Administrator password in AD. This will get the Kerberos Ticket mechanism working with Samba/Winbind. This has to be done whether you upgraded from AD2000 to 2003 or installed AD2k3 from scratch.

---

### Post by ximok on 2006-04-25
Mattj,

We have just performed the installation you are talking about.

We actually had to use kerberos+winbind to make it work like you did.  I will post some files here tomorrow to help you out. 

I didn't see anything about your pam modules (these are required to pull off logins)

we are using pam_winbind to pull ours off...  So... if you give me 24 hours, you can eyeball my configs and see if they'll help you.

Note: right now I can login just fine, but logins generate a kerberos error in the logs on the domain controller.

---

