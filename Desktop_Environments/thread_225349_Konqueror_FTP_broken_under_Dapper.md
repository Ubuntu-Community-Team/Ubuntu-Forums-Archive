---
title: "Konqueror FTP broken under Dapper?"
date: 2006-07-29
forum: Desktop Environments
---

### Post by josh2112 on 2006-07-29
I have been using Konqueror's buit-in FTP support for years, always worked great, but since I've upgraded to Dapper I've had problems with the authorization dialog.  I'm running vsftpd, trying to log in through Konqueror.  I'm not sure what's going on here...

Method 1: [ftp://localhost](ftp://localhost)
[INDENT]
The authorization dialog pops up.  I fill in both my username and password and click OK.  A message box pops up and says "Message sent: Login using username=XXX and password=[hidden]  Server replied: 331 Please specify the password. Do you want to retry?"
Retrying will pop up the same error box over and over again, and eventually I'll get a blank window with "Cannot connect to folder .".
[/INDENT]

Method 2: [ftp://XXX@localhost](ftp://XXX@localhost)
[INDENT]
Authrorization dialog pops up with username already fill in, I enter the password, click OK, everything works great.
[/INDENT]

Method 3:  [ftp://XXX:XXX@localhost](ftp://XXX:XXX@localhost)
[INDENT]
Works fine.
[/INDENT]

So why does method 1 not work?  It looks like maybe it's not sending the password, but then /var/log/vsftpd.conf says "[XXX] OK LOGIN: Client "127.0.0.1" and "CONNECT: Client "127.0.0.1"".  So I believe I got successfully logged in but Konqueror misses that somehow and just gets the "specify password" prompt... so maybe some kind of synchronization issue between Konqueror and vsftpd??

Josh

---

