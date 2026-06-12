---
title: "Cups - localhost:631 get a 404 error"
date: 2006-08-27
forum: Desktop Environments
---

### Post by MrYouP on 2006-08-27
Hello everybody !!

My cups server is gone away one a kubuntu dapper install !

It start well but seems to refuse to answer anything.

When I try to go to localhost:631, I've got the following logs :
D [27/Aug/2006:17:24:29 +0200] cupsdCloseClient: 5
D [27/Aug/2006:17:24:41 +0200] cupsdAcceptClient: 5 from localhost:631 (IPv4)
D [27/Aug/2006:17:24:41 +0200] cupsdReadClient: 5 GET / HTTP/1.1
D [27/Aug/2006:17:24:41 +0200] cupsdReadClient: 5 Browser asked for language "fr.utf-8"...
D [27/Aug/2006:17:24:41 +0200] cupsdAuthorize: No authentication data provided.
D [27/Aug/2006:17:24:41 +0200] cupsdSendError: 5 code=404 (Not Found)

When I try to add a printer into the KDE interface, I've got the following logs :
D [27/Aug/2006:17:22:48 +0200] cupsdCloseClient: 5
D [27/Aug/2006:17:22:52 +0200] cupsdAcceptClient: 5 from localhost:631 (IPv4)
D [27/Aug/2006:17:22:52 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [27/Aug/2006:17:22:52 +0200] cupsdAuthorize: No authentication data provided.
D [27/Aug/2006:17:22:52 +0200] CUPS-Get-Devices ipp://localhost:631/printers/
D [27/Aug/2006:17:22:52 +0200] CGI /usr/lib/cups/daemon/cups-deviced started - PID = 5139
I [27/Aug/2006:17:22:52 +0200] Started "/usr/lib/cups/daemon/cups-deviced" (pid=5139)
D [27/Aug/2006:17:22:52 +0200] cupsdSendCommand: 5 file=6
E [27/Aug/2006:17:22:52 +0200] PID 5139 (/usr/lib/cups/daemon/cups-deviced) stopped with status 22!
D [27/Aug/2006:17:22:52 +0200] [CGI] /usr/lib/cups/daemon/cups-deviced: Permission denied

And then interface hang until I stop cups manually
And of course it refused to print anything

Anybody got an idea ?

---

### Post by bobpaul on 2006-09-13
This happened on one of our gentoo servers and was the result of a mangled /etc/cups/cupsd.conf. I restored from backup. I'm not sure if/where Ubuntu stores backups of config files...

try ```
find / | grep cupsd.conf
``` and see if you can find a copy of the file from back when things worked. Otherwise you could try deleting unininstalling cups (and deleting the /etc/cups folder) and then reinstalling. **NOTE if you delete the /etc/cups folder all cups configuration data will be lost and you will have to reconfigure all of your printers!**

This is what I would try.

---

### Post by kiev on 2007-09-09
Ten same problem!!! 404 not found
(ubuntu gutsy last)

---

### Post by alph4bet4 on 2008-04-10
I too had the same problem.  The issue turned out to be that I had incorrectly specified the cups user and group accounts (more correctly, I forgot to supply them during configuration).

My solution was to recompile and specify the --with-cups-user and --with-cups-group options and then everything worked correctly.

-- I should add that I use Slackware, not Ubuntu, but I'm assuming that the root issue may be the same

---

