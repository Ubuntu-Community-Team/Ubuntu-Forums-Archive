---
title: "Samba Network Browsing"
date: 2006-09-24
forum: Desktop Environments
---

### Post by Vuen on 2006-09-24
Hi, I've been trying to properly configure Samba for a month now and I'm getting pretty ******* fed up of it always half-working.

I live in a house with 5 roommates who use Windows XP. I want to share files with them. I don't want any passwords, I just want open read-only shares so they can see my files. This all works, except my computer doesn't show up in Network Neighborhood on their computers, and nothing shows up in Network Servers on mine. They also can't access my computer via \\Nick, and I can't access them via smb://<hostname>. If however they type \\192.168.0.XXX (my local IP) into explorer, they can access all my shares perfectly without passwords, and I can do the same with them via smb://192.168.0.XXX . So network browsing is broken.

Here's my smb.conf:

```
[global]
netbios name = Nick
workgroup = MSHOME
server string = Nick
;%h server (Samba, Ubuntu)
;wins support = yes
;os level = 8

#become master browser
;local master = yes
;os level = 255
;preferred master = yes

log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

security = share
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
guest account = nobody
invalid users = root
unix password sync = no

socket options = TCP_NODELAY


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

[Files]
path = /media/data/files
available = yes
browseable = yes
public = yes
writable = no

```

I've tried a thousand different ways to configure it, and nothing works. I'm sick of this ridiculous configuration process. Ideas anyone?

---

### Post by tjvdberg on 2006-09-24
I think the Windows pc's and you're pc, don't have a way to resolve names to ip adresses. So i think you need a dns server, or WINS. Or you can manualy map the names to ipadresses.

---

### Post by Vuen on 2006-09-24
> Or you can manualy map the names to ipadresses.

That's out of the question. There's no reason this shouldn't just work like any other Windows machine. Furthermore, we use DHCP, so IP addresses change from one day to the next.

I've tried a variety of ways of configuring WINS, and I cannot get it to work. What configuration options should I be setting?

---

### Post by tjvdberg on 2006-09-24
Sorry I don't know anything from WINS. I have always used DNS for this.

---

