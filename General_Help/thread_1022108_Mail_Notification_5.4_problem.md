---
title: "Mail Notification 5.4 problem"
date: 2008-12-26
forum: General Help
---

### Post by Wanas on 2008-12-26
I have just installed Mail Notification 5.4 but when I added my hotmail and yahoo accounts I have this messages:
1- Hotmail (unhandled windows live hotmail mailbox (cannot execute "GetLive": Failed to execute child process "GetLive" (No such file or directory))
2- Yahoo (unhandled Yahoo mailbox (cannot execute "fetchyahoo": Failed to execute child process "fetchyahoo" (No such file or directory))
See the attachment.png

So what I gonna do to fix this?

---

### Post by Wanas on 2008-12-29
no one have the same problem :(

---

### Post by katana2k on 2009-01-01
im having the same issues

---

### Post by musugashi on 2009-03-06
For the Yahoo mail issue, you need to load the FetchYahoo libraries.

sudo apt-get install fetchyahoo

For other library issues see [http://www.linux.com/feature/153635?theme=print](http://www.linux.com/feature/153635?theme=print)

;)

---

### Post by balcis on 2009-03-16
so the fetchyahoo thing is actually a dependencie?! why seem not like. thank you for answer.

---

