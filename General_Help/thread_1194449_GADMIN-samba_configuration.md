---
title: "GADMIN-samba configuration"
date: 2009-06-22
forum: General Help
---

### Post by epyonite on 2009-06-22
I have installed GADMIN-samba on my Ubuntu computer and I can see it from Vista, but a username/password prompt pops up and i cannot figure out how to correctly configure the passwords in GADMIN-samba or better yet get rid of passwords, in the end im only going to share stuff anyone can have. any help would be apperciated.

Im not sure what information you need so i guess the configuration file would be a good start.

```


[global]
netbios name = Samba24
server string = Samba file and print server
workgroup = LEVISWORKGROUP
security = user
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24
bind interfaces only = yes
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 121
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =

```

---

### Post by AreEK on 2009-06-22
You have security = user, and that means that you need a user on the Samba server with the same user name as on the Win-machines. Do you have a user like that?

---

### Post by zenaan on 2010-09-09
I was very frustrated trying to figure out why gadmin-samba (gas) does not seem to work, wrt users and adding new users. Here's what I found:

- gas in lucid is version 0.2.8
- 0.2.8 does not use pdbedit for retrieving/ changing/ adding/ deleting users. It still uses the old smbpasswd. Or worse, directly reads the /etc/smbpasswd file, I think that's the problem.
- the new samba defaults to using the new tdbsam samba password backend, not the old passdb/smbpasswd backend
- gas 0.2.9 uses pdbedit, which defaults to / works with tdbsam, or goes through the smbd process or something. It works.

gas 0.2.9 can be installed most easily from ppa:

** ppa for gadmin-samba:
[https://launchpad.net/~matthaeus123/+archive/ppa](https://launchpad.net/~matthaeus123/+archive/ppa)
This ppa also has more recent fusesmb and samba, so you may want the ppa for those too.

hth

---

### Post by Mriswithe on 2010-09-15
> **zenaan said:**
> I was very frustrated trying to figure out why gadmin-samba (gas) does not seem to work, wrt users and adding new users. Here's what I found:
- 0.2.8 does not use pdbedit for retrieving/ changing/ adding/ deleting users. It still uses the old smbpasswd. Or worse, directly reads the /etc/smbpasswd file, I think that's the problem.
- the new samba defaults to using the new tdbsam samba password backend, not the old passdb/smbpasswd backend


Thank you!!! I have been fighting samba for days since I recently did a full wipe to make it a gateway as well as a samba server... I have been fighting this trying to figure out what I was doing wrong, decided to get Gadmin going and that couldn't make a user. Thank you again, I am upgrading now.

Mriswithe

---

### Post by OldManRiver on 2011-02-16
All,

I just upgraded to 10.04 and now the users are not registering in the Samba24, so no shares show.  Added the PPA and upgraded, but got the message, "No packages upgraded" as it thinks I'm correct, but still can not create a user in the GADMIN-samba configuration session.

What do I change in the config for this package to point to the right config/user file so the users are collected and maintained?

Thanks!

OMR

---

### Post by OldManRiver on 2011-02-19
All,

This is really frustrating, because now with GADMIN installed I do not go directly to my network, get prompted for a ring password and do not see anything SAMBA at all, where I had local shares before, in places, but was unable to see them from the Windows Network side.

Right now I'm worse than before I installed this.  Help please!  Need this working.

Thanks!

OMR

---

### Post by OldManRiver on 2011-03-21
All,

Installed WebMin and disabled GADMIN-samba.  So far so good!

OMR

---

