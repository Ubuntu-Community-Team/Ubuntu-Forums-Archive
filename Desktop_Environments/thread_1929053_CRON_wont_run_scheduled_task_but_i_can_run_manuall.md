---
title: "CRON wont run scheduled task but i can run manually"
date: 2012-02-21
forum: Desktop Environments
---

### Post by thomo2710 on 2012-02-21
Hi all,

Ubuntu 11.04 Desktop 32bit

I have set up a scheduled task to email me reports from Nagios every Monday at 00:01

It didnt run though and the syslog says:


 [COLOR=black][FONT=&quot]Feb 20 00:00:01 UBUNTU CRON[13581]: (user) CMD (/usr/local/nagios/etc/objects/Reports/nagios_reports.sh -p Weekly # JOB_ID_5)[/FONT][/COLOR]
[COLOR=black][FONT=&quot]
[/FONT][/COLOR]
[COLOR=black][FONT=&quot]Feb 20 00:00:01[/FONT][/COLOR][COLOR=black][FONT=&quot] UBUNTU CRON[13578]: (CRON) error (grandchild #13581 failed with exit status 2)[/FONT][/COLOR]
[COLOR=black][FONT=&quot]
[/FONT][/COLOR]
[COLOR=black][FONT=&quot]Feb 20 00:00:01[/FONT][/COLOR][COLOR=black][FONT=&quot] UBUNTU postfix/pickup[27770]: 66D7A10015B: uid=1000 from=<user>[/FONT][/COLOR]
[COLOR=black][FONT=&quot]
[/FONT][/COLOR]
[COLOR=black][FONT=&quot]Feb 20 00:00:01[/FONT][/COLOR][COLOR=black][FONT=&quot] UBUNTU postfix/cleanup[13596]: 66D7A10015B: message-id=<[EMAIL="20120221112801.66D7A10015B@ftlubuntu.fulgent.co.uk"]20120221112801.66D7A10015B@ubuntu.xxxxxxxx.co.uk[/EMAIL]>[/FONT][/COLOR]
[COLOR=black][FONT=&quot]
[/FONT][/COLOR]
[COLOR=black][FONT=&quot]Feb 20 00:00:01[/FONT][/COLOR][COLOR=black][FONT=&quot] UBUNTU postfix/qmgr[1718]: 66D7A10015B: from=<[EMAIL="ftladmin@ftlubuntu.fulgent.co.uk"]user@ubuntu.[/EMAIL][/FONT][/COLOR][COLOR=black][FONT=&quot][EMAIL="20120221112801.66D7A10015B@ftlubuntu.fulgent.co.uk"]xxxxxxxx[/EMAIL][/FONT][/COLOR][COLOR=black][FONT=&quot][EMAIL="ftladmin@ftlubuntu.fulgent.co.uk"].co.uk[/EMAIL]>, size=844, nrcpt=1 (queue active)[/FONT][/COLOR]
[COLOR=black][FONT=&quot]
[/FONT][/COLOR]
[COLOR=black][FONT=&quot]Feb 20 00:00:01[/FONT][/COLOR][COLOR=black][FONT=&quot] UBUNTU postfix/local[13599]: 66D7A10015B: to=<[EMAIL="ftladmin@ftlubuntu.fulgent.co.uk"]user@ubuntu.[/EMAIL][/FONT][/COLOR][COLOR=black][FONT=&quot][EMAIL="20120221112801.66D7A10015B@ftlubuntu.fulgent.co.uk"]xxxxxxxx[/EMAIL][/FONT][/COLOR][COLOR=black][FONT=&quot][EMAIL="ftladmin@ftlubuntu.fulgent.co.uk"].co.uk[/EMAIL]>, orig_to=<user>, relay=local, delay=0.28, delays=0.21/0.01/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)[/FONT][/COLOR]
[COLOR=black][FONT=&quot]
[/FONT][/COLOR]
[COLOR=black][FONT=&quot]Feb 20 00:00:01[/FONT][/COLOR][COLOR=black][FONT=&quot] UBUNTU postfix/qmgr[1718]: 66D7A10015B: removed[/FONT][/COLOR]




So straight away it got a status code of 2 and user has run the script and emailed itself through relay=local even though the script says to email [EMAIL="me@mycompany.co.uk"]me@mycompany.co.uk[/EMAIL] and postfix is configured to send email through my Microsoft Exchange Server.


But if i run the script manually from a terminal logged in as user it works, i recieve the emails and the syslog gets:


[COLOR=black][FONT=&quot]
[/FONT][/COLOR][COLOR=black][FONT=&quot]Feb 21 11:30:43 UBUNTU postfix/pickup[27770]: B531910015B: uid=1000 from=<user>
[/FONT][/COLOR]
[COLOR=black][FONT=&quot][/FONT][/COLOR][COLOR=black][FONT=&quot]Feb 21 11:30:43 UBUNTU postfix/cleanup[15323]: B531910015B: message-id=<[EMAIL="20120221113043.B531910015B@ftlubuntu.fulgent.co.uk"]20120221113043.B531910015B@ubuntu.xxxxxxxx.co.uk[/EMAIL]>[/FONT][/COLOR]
[COLOR=black][FONT=&quot]
[/FONT][/COLOR][COLOR=black][FONT=&quot]Feb 21 11:30:43 UBUNTU postfix/qmgr[1718]: B531910015B: from=<[EMAIL="ftladmin@ftlubuntu.fulgent.co.uk"]user@ubuntu.xxxxxxxx.co.uk[/EMAIL]>, size=157097, nrcpt=1 (queue active)

Feb 21 11:30:44 UBUNTU postfix/smtp[15338]: B531910015B: to=<[EMAIL="andrew@fulgent.co.uk"]thomo2710@xxxxxxxx.co.uk[/EMAIL]>, relay=192.168.1.3[192.168.1.3]:25, delay=0.48, delays=0.16/0/0/0.32, dsn=2.6.0, status=sent (250 2.6.0 <[EMAIL="20120221113043.B531910015B@ftlubuntu.fulgent.co.uk"]20120221113043.B531910015B@ubuntu.xxxxxxxx.co.uk[/EMAIL]> [InternalId=578344] Queued mail for delivery)

Feb 21 11:30:44 FTLUBUNTU postfix/qmgr[1718]: B531910015B: removed[/FONT][/COLOR]


So the main difference is i got the email and manually it got routed to me through my Exchnage server (relay=192.168.1.3)


I tried moving the script to the user Desktop and running it via CRON from there but it failed exactly the same.


I dont use encrypted home directory.


The permissions on the script are:


Owner: user - USER
Access: Read and Write


Group: user
Access: Read Only


Others
Access: Read Only


Script is executable



Can anybody help me as to why CRON wont run this script but i can manually via the terminal please, and how i can get CRON to run it.



Thanks in advance[COLOR=black][FONT=&quot]
[/FONT][/COLOR]

---

