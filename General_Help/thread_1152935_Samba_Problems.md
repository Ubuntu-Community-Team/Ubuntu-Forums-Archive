---
title: "Samba Problems"
date: 2009-05-08
forum: General Help
---

### Post by Lybic on 2009-05-08
Ok 
I was using samba share folders to share media with  XBMC on a modded xbox, This was working for about two weeks. Just recently all my samba shares stopped working and I have been pulling my hair out trying to fix it. 

when i try to access shares through dolphin from my laptop to desktop ( both running kubuntu jaunty) i get the error "unable to find any workgoups in your network this could be caused by an enabled firewall" I have checked the firewall and am fairly confident that everything is setup correctly.

Now I have spent several days franticly trying to fix it and am sure I have done more harm than good. I need help....I feel like i need to start fresh but not reinstall the OS fresh....Any help would be greatly appreciated.

I am sure I have messed alot of things up in my search for media streaming happiness

Thanx in advance

---

### Post by Lybic on 2009-05-08
bump

---

### Post by Roasted on 2009-05-08
First thing's first.

Please post your smb.conf.

Secondly, what computers are on the network you're working with in terms of Samba? Any XP? Other Ubuntu machines? 

Just give us as much information as you can and we'll try to help ya figure it out. 


I know how frustrating Samba can be. Off topic but still kinda related - Recently I had a problem connecting to my Samba server. I was so aggrivated I wanted to quit computers all together. Then I realized my spare computer I accidentally gave it the same computer name as my Ubuntu server... Renamed my spare pc... Samba worked...

So post your smb.conf and we'll try to help.

---

### Post by Lybic on 2009-05-08
Ok I have

Desktop - Kubuntu Jaunty  wired
Netbook  - Kubuntu Jaunty wireless
Laptop - Vista ( wifes) wireless
modded xbox  wired

all running through a belkin wireless router


I have to work today so I will be back on a little later below is my smb.conf 

Thanx for helping


```
# Samba config file created using SWAT
# from UNKNOWN (z&#65533;&#65533;&#62263; &#65533;4&#65533;&#65533;&l&#65533;&#65533;&#65533;&#831;&#65533;&#65533;&#65533;&#65533; &#65533;4&#65533;&#65533;2&#65533;&#65533;&#65533;&#831;)
# Date: 2009/05/09 10:52:01

[global]
	workgroup = WORKPLZ
	server string = %h server (Samba, Ubuntu)
	encrypt passwords = No
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[media-share]
	path = /media/1.5_TB
	read only = No
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[test]
	path = /home/lybic/test
	valid users = USERNAME
	read only = No
	guest ok = Yes
[media-share]
	path = /media/1.5_TB
	read only = No
	guest ok = Yes


```
updated smb.conf suing swat....easier to read now

---

### Post by Gnea on 2009-05-08
Noticing a few odd things here, so perhaps modifying these things will help you find a solution. :)

I noticed that it your smb.conf file is rather plain looking.  Have you tried using [SWAT]("https://help.ubuntu.com/community/Swat")?

A few other things.. are you checking the samba logs as you're trying to access the system from the xbox?

```
gnea@box:~/$ tail -f /var/log/samba/log.smbd
```

If it isn't finding the domain 'WORKPLZ' at all, then perhaps samba is crashing. :confused:

---

### Post by Lybic on 2009-05-08
gnea 
I need to check logs but i cant even see other computers in linux

my xbox sees my wifes vista laptop but the two kubuntu machines and the xbox act as if the others dont exist

---

### Post by Lybic on 2009-05-08
update

Dolphin>NEtwork>Samba Shares
gives me nothing but now if i type in the desktop pc name in the address bar my shares show up so i'm making some progress

---

### Post by Lybic on 2009-05-12
help :)

---

