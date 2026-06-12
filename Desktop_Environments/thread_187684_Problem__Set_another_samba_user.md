---
title: "Problem : Set another samba user"
date: 2006-06-03
forum: Desktop Environments
---

### Post by wayanwolvie on 2006-06-03
Hi, I wan't to run a samba server in my computer. I added a new samba user (for myself) and I can use the account from other computers to access my samba server. Then I try to add another sama user (guest). But problem's coming. I can't use the guest account to access my samba server. I have tried to set the account using smbpasswd and webmin but the error is still there. The error message is the guest account is not activated or the password input is not correct (the Windows returns one of those error). Can you help me solve my problem??

this is my global setting for smb.conf

> 
[global]
log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY
	wins server = 155.69.5.230
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = %h server (Samba, Kubuntu)
	invalid users = root
	workgroup = MSHOME
	os level = 20
	valid users = tresna guest
	security = share
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000

---

