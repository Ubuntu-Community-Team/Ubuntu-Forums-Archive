---
title: "SAMBA not sharing the goods"
date: 2005-01-24
forum: Desktop Environments
---

### Post by KLineD on 2005-01-24
I'm trying to get SAMBA working for the second time. When I first installed ubuntu, I followed the "unnoficial" guide to get samba working with my modded xbox (the client) and all when allright, suddenly my gnome installation got screwed and I had to reinstall ubuntu as I couldn't figure that out but I managed to backup the relevant config files.

When I reinstalled ubuntu and samba (and copied the backup config files) the client could access the internet just fine (xbmc could grab RSS news headers) but it could not access the samba shares. Booting my machine into winXP discards the possibility of the client being misconfigured, since it can see and browse all the shares just fine. What's buggin me is that I could do it before reinstalling and I'm doing exactly the same thing.

BTW I'm doing NAT with Firestarter and I also opened the 137-139 ports. I'm running Warty with some all the security updates and some packages updated from the ubuntu backports.

This is my SAMBA config file:

```
[global]
   workgroup = MSHOME
   server string = %h (Samba, Ubuntu)
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   passdb backend = tdbsam guest
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
username map = /etc/samba/smbusers
   socket options = TCP_NODELAY

[homes]
   comment = Home Directories
   browseable = no
   writable = no
   create mask = 0700
   directory mask = 0700

[music]
	comment = music
	path = /home/cesar/music
	public = yes
	writable = no
	valid users = cesar
	create mask = 0700
	directory mask = 0700
	force user = nobody
	force group = nogroup

```

Thanks and I hope someone can figure out what am I doing wrong!

---

### Post by combatwombat_nz on 2005-01-24
Here's my 2 cents worth:
Check the logs. You have them located in /var/log/samba/log.machinename.
Add "log level =3" to get more detail.
Most of these issues are due to the authentication of the Machine account in the Samba password database. Make sure that the machine name for the OS that isn't working is added correctly on the Samba box, and that there is no password assigned to the machine name.

-CW

---

### Post by albersag on 2005-01-25
You have to make 2 things to user smb passsword authentication.

Add a user to system,called cesar as i've seen on your smb.conf

Then "smbpasswd -a cesar" and add your password.

Restart smb server "smbd restart" and try again.

---

### Post by fng on 2005-01-25
Also put "browseable = yes" into the shares.  That solved my problem not seeing the samba shares.

---

### Post by KLineD on 2005-01-25
albersag: I did that already, but thanks a lot
fng: You got that one right!! I didn't knew about that option...

---

