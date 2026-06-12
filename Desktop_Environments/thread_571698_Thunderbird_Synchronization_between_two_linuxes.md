---
title: "Thunderbird Synchronization between two linuxes?"
date: 2007-10-09
forum: Desktop Environments
---

### Post by CyberAngel on 2007-10-09
Is that possible?

I also found an old thread that has no answer [here]("http://ubuntuforums.org/showthread.php?t=236474").

I want to do exactly what this guy says but on two different machines (Desktop and laptop).

I want to be able to receive my e-mails on Desktop and when I open my laptop to synchronize it and vice versa.
If I am out with my laptop to be able to get my e-mails on it, and when I return home to synchronize it again with the desktop.

Is that possible?
Please don`t answer just "Yes" but throw your ideas here :)

Thanks!

---

### Post by rsambuca on 2007-10-09
Will it work if you set both Thunderbirds to leave the messages on the server?

---

### Post by CyberAngel on 2007-10-09
If I am always leaving the e-mails on the server won`t they be downloaded again and again?

---

### Post by rsambuca on 2007-10-09
I have no idea!  Why don't you send yourself an email and test it out.  I had assumed that it wouldn't download an email if it was already on your machine, but that is a guess.  You would have to occasionally delete the ones on the server, though.

---

### Post by rsambuca on 2007-10-09
OK, I just did one test for you.  I set my TB to leave the messages on the server.  After it retrieved the mail, I closed TB and it won't retrieve it again.  I don't know how it remembers, but I tried moving it from the TB inbox, and it still left it, and after deleting it from TB, it still leaves it on the server.

---

### Post by pbcartwright on 2007-10-09
you probably want IMAP folders.. I think that would be your best bet.
see wiki-IMAP:
Multiple clients simultaneously connected to the same mailbox

The POP3 protocol requires the currently connected client to be the only client connected to the mailbox. In contrast, the IMAP protocol specifically allows simultaneous access by multiple clients and provides mechanisms for clients to detect changes made to the mailbox by other, concurrently connected, clients.

[http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol#Multiple_clients_simultaneously_connected_to_the_same_mailbox](http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol#Multiple_clients_simultaneously_connected_to_the_same_mailbox)

---

### Post by CyberAngel on 2007-10-10
> **rsambuca said:**
> OK, I just did one test for you.  I set my TB to leave the messages on the server.  After it retrieved the mail, I closed TB and it won't retrieve it again.  I don't know how it remembers, but I tried moving it from the TB inbox, and it still left it, and after deleting it from TB, it still leaves it on the server.

Probably it`s a setting on the server that remembers which e-mail will resend to the client...
But I want all the e-mail to both clients..

---

### Post by CyberAngel on 2007-10-10
> **pbcartwright said:**
> you probably want IMAP folders.. I think that would be your best bet.
see wiki-IMAP:
Multiple clients simultaneously connected to the same mailbox

The POP3 protocol requires the currently connected client to be the only client connected to the mailbox. In contrast, the IMAP protocol specifically allows simultaneous access by multiple clients and provides mechanisms for clients to detect changes made to the mailbox by other, concurrently connected, clients.

[http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol#Multiple_clients_simultaneously_connected_to_the_same_mailbox](http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol#Multiple_clients_simultaneously_connected_to_the_same_mailbox)

That would be a good solution but I have some gmail accounts and as google says [here]("http://mail.google.com/support/bin/answer.py?hl=en&answer=10339") they do not support imap at the moment.

---

### Post by Gabix on 2008-04-17
I want to do even more!
I'd like to have an exact replica of the two thunderbirds in two different op systems (Ub an XP) And by replica I mean all the folders, tasks, contacts, and of course configs.

Is that possible?

---

### Post by Gabix on 2008-04-17
I think I found an answer to my own question here:
[http://kb.mozillazine.org/Synchronizing_mail_on_two_computers_(Thunderbird](http://kb.mozillazine.org/Synchronizing_mail_on_two_computers_(Thunderbird))

Anyway, I have to test It... I'll report my results...

---

