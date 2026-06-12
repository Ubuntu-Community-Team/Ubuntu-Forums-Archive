---
title: "Run script with email"
date: 2009-02-16
forum: General Help
---

### Post by shortylonglegs on 2009-02-16
I wanted to set something up that could run a script using the information contained in an email.  I would like it to be able to use information like the sender and subject, as well as the body if possible.  I've found a few websites telling how to do this for people running their own email servers.  I would like to just be able to run it for messages I get from an external pop/imap server.  Is this possible?  Sorry if my question isn't clear enough, I'm having a hard time describing.

---

### Post by HermanAB on 2009-02-16
Procmail.

Cheers,

Herman

---

### Post by Phlee on 2009-02-16
Yeap.  Fetchmail and procmail.  Great tools.  Pleanty of docs online google it;)

---

### Post by shortylonglegs on 2009-02-16
Thanks, I'll look into those

---

### Post by shortylonglegs on 2009-02-16
EDIT: Nevermind, I wasn't sending it to procmail, changed command to ```
$ fetchmail -v -m /usr/bin/procmail
``` and it seems to be working.


Ok, it looks like these are what I need, but I'm having trouble getting it all to work together.  I've been following online tutorials, and so far can get fetchmail to give me this:
```
$ fetchmail -v
fetchmail: 6.3.8 querying imap.gmail.com (protocol IMAP) at Mon 16 Feb 2009 10:52:33 PM EST: poll started
Trying to connect to 209.85.133.111/993...connected.
fetchmail: Issuer Organization: Thawte Consulting cc
fetchmail: Issuer CommonName: Thawte Premium Server CA
fetchmail: Server CommonName: imap.gmail.com
fetchmail: imap.gmail.com key fingerprint: 47:D1:87:DB:EA:7F:C6:4C:23:17:B2:DB:E3:05:D3:64
fetchmail: IMAP< * OK Gimap ready for requests from *my IP* b37if16778981ana.54
fetchmail: IMAP> A0001 CAPABILITY
fetchmail: IMAP< * CAPABILITY IMAP4rev1 UNSELECT IDLE NAMESPACE QUOTA XLIST CHILDREN XYZZY
fetchmail: IMAP< A0001 OK Thats all she wrote! b37if16778981ana.54
fetchmail: IMAP> A0002 LOGIN "my_address@gmail.com" *
fetchmail: IMAP< A0002 OK my_address@gmail.com authenticated (Success)
fetchmail: IMAP> A0003 SELECT "INBOX"
fetchmail: IMAP< * FLAGS (\Answered \Flagged \Draft \Deleted \Seen)
fetchmail: IMAP< * OK [PERMANENTFLAGS (\Answered \Flagged \Draft \Deleted \Seen \*)]
fetchmail: IMAP< * OK [UIDVALIDITY 2]
fetchmail: IMAP< * 1 EXISTS
fetchmail: IMAP< * 0 RECENT
fetchmail: IMAP< * OK [UNSEEN 1]
fetchmail: IMAP< * OK [UIDNEXT 4191]
fetchmail: IMAP< A0003 OK [READ-WRITE] INBOX selected. (Success)
fetchmail: IMAP> A0004 SEARCH UNSEEN NOT DELETED
fetchmail: IMAP< * SEARCH 1
fetchmail: IMAP< A0004 OK SEARCH completed (Success)
1 message for my_address@gmail.com at imap.gmail.com.
fetchmail: IMAP> A0005 FETCH 1 RFC822.SIZE
fetchmail: IMAP< * 1 FETCH (RFC822.SIZE 712)
fetchmail: IMAP< A0005 OK Success
fetchmail: IMAP> A0006 FETCH 1 RFC822.HEADER
fetchmail: IMAP< * 1 FETCH (RFC822.HEADER {429}
reading message my_address@gmail.com@gmail-imap.l.google.com:1 of 1 (429 header octets)
Trying to connect to 127.0.0.1/25...connection failed.
fetchmail: connection to localhost:smtp [127.0.0.1/25] failed: Connection refused.
Trying to connect to 127.0.0.1/25...connection failed.
fetchmail: connection to localhost:smtp [127.0.0.1/25] failed: Connection refused.
fetchmail: SMTP connect to localhost failed
fetchmail: IMAP> A0007 LOGOUT
fetchmail: IMAP< )
fetchmail: IMAP< A0006 OK Success
fetchmail: IMAP< * BYE LOGOUT Requested
fetchmail: IMAP< A0007 OK 73 good day (Success)
fetchmail: SMTP transaction error while fetching from my_address@gmail.com@imap.gmail.com and delivering to SMTP host localhost
fetchmail: 6.3.8 querying imap.gmail.com (protocol IMAP) at Mon 16 Feb 2009 10:52:33 PM EST: poll completed
fetchmail: Query status=10 (SMTP)
fetchmail: normal termination, status 10

```
I think the part where it fails, connecting to 127.0.0.1:25 is because I don't have anything running to accept the connection?  I think I have procmail running and configured right though.  Is there a way to tell if everything is right?

---

### Post by HermanAB on 2009-02-16
Howdy,  

Procmail is arcane, but it is very good at what it does. (I always feel very sorry for the poor sod I recommend procmail to.) However, debugging isn't its strong point.  You need to build the scripts up little by little and maybe use these tricks:
LOGFILE=/var/log/procmail.log
VERBOSE=yes
LOGABSTRACT=all

Cheers,

Herman

---

### Post by shortylonglegs on 2009-02-17
Not at all Herman, it worked perfectly once I had the mail going to it.  Thanks for the help.

---

