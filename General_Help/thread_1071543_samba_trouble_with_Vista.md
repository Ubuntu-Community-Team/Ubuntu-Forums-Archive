---
title: "samba trouble with Vista"
date: 2009-02-16
forum: General Help
---

### Post by Cr0n_J0b on 2009-02-16
I am having some issues getting my vista client to automatically reconnect to samba after a reboot.  The client OS is Vista Business 64Bit SP1.  The server is running on Ubuntu (latest version) and Samba 3.2.3. 

The symptoms are this.  I browse to the server via \\name or \\IP_address.  I then select a share, map network share to say z:/  It will usually prompt me for authentication just after the initial connection request.  So all is good until i reboot.  Then the drives show up as not connected.  I get notified that they cannot reconnect.  I click on the icon for the mapped device and it fails.  To fix this, I can just browse to the server via \\server, click on the share and then then a folder...and it will reconnect again.  It seems like the authentication isn't getting cached or something.  I've never had this issue before, but then I'm new to using Vista.  By the way I have changed the Specpol.msc to negotiate NTLM from the default.  This was a sticking point for others, but it hasn't seemed to help me. 

here is a copy of my samba config if it will help. 

[global] 
netbios name = linuxgate 
server string = Samba file and print server 
workgroup = EWORKGROUP 
security = user 
hosts allow = 127. 192.168.1. 
interfaces = 127.0.0.1/8 192.168.1.0/24 
bind interfaces only = yes 
remote announce = 192.168.1.255 
remote browse sync = 192.168.1.255 
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
encrypt passwords = true 
unix password sync = yes 
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192 
local master = yes 
domain master = yes 
preferred master = yes 
domain logons = no 
os level = 66 
logon drive = m: 
logon home = \\%L\homes\%u 
logon path = \\%L\profiles\%u 
logon script = %G.bat 
time server = no 
name resolve order = wins lmhosts bcast 
wins support = yes 
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
machine password timeout = 120 
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
machine password timeout = 120 
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

[RAID5] 
path = \RAID5\ 
comment = Main 1.8TB RAID5 share 
valid users = @friends carl-e 
directory mask = 777 
create mode = 777 
force user = 777 
read only = no 
available = yes 
browseable = yes 
writable = yes 
guest ok = no 
public = no 
printable = no

---

### Post by Cr0n_J0b on 2009-02-18
bump

---

