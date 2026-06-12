---
title: "Accessing samba server by IP"
date: 2006-08-31
forum: Desktop Environments
---

### Post by shakil on 2006-08-31
Hi,

I have some problem access samba server on ubnutu machine by ip from windows 2000, but access by machine name works fine. I can't even connect by ip localy (from ubuntu), except 127.0.0.1.

Samba configuration file:

[HTML][global]

character set = utf-8 
client code page = 866
preserve case = yes 
short preserve case = yes

workgroup = All
server string = %h server (Samba, Ubuntu)
wins support = no
dns proxy = no

log file = /var/log/samba/log.%m

max log size = 1000

syslog = 0

panic action = /usr/share/samba/panic-action %d

encrypt passwords = true

passdb backend = tdbsam

obey pam restrictions = yes

invalid users = root

passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

socket options = TCP_NODELAY

[fun]
path = /home/fun
comment = zhme
available = yes
browseable = yes
public = yes
writable = yes

[home]
path = /home/shakil
available = yes
browseable = yes
public = yes
writable = yes[/HTML]

---

### Post by mjziegle on 2006-08-31
Start from scratch and follow this guide

[http://ubuntuguide.org/wiki/Dapper#Samba_Server](http://ubuntuguide.org/wiki/Dapper#Samba_Server)

---

