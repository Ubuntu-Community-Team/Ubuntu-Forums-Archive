---
title: "Setting up email notifications with Nagios"
date: 2011-10-25
forum: Desktop Environments
---

### Post by thomo2710 on 2011-10-25
Hello all.

I have setup Nagios Core and am monitoring 1 of my switches as a test.

I am trying to get Nagios to email me when i pull the power out the switch but i am not having much joy.

Using Ubuntu Desktop 11.04 32bit.

I have installed mailx and postfix 

Here is what i have populated in my main.cf

 [FONT=&quot]myhostname = ASTNAGIOS
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = 192.168.1.100, mydomain.co.uk
relayhost = 192.168.1.100
mynetworks = 127.0.0.0/8, 192.168.1.0/24 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
[/FONT]
  
192.168.1.100 is the IP of my Microsoft Exchange 2010 server.
ASTNAGIOS is the name of my Linux machine running nagios - this machine is not on my domain.

I want Nagios to send mail to exchnage for it to deliver it to me.

I have powered off my switch im using to test (testing with PING only)
I have enabled notifications for the host in the web interface

It says 1 notification has been sent out and to me as defined in my contacts.cfg but i dont get anything

My mail.log shows this:

 [FONT=&quot]Oct 25 11:38:22 ASTNAGIOS postfix/pickup[2939]: 44FAF1C028E: uid=1001 from=<nagios>
[/FONT]
[FONT=&quot]Oct 25 11:38:22 [/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot] postfix/cleanup[4124]: 44FAF1C028E: message-id=<20111025103822.44FAF1C028E@[/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot]>
Oct 25 11:38:22 [/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot] postfix/qmgr[1016]: 44FAF1C028E: from=<nagios@[/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot]>, size=521, nrcpt=1 (queue active)
Oct 25 11:38:22 [/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot] postfix/local[4126]: 44FAF1C028E: to=<MYNAME@MYCOPANY.co.uk>, relay=local, delay=0.31, delays=0.17/0.08/0/0.06, dsn=5.1.1, status=bounced (unknown user: "MYNAME")
Oct 25 11:38:22 [/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot] postfix/cleanup[4124]: 7F94E1C0299: message-id=<20111025103822.7F94E1C0299@[/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot]>
Oct 25 11:38:22 [/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot] postfix/qmgr[1016]: 7F94E1C0299: from=<>, size=2176, nrcpt=1 (queue active)
Oct 25 11:38:22 [/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot] postfix/bounce[4127]: 44FAF1C028E: sender non-delivery notification: 7F94E1C0299
Oct 25 11:38:22 [/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot] postfix/qmgr[1016]: 44FAF1C028E: removed
Oct 25 11:38:22 [/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot] postfix/smtp[4129]: 7F94E1C0299: to=<nagios@[/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot]>, relay=192.168.1.3[192.168.1.3]:25, delay=0.26, delays=0.05/0.01/0.01/0.19, dsn=2.6.0, status=sent (250 2.6.0 <20111025103822.7F94E1C0299@[/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot]> [InternalId=274498] Queued mail for delivery)
Oct 25 11:38:22 [/FONT][FONT=&quot]ASTNAGIOS[/FONT][FONT=&quot] postfix/qmgr[1016]: 7F94E1C0299: removed
[/FONT]
  

What have i configured wrong or not configured?
It appears that its trying to deliver it to itself and boucing because i dont exist on the Nagios machine which is correct.

Please help.

Thankyou so much

---

