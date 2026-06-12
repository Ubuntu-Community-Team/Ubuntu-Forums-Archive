---
title: "Postfix issues with PHP mail()"
date: 2006-06-13
forum: Desktop Environments
---

### Post by rem on 2006-06-13
Hello all,

Is it just me or there are some Postfix issues in Dapper that weren't there in Breezy? I'm a PHP developer and can't send PHP emails on my development local server (Apache2 / MySQL5 / PHP5). In Breezy everything went just fine but not now. I searched the forums and the old posts as well as google it out but don't seem to be able to find a fix... I'm not such a proficient console file configuration guy and don't quite understand the inside outs of Postix also... Just using it as default installed and heard it suposed to work. Here's an excerpt of my mail log:

```
Jun 13 15:42:03 localhost postfix/pickup[10888]: 445FD9E8EF: uid=33 from=<www-data>
Jun 13 15:42:04 localhost postfix/cleanup[10898]: 445FD9E8EF: message-id=<20060613124203.445FD9E8EF@localhost>
Jun 13 15:42:04 localhost postfix/qmgr[10889]: 445FD9E8EF: from=<www-data@localhost>, size=334, nrcpt=1 (queue active)
Jun 13 15:42:07 localhost postfix/smtp[10901]: 445FD9E8EF: to=<test1@eclipsedesign.net>, relay=eclipsedesign.net[194.117.236.18], delay=4, status=bounced (host eclipsedesign.net[194.117.236.18] said: 550-Verification failed for <www-data@localhost> 550-unrouteable mail domain "localhost" 550 Sender verify failed (in reply to RCPT TO command))
Jun 13 15:42:07 localhost postfix/cleanup[10898]: 142009E8F0: message-id=<20060613124207.142009E8F0@localhost>
Jun 13 15:42:07 localhost postfix/qmgr[10889]: 142009E8F0: from=<>, size=2258, nrcpt=1 (queue active)
Jun 13 15:42:07 localhost postfix/qmgr[10889]: 445FD9E8EF: removed
Jun 13 15:42:07 localhost postfix/local[10904]: 142009E8F0: to=<rem@localhost>, orig_to=<www-data@localhost>, relay=local, delay=0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jun 13 15:42:07 localhost postfix/qmgr[10889]: 142009E8F0: removed
```

As I can see, My SMTP server (rely host, eclipsedesign.net) needs authentication, but how can I set that in /etc/postfix/main.cf file???
Any help or suggestion is greately appreciated. Many, many thanks and my best to all of yous!

---

### Post by rem on 2006-06-13
I think I'll better take this to the server talk forum as I now realize I should been done from the first place... sorry for the mess...

---

