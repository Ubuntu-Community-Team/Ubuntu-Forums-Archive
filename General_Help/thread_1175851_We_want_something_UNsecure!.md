---
title: "We want something UNsecure!"
date: 2009-06-01
forum: General Help
---

### Post by Watership on 2009-06-01
Hey Genii, you've always been a big help, so here goes another question.
Our research lab is learning how to work with IPtables in Ubuntu, and to monitor our progress, we want to see if we can edit packets as they go through. Fair enough... we just need to send some packets through with words that we can recognize, search for, and replace. But that means that your normal 'secure' protocols (scp, ssh, sftp) are no good... we want to see what it is we're transmitting.

Tried telnet, but the connection kept being refused, no idea why.
Tried ftp, same story.

Anybody know another protocol we could use which does not encode its packets, or have suggestions about why ftp and telnet aren't doing the trick? Thanks a million!

---

### Post by Chronon on 2009-06-01
Many hosts don't allow unencrypted connections these days.  I can only log into my school's unix system with sftp or ssh rather than ftp or telnet.

---

### Post by Watership on 2009-06-01
> **Chronon said:**
> Many hosts don't allow unencrypted connections these days.  I can only log into my school's unix system with sftp or ssh rather than ftp or telnet.

We've got complete control over our own tiny network here, though. There must be a way to allow all that dirty connection goodness.

---

### Post by Mirge on 2009-06-01
> **Watership said:**
> We've got complete control over our own tiny network here, though. There must be a way to allow all that dirty connection goodness.

Not constructive at all, but "dirty connection goodness" made me laugh lol

---

### Post by jonobr on 2009-06-01
hello


By default, telnet and ftp programs/daemons are not on a ubuntu system
You have telnet and ftp clients, however, nothing will answer the telnet or ftp request to your ubuntu server.
You would need to install telnet from synaptic
search for telnetd
For FTP theres a few programs out there.
The simplest would be vsftp

---

