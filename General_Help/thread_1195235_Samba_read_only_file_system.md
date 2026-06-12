---
title: "Samba read only file system"
date: 2009-06-23
forum: General Help
---

### Post by ybardagi on 2009-06-23
Hello 
I'm having a problem with samba configuration thus it don't let me do read-write stuff. It js telling me that the system is read only and it's not

---

### Post by Celauran on 2009-06-23
You haven't given us much to work with. Can you post your smb.conf?

---

### Post by ybardagi on 2009-06-23
[global]
	name resolve order = wins lmhosts bcast
	ldap ssl = no
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	idmap gid = 16777216-33554431
	obey pam restrictions = Yes
	client signing = No
	ntlm auth = No
	client schannel = No
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	passwd program = /usr/bin/passwd '%u'
	dns proxy = No
	cups options = raw
	writable = yes
	idmap uid = 16777216-33554431
	os level = 33
	update encrypted = Yes
	printcap name = cups
	security = user
	machine password timeout = 120
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	server schannel = No
	max log size = 1000
	delete user script = /usr/sbin/userdel '%u'
	winbind separator = @
	winbind nss info = no
	lanman auth = Yes
	log file = /var/log/samba/samba.log
	usershare owner only = No
	passwd chat timeout = 120
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	wins server = 10.8.176.5
	client use spnego = No
	create mask = 0775
	username map = /etc/samba/smbusers
	follow symlinks = No
	winbind trusted domains only = Yes
	winbind use default domain = Yes
	logon home = 
	template shell = /dev/null
	server string = Servidor de GRIAL
	winbind nested groups = No
	unix password sync = Yes
	logon path = 
	client lanman auth = Yes
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	directory mask = 0775
	pam password change = Yes
	winbind cache time = 360

---

### Post by Celauran on 2009-06-23
I don't see any shares defined.

---

### Post by ybardagi on 2009-06-23
[global]
	name resolve order = wins lmhosts bcast
	ldap ssl = no
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	idmap gid = 16777216-33554431
	obey pam restrictions = Yes
	client signing = No
	ntlm auth = No
	client schannel = No
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	passwd program = /usr/bin/passwd '%u'
	dns proxy = No
	cups options = raw
	writable = yes
	idmap uid = 16777216-33554431
	os level = 33
	update encrypted = Yes
	printcap name = cups
	security = user
	machine password timeout = 120
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	server schannel = No
	max log size = 1000
	delete user script = /usr/sbin/userdel '%u'
	winbind separator = @
	winbind nss info = no
	lanman auth = Yes
	log file = /var/log/samba/samba.log
	usershare owner only = No
	passwd chat timeout = 120
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	wins server = 10.8.176.5
	client use spnego = No
	create mask = 0775
	username map = /etc/samba/smbusers
	follow symlinks = No
	winbind trusted domains only = Yes
	winbind use default domain = Yes
	logon home = 
	template shell = /dev/null
	server string = Servidor de GRIAL
	winbind nested groups = No
	unix password sync = Yes
	logon path = 
	client lanman auth = Yes
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	directory mask = 0775
	pam password change = Yes
	winbind cache time = 360

---

### Post by Celauran on 2009-06-23
Which directories are you trying to share? There are no shares listed in the smb.conf you posted. How are you going about sharing?

---

### Post by Hund on 2009-06-23
I'm using Samba on my server and the sharing part in my config looks like this:

> [HDD1]
path = /media/HDD1/
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = johan
hosts allow = 127.0.0.1 <My IP>
hosts deny = 0.0.0.0/0

My smb.conf:

> [global]
; General server settings
netbios name = <Server Name>
server string =
workgroup = <Name>
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = no

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

[HDD1]
path = /media/HDD1/
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = johan
hosts allow = 127.0.0.1 <My IP>
hosts deny = 0.0.0.0/0

I'm only allowing a specific user and a specific IP adress to, remove that part if you dont want it.

---

### Post by ybardagi on 2009-06-23
I didn't think that was necesary. Sorry.
[Docencia]
	path = /home/shares/Docencia/
	invalid users = root
	valid users = nobody, yasser, @profes
	admin users = yasser, root
	read list = nobody
	write list = yasser, @profes
	guest ok = Yes

[Procesamiento de Lenguaje]
	comment = Printer Drivers
	path = /home/shares/speech and processing 2
	invalid users = root
	guest ok = Yes

---

### Post by ybardagi on 2009-06-23
I didn't think that was necesary. Sorry.
[Docencia]
	path = /home/shares/Docencia/
	invalid users = root
	valid users = nobody, yasser, @profes
	admin users = yasser, root
	read list = nobody
	write list = yasser, @profes
	guest ok = Yes

[Procesamiento de Lenguaje]
	comment = Printer Drivers
	path = /home/shares/speech and processing 2
	invalid users = root
	guest ok = Yes

---

### Post by Celauran on 2009-06-23
Have you checked permissions on /home/shares/Docencia? Regardless of what's in smb.conf, if the directory itself does not grant write access, you're out of luck.

---

