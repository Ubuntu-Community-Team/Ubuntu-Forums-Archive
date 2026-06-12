---
title: "Why my ubuntu server reset date to 1968 itself ?"
date: 2009-06-22
forum: General Help
---

### Post by mserry on 2009-06-22
Hi, 
 
We are running on Ubuntu 8.04. I have installed webmin, lamp installation and we are running a website with apache mysql and php. 
 
Everything was working fine for month but now, somethings, server become really slow to loading page and to connect via ssh.
 
Finnaly after connecting and checking with the command "date" the server display an incorrect date and time and the year is now 1968.
 
-----------------------------
Linux **** 2.6.24-19-server #1 SMP Wed Jun 18 15:18:00 UTC 2008 i686
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
No mail.
Last login: Thu Jun 18 10:05:04 2009 from 192.168.***.***
****************:~$ date
Tue Sep 17 22:40:58 ADT 1968
 
------------
 
We don't know why the date is getting reset to 1968. To restore the server performance, we need to reset it and magic the date is now correct. Keep getting this error every 2-3 week.
 
Anyone can help?

---

### Post by geirha on 2009-06-22
Perhaps a script run by cron once a month is running "date -s" or "date --set" by a mistake? Hard to say what it could be.

Are you using ntp? [https://help.ubuntu.com/8.04/serverguide/C/NTP.html](https://help.ubuntu.com/8.04/serverguide/C/NTP.html)

---

### Post by BUSHYBOB on 2009-06-22
Could the cmos battery need replacing?

---

