---
title: "Problem with Samba Shares"
date: 2008-12-05
forum: General Help
---

### Post by KagenoKaze on 2008-12-05
Ok I have a server and its main purpose is to host USB drives on the network to back up data at a few branches with less than 100GB of data.  I formatted the drives, labeled them so samba will know which one is which when mounted, and configured samba.  Things seemed well until I went to view them on my XP machine (all other servers are Windows based)  When viewed I can only see the first drive and the others are nowhere to be seen.

Here is my conf

[Backup1]
	comment = Backup1 share
	path = /media/Backup1
	browsable = yes
	guest ok = no
	read only = no
	create mask = 755

[Backup2]
	comment = backup2 share
	path /media/Backup2
	browsable = yes
	guest ok = no
	read only = no
	create mask = 755

[Backup3]
	comment = backup3 share
	path /media/Backup3/
	browsable = yes
	guest ok = no
	read only = no
	create mask = 755

[Backup4]
	comment = drive4 share
	path /media/Backup4/
	browsable = yes
	guest ok = no
	read only = no
	create mask = 755

All I can see is Backup1
Security is user

Thanks in advance

Kage

Edit:

NEVERMIND

Working two weeks straight is messing with me...lol

Thanks anyway

---

