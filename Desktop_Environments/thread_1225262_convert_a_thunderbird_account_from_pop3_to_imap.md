---
title: "convert a thunderbird account from pop3 to imap"
date: 2009-07-28
forum: Desktop Environments
---

### Post by koba101 on 2009-07-28
HI,

does anybody know how to convert a pop3 account to imap in thunderbird...i have a gmail account that's currently on pop3 and it want it to be on imap

challenging part would be to keep the messages i have already....

---

### Post by silis024 on 2009-07-28
Go to Edit > Account Settings > Server Settings.  In the "Server Name" bar replace pop with imap.

/VG

---

### Post by koba101 on 2009-07-29
it'll still say pop3 as type

---

### Post by lavezarez on 2009-07-29
if you deactivate your pop gmail account like this:
1) uncheck the Check for new messages at startup
2) uncheck the Check for new message every XX minutes
3) change the server name to something like my-archives.xxx, and 
4) change the user name to [email]user@my-archives.xxx[/email]

then 
A) login your gmail account and enable IMAP

B) create a new account for your imap gmail like:
1) server type = IMAP
2) server name = imap.gmail.com, port = 993
3) user name = your gmail email address
4) secure connection = SSL

C) modify your SMTP to be:
1) server = smtp.gmail.com
2) port = 587
3) secure connection = TLS

that should work.

Then simply move your emails from the old POP to the new IMAP before removing the old account.

---

