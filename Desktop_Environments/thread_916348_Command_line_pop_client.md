---
title: "Command line pop client?"
date: 2008-09-10
forum: Desktop Environments
---

### Post by solexious on 2008-09-10
Hia,

I need a command line mail client that will get emails, put any attachments into a folder with a text file of the message body and remove the email.

Any suggestions?

Sol

---

### Post by solitaire on 2008-09-10
is pine still around? can't that access pop3 accounts?

look here for some reviews.
[http://www.linux.com/feature/58720](http://www.linux.com/feature/58720)

---

### Post by ajmorris on 2008-09-10
> **solexious said:**
> Hia,

I need a command line mail client that will get emails, put any attachments into a folder with a text file of the message body and remove the email.

Any suggestions?

Sol

Hi there,
you could try using 'pine'

EDIT: solitaire beat me to it :P

AJ

---

### Post by Oldsoldier2003 on 2008-09-11
Pine isn't in the Ubuntu repos because of funky licensing. try alpine, which a a clone of pine. In fact thats why we have nano instead of pico (pico was part of the pine package).
```
 apt-cache policy alpine
alpine:
  Installed: (none)
  Candidate: 1.0+dfsg-3
  Version table:
     1.0+dfsg-3 0
        500 http://mirror.anl.gov hardy/universe Packages

```

---

### Post by solexious on 2008-09-11
This seems to be more than I need.

I need a very simple client that will pull from a external pop3 account, and put the atachment in a folder. And send email back to the same server. Haviing to setup sendmail or postfix seems alot to do this...?

Thank you for the help so far

Sol

---

### Post by vishzilla on 2008-09-11
Mutt is another option > Description: text-based mailreader supporting MIME, GPG, PGP and threading
 Mutt is a sophisticated text-based Mail User Agent. Some highlights:
 .
  * MIME support (including RFC1522 encoding/decoding of 8-bit message
    headers and UTF-8 support).
  * PGP/MIME support (RFC 2015).
  * Advanced IMAP client supporting SSL encryption and SASL authentication.
  * POP3 support.
  * ESMTP support.
  * Message threading (both strict and non-strict).
  * Keybindings are configurable, default keybindings are much like ELM;
    Mush and PINE-like ones are provided as examples.
  * Handles MMDF, MH and Maildir in addition to regular mbox format.
  * Messages may be (indefinitely) postponed.
  * Colour support.
  * Highly configurable through easy but powerful rc file.
Homepage: [http://www.mutt.org/](http://www.mutt.org/)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: mail-server

---

### Post by solexious on 2008-09-11
Again with mutt you need sendmail and others setup, I was hoping for one client i can put my pop3 account details in, like the ease of setup like thundberird but commandline only...

Thanks Sol

---

### Post by mali2297 on 2008-09-11
(Al)pine is an interactive text-mode email client. I interpret the OP:s request as wanting a non-interactive program to process the mail. 

I haven't tried this myself, but I think a combination of fetchmail and procmail can do what you want. This [tutorial]("http://www.ioncannon.net/system-administration/97/using-fetchmail-and-procmail-for-maildir-style-storage-from-a-pop3-account/") may get you started. 

The tutorial doesn't tell you how to extract attachments, but I think this can be done with procmail.

---

### Post by solexious on 2008-09-11
Checking that link now, will remember to specify non-interactive in future questions.

Sol

---

### Post by solexious on 2008-09-11
Not found the right thing yet, found some thing for sending, nails, now im looking for a resiving version, where i can make one command i.e.

mailProgram --reciveMail --outputText --pop mail.***.com message.txt

If that makes it any more clear.

Sol

---

### Post by panhandle on 2008-09-13
What about Mail?

I think it can be used in conjunction with exim.

A simple program that will allow you to send email from the command line.

---

### Post by vranga on 2009-07-26
Sol,

Did you find the solution to this? I need exactly the same thing. In fact I don't even need incoming mail. I just need to be able to send a mail out to gmail automatically from a shell script.

-Vishy

---

