---
title: "Cups remote printing problem"
date: 2006-08-10
forum: Desktop Environments
---

### Post by Termina on 2006-08-10
Both machines are running cups, and it USED to work.

Here's the /var/log/cups/access_log on the server:

> 
will@duron:~$ cat /var/log/cups/access_log
192.168.2.124 - - [10/Aug/2006:11:37:15 -0500] "POST /printers/LaserJet-III-series HTTP/1.1" 200 13504 - successful-ok
192.168.2.124 - - [10/Aug/2006:11:37:15 -0500] "POST /printers/LaserJet-III-series HTTP/1.1" 200 250 Get-Job-Attributes successful-ok
192.168.2.124 - - [10/Aug/2006:11:37:26 -0500] "POST /printers/LaserJet-III-series HTTP/1.1" 200 250 Get-Job-Attributes successful-ok


Here's the /var/log/cups/access_log on the client:

> 
localhost - - [10/Aug/2006:11:45:43 -0500] "GET /ppd/LaserJet-3.ppd HTTP/1.1" 200 10481 - -
localhost - - [10/Aug/2006:11:45:46 -0500] "GET /ppd/LaserJet-3.ppd HTTP/1.1" 200 10481 - -
localhost - - [10/Aug/2006:11:45:46 -0500] "POST /printers/LaserJet-3 HTTP/1.1" 200 44082 - successful-ok


Nothing in error_log on either machines; but nothing is sent to the printer. Local printing on the server is OK.

---

### Post by Termina on 2006-08-10
The problem seems to be client side. When I go to 'localhost:631/printers' I get:

  	
> 
Error:

    Bad Request


---

