---
title: "[SOLVED] sending terminal messages"
date: 2008-12-15
forum: General Help
---

### Post by jspolen on 2008-12-15
Hi I was wondering if it's possible to send messages via the terminal to other users logged into my server? And if possible how to?

---

### Post by davec64 on 2008-12-15
If memory serves me right:

```
smbclient -M HOSTNAME
```

It will then connect to the client and prompt for your message.

---

### Post by jspolen on 2008-12-15
I'm currently trying to get a hold on the to program. *to user message* but all I get is Access to's (user) terminal denied.

Sending messages to myself is no problem.

---

### Post by geirha on 2008-12-15
You can use the write an wall commands. write sends a message to a particular user, while wall writes a message to all users. 
```
write *username*
```
Type in the message and hit Ctlr+D or Ctrl+C to exit and send.

If you get a message saying "write: *username* has messages disabled", then that user does not want to recieve messages. Users can toggle whether they want to recieve such messages or not by running "mesg y" and "mesg n".

The root user can send walls and writes to anyone no matter if the user wants to recieve them or not.

---

