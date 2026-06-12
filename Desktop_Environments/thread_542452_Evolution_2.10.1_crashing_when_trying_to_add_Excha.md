---
title: "Evolution 2.10.1 crashing when trying to add Exchange acct"
date: 2007-09-04
forum: Desktop Environments
---

### Post by mjthor on 2007-09-04
I'm not sure what's going on here.  I've looked at a few sites relating to Evolution and Exchange servers, but nothing has worked.  It crashes immediately after I enter my password on the "Authenticate" popup window.

This is what the terminal output is:
```
(evolution-2.10:10921): libsoup-CRITICAL **: soup_message_set_request: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution-2.10:10921): libsoup-CRITICAL **: soup_message_set_flags: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution-2.10:10921): libsoup-CRITICAL **: soup_session_send_message: assertion `SOUP_IS_MESSAGE (msg)' failed
Segmentation fault (core dumped)

```

Here's the tutorial of how to set up the server I'm trying to connect to with Red Hat and Evolution 2: [http://helpdesk.its.uiowa.edu/exchange/evolution.htm]("http://helpdesk.its.uiowa.edu/exchange/evolution.htm")
I'm not sure if that will be any help, but it's the only other information I can really give.

For my username I used the format jdoe@ui and for OWA I used [https://email.uiowa.edu/exchange](https://email.uiowa.edu/exchange)

If anyone can help, please do!  This is extremely frustrating!  Thanks!

---

### Post by AmaranthineNight on 2007-09-04
I'm experiencing the same error. After extensive googling on the subject, I cannot find any solutions. Any help would be greatly appreciated.

---

### Post by al123 on 2007-09-05
Me too 

[Edit]  as version is 2.10

Error message is
CalDAV Eplugin starting up ...

(evolution-2.10:21669): libsoup-CRITICAL **: soup_message_set_request: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution-2.10:21669): libsoup-CRITICAL **: soup_message_set_flags: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution-2.10:21669): libsoup-CRITICAL **: soup_session_send_message: assertion `SOUP_IS_MESSAGE (msg)' failed
Segmentation fault (core dumped)
[/edit]

I have two systems that were working fine (accessed exchange no problem) but now I cannot even start evolution on either of them.

Don't think I upgraded my Evolution recently on either machine, but work has just upgraded their version of Exchange, and that was the day I started having problems (version now operating unknown).  

I'm just wondering whether some Exchange versions break access by Evolution?

Any help/suggestions appreciated as the only fixes I've found are for similar problems, but about a year ago and I don't think they're the cause of my current issue.

TIA

Andrew

---

### Post by freelsjd on 2007-09-06
Heh !!  I get this exact same error message starting this afternoon at about 4pm.  Is it a Microsoft conspiracy ?  Could be some subtle changes in the exchange server going on that is causing this !

---

### Post by AmaranthineNight on 2007-09-06
I think it's probably a problem with Exchange Server 2007, which is the version of exchange my school is using.

I am working around this problem by using Thunderbird with IMAP for right now, so at least I can get my mail. To configure thunderbird for IMAP, if it's enabled, you use the OWA URL as your incoming and outgoing servers. My school requires you use SSL as well, so make sure you know if that's something you need to enable.

I still haven't figured out how to configure Thunderbird to use my Global Address List though....

Anyway, I haven't found anything on making evolution work, it still crashes.

---

### Post by mjthor on 2007-09-09
Yeah.  Luckily my school has a fully-functional webmail client, otherwise I'd be S.O.L.

It'd still be nice to have Evolution work, but at this point I'm ready to concede defeat.  I don't have the time to mess around with code and figure out how to get Evolution working.

---

### Post by pagingmrherman on 2007-10-02
I've got the same problem too.  It happened just after we installed SQL 2005 on our exchange2k3 server.  We had to update the IIS cert and after that evolution started core dumping on all our PCs.  I filed a gnome bug report for evolution but haven't heard anything..

---

### Post by snickers295 on 2007-10-02
me too. 
i just got mozilla thunderbird for a replacement.
its much better then evolution and its easy to get in the terminal and type:
```
sudo apt-get install mozilla-thunderbird
```Good Luck

---

### Post by pagingmrherman on 2007-12-17
unfortunately, that only works if you have imap or pop3 enabled on your exchange server.

---

### Post by Dreamer Zero on 2007-12-19
i am having the same issue, working with a 2007 exchange server, this is the last thing i need to work with Gusty then my boss will let me format my Vista machine.

---

