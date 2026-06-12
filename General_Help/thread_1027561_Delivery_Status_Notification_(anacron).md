---
title: "Delivery Status Notification (anacron)"
date: 2009-01-01
forum: General Help
---

### Post by richbl on 2009-01-01
Hello all,

For the past few weeks (months?), I've been receiving failure email messages that originate from my Ubuntu (Ibex 8.10) box. I can't seem to identify what is causing this problem.

The originating email subject is: **Anacron job 'cron.daily' on ubuntu**

The content of the email message is as follows:

```
This is an automatically generated Delivery Status Notification

THIS IS A WARNING MESSAGE ONLY.

YOU DO NOT NEED TO RESEND YOUR MESSAGE.

Delivery to the following recipient has been delayed:

    root@192.xxx.xxx.xxx

Message will be retried for 2 more day(s)
```

Any ideas on how to track down issues related to this kind of message?

Thanks much.

---

### Post by ibuclaw on 2009-01-01
Do you know what mail client you have installed? If any?

Regards
Iain

---

### Post by richbl on 2009-01-01
> **tinivole said:**
> Do you know what mail client you have installed? If any?

Regards
Iain

On the machine that originated the email (called ubuntu), no mail client installed (beyond any default install).

The mail gets forwarded to my local mail server (called kurobox) running exim4 under Debian. From there, the notification message is sent to my gmail account.

The trace on the email suggests an issue with anacron cron.daily on ubuntu. **Why would anacron be attempting to send out an email?**

Here's a set of log files (on ubuntu, the originating machine):

A view of /var/log/mail.err shows a series of:

```
Dec 28 07:59:39 ubuntu nullmailer[17632]: smtp: Failed: Connect failed
Dec 28 07:59:39 ubuntu nullmailer[5477]: Sending failed:  Connection failed
```

A view of /var/log/mail.info shows a series of related messages:

```
Dec 29 08:24:02 ubuntu nullmailer[5455]: Trigger pulled.
Dec 29 08:24:02 ubuntu nullmailer[5455]: Rescanning queue.
Dec 29 08:24:02 ubuntu nullmailer[5455]: Starting delivery: protocol: smtp host: 192.xxx.xxx.113 file: 1230567842.11228
Dec 29 08:24:04 ubuntu nullmailer[11229]: smtp: Failed: Connect failed
Dec 29 08:24:04 ubuntu nullmailer[5455]: Sending failed:  Connection failed
Dec 29 08:24:04 ubuntu nullmailer[5455]: Starting delivery: protocol: smtp host: 192.xxx.xxx.113 file: 1230479909.17413
Dec 29 08:24:07 ubuntu nullmailer[11230]: smtp: Failed: Connect failed
Dec 29 08:24:07 ubuntu nullmailer[5455]: Sending failed:  Connection failed
Dec 29 08:24:07 ubuntu nullmailer[5455]: Starting delivery: protocol: smtp host: 192.xxx.xxx.113 file: 1230307108.8889
Dec 29 08:24:10 ubuntu nullmailer[11231]: smtp: Failed: Connect failed
Dec 29 08:24:10 ubuntu nullmailer[5455]: Sending failed:  Connection failed
Dec 29 08:24:10 ubuntu nullmailer[5455]: Starting delivery: protocol: smtp host: 192.xxx.xxx.113 file: 1230393731.26550
Dec 29 08:24:13 ubuntu nullmailer[11232]: smtp: Failed: Connect failed
Dec 29 08:24:13 ubuntu nullmailer[5455]: Sending failed:  Connection failed
Dec 29 08:24:13 ubuntu nullmailer[5455]: Delivery complete, 4 message(s) remain.
```

A view of /var/log/mail.warn shows:

```
Dec 28 07:59:39 ubuntu nullmailer[17632]: smtp: Failed: Connect failed
Dec 28 07:59:39 ubuntu nullmailer[5477]: Sending failed:  Connection failed
Dec 28 07:59:42 ubuntu nullmailer[17633]: smtp: Failed: Connect failed
Dec 28 07:59:42 ubuntu nullmailer[5477]: Sending failed:  Connection failed
Dec 28 07:59:45 ubuntu nullmailer[17634]: smtp: Failed: Connect failed
Dec 28 07:59:45 ubuntu nullmailer[5477]: Sending failed:  Connection failed
Dec 28 08:00:48 ubuntu nullmailer[17636]: smtp: Failed: Connect failed
Dec 28 08:00:48 ubuntu nullmailer[5477]: Sending failed:  Connection failed
Dec 28 08:00:51 ubuntu nullmailer[17637]: smtp: Failed: Connect failed
Dec 28 08:00:51 ubuntu nullmailer[5477]: Sending failed:  Connection failed
Dec 28 08:00:54 ubuntu nullmailer[17638]: smtp: Failed: Connect failed
```

So, clearly something is amiss.

Here's a scrubbed copy of the full email received:
                                                                                                                                                                                                                                                               
```
Delivered-To: someone@gmail.com
Received: by xx.xxx.xx.xx with SMTP id xxx;
        Thu, 1 Jan 2009 08:49:47 -0800 (PST)
Received: by xx.xxx.xx.xx with SMTP id xxx;
        Thu, 01 Jan 2009 08:49:45 -0800 (PST)
Return-Path: <>
Received: by xx.xxx.xx.xx with SMTP id xxx;
        Thu, 01 Jan 2009 08:49:45 -0800 (PST)
Message-ID: <xxx@googlemail.com>
From: Mail Delivery Subsystem <mailer-daemon@googlemail.com>
To: someone@gmail.com
Subject: Delivery Status Notification (Delay)
Date: Thu, 01 Jan 2009 08:49:45 -0800 (PST)

This is an automatically generated Delivery Status Notification

THIS IS A WARNING MESSAGE ONLY.

YOU DO NOT NEED TO RESEND YOUR MESSAGE.

Delivery to the following recipient has been delayed:

     root@192.xxx.xxx.113

Message will be retried for 2 more day(s)

Technical details of temporary failure: 
The recipient server did not accept our requests to connect. Learn more at http://mail.google.com/support/bin/answer.py?answer=7720 
[192.xxx.xxx.113 (1): Connection timed out]

   ----- Message header follows -----

Received: by xx.xxx.xx.xx with SMTP id xxx;
        Wed, 31 Dec 2008 08:10:22 -0800 (PST)
Return-Path: <someone@gmail.com>
Received: from KURO-BOX (pool-xx-xxx-xx-xx.dsl.xxx.net [xx.xxx.xx.xx])
        by mx.google.com with ESMTPS id xxx
        (version=TLSv1/SSLv3 cipher=RC4-MD5);
        Wed, 31 Dec 2008 08:10:20 -0800 (PST)
Received: from ubuntu ([192.xxx.xxx.111] helo=192.xxx.xxx.113)
	by KURO-BOX with smtp (Exim 4.63)
	(envelope-from <root@192.xxx.xxx.113>)
	id xxx
	for root@192.xxx.xxx.113; Wed, 31 Dec 2008 08:09:58 -0800
Received: (nullmailer pid 28589 invoked by uid 0);
	Wed, 31 Dec 2008 16:09:58 -0000
To: root@192.xxx.xxx.113
Subject: Anacron job 'cron.daily' on ubuntu
Date: Wed, 31 Dec 2008 08:09:58 -0800
Message-Id: <xxx.nullmailer@192.xxx.xxx.113>
From: Anacron <someone@gmail.com>

   ----- Message body suppressed -----
```

---

