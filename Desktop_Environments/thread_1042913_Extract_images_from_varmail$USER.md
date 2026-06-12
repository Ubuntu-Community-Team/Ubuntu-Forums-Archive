---
title: "Extract images from /var/mail/$USER"
date: 2009-01-18
forum: Desktop Environments
---

### Post by abetterlie on 2009-01-18
Hey guys, I searched far and wide for a solution for this, but could not find one. 
I have an 800mb file in /var/mail that presumably contains all the mail that I have recieved/sent. Does anyone know how I would go about pulling all of the images that were attached to messages from this file? 

Anyone have any ideas?
Thanks,
matt.

---

### Post by abetterlie on 2009-01-18
I understand that there is munpack, but I really don't know how to use it for more than one message at a time, or where i would start with iterating it over a ton of messages in one file.

---

### Post by apmcd47 on 2009-01-18
> **abetterlie said:**
> I understand that there is munpack, but I really don't know how to use it for more than one message at a time, or where i would start with iterating it over a ton of messages in one file.

/var/mail/$USER is probably an mbox-format mail folder.

Look for a program called git-mailsplit (git package?) I don't know if it exists as an Ubuntu package. With git-mailsplit you will be able to split am mbox-format mail folder into individual mail files, one per message. You will probably be able to use munpack on them.

Andrew

---

### Post by abetterlie on 2009-01-23
Thanks, I'll give it a shot and report back. 

> **apmcd47 said:**
> /var/mail/$USER is probably an mbox-format mail folder.

Look for a program called git-mailsplit (git package?) I don't know if it exists as an Ubuntu package. With git-mailsplit you will be able to split am mbox-format mail folder into individual mail files, one per message. You will probably be able to use munpack on them.

Andrew

---

