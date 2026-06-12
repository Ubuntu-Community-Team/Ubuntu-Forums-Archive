---
title: "Samba Problem: Directory Creation"
date: 2009-03-15
forum: General Help
---

### Post by Prospero2006 on 2009-03-15
Problem: 
When I try to create a directory on my samba server, it always locks
me out as being read only. I can change the name of the directory or
delete it, but I can't put anything into the folder.

-The server is running on a machine across the room from me.

-The administrator on that machine has a different name than
the administrator account on the machine I am using to access it.

The share is mounted in /etc/rc.local like this:

 mount -t smbfs //192.168.2.100/500gb /500gb -o username=joe,password=XXXX

-(joe is the adminstrator name on the client machine.)
-I created a user called joe and added him using smbpasswd -a joe 
on the server.

-I added joe to the 'admin' group 

The server config file looks like this:

[500gb]
   comment = 500
   path = /500gb 
   guest ok = yes
   writeable = yes
   create mask = 0777
   directory mask = 0777
   directory mode = 0777




Any suggestions out there?

I can place files, but I can't create directories with write access....

(When I run gksudo nautilus, everything works fine and I can fully access the share.)

Any suggestions are appreciated, and thank you!

---

