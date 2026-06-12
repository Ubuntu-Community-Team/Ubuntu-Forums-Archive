---
title: "last login (hardy heron)"
date: 2009-04-04
forum: General Help
---

### Post by Wim Sturkenboom on 2009-04-04
I'm trying to figure out when a user logged in for the last time. Both *finger* and *lastlog* provide incorrect information.

```

wim@desktop1:~$ lastlog
Username         Port     From             Latest
root                                       **Never logged in**
daemon                                     **Never logged in**
bin                                        **Never logged in**
sys                                        **Never logged in**
sync                                       **Never logged in**
games                                      **Never logged in**
man                                        **Never logged in**
lp                                         **Never logged in**
mail                                       **Never logged in**
news                                       **Never logged in**
uucp                                       **Never logged in**
proxy                                      **Never logged in**
www-data                                   **Never logged in**
backup                                     **Never logged in**
list                                       **Never logged in**
irc                                        **Never logged in**
gnats                                      **Never logged in**
dhcp                                       **Never logged in**
syslog                                     **Never logged in**
klog                                       **Never logged in**
cupsys                                     **Never logged in**
messagebus                                 **Never logged in**
haldaemon                                  **Never logged in**
hplip                                      **Never logged in**
gdm                                        **Never logged in**
**wim              :0                        Mon Dec 22 16:00:13 +0200 2008**
liza             tty2                      Mon Feb 16 18:32:38 +0200 2009
jade             :0                        Sun Dec 14 11:04:12 +0200 2008
lebatsamai       :21                       Tue Nov 18 16:00:26 +0200 2008
nathan           :0                        Thu Oct 30 16:45:56 +0200 2008
snmp                                       **Never logged in**
**fortyfourgalena  :0                        Mon Dec 22 15:47:37 +0200 2008**
libuuid                                    **Never logged in**
pulse                                      **Never logged in**
festival                                   **Never logged in**
avahi-autoipd                              **Never logged in**
polkituser                                 **Never logged in**
avahi                                      **Never logged in**

wim@desktop1:~$ finger wim
Login: wim            			Name: wim sturkenboom
Directory: /home/wim                	Shell: /bin/bash
On since Sat Apr  4 20:39 (SAST) on tty9 from :0
On since Sat Apr  4 20:40 (SAST) on pts/0 from :0.0
No mail.
No Plan.

wim@desktop1:~$ finger fortyfourgalena
Login: fortyfourgalena			Name: 
Directory: /home/fortyfourgalena    	Shell: /bin/bash
Last login Mon Dec 22 15:47 (SAST) on :0
No mail.
No Plan.
wim@desktop1:~$ 



```The finger information for wim seems to be correct, but lastlog is not. finger and lastlog for user fortyfourgalena are not correct as I logged in as 'him' this morning.

Question is how I check correctly when a user was last logged in? Or what goes wrong?

PS There might be something special about the 22nd of december as it might have been the date that I upgraded from 6.06 to 8.04

---

### Post by bapoumba on 2009-04-04
I got interested by your question, and did a little searching.
I lost the link explaining lastlog shows tty logins (iirc.. Looks okay if I run it on my system).

You may can to try the followings if we are talking about X sessions logins:
```
ck-list-sessions
```
```
last
```

Do not ask me how I got to ConsoleKit ;)

---

### Post by Wim Sturkenboom on 2009-04-05
Thank you, ***last*** did the trick as I want to see the information for other users (my grandkids ;) who use the computer when they're not supposed to use it)

---

### Post by bapoumba on 2009-04-05
> **Wim Sturkenboom said:**
> Thank you, ***last*** did the trick as I want to see the information for other users (my grandkids ;) who use the computer when they're not supposed to use it)
Please do not be to harsh on them. Breaking _some_ boundaries are useful when growing up :)

---

