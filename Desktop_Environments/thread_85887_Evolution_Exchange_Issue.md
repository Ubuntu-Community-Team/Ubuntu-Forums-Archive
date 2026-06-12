---
title: "Evolution Exchange Issue"
date: 2005-11-03
forum: Desktop Environments
---

### Post by ils_systems on 2005-11-03
I use evolution to connect to an exchange server.  It connects fine and I can see all my messages, but when I try to delete a message evolution hangs for about 5 min.  After that I can delete messages without any delays.   Why does it hang on the first message, but works fine after that?  I'm running breezy w/ evolution 2.4.1 and evolution-exchange 2.4.1.  Thanks for your help.

---

### Post by toadi on 2005-11-16
I have a issue to get connected to exchange. If you can shed a light how you got it to work :)

---

### Post by joshmachine on 2005-11-17
Gnome only knows.  The evolution exchange stuff is pretty broken ... hangs for extensive periods of time, sometimes crashes ... general funky. 

Did you know that a lot of exchange servers expose their folders as IMAP and have a virtual SMTP server for sending mails.  That's what I am using and let me tell you brother (or sister) soooooo much better.

Just try configuring a new mail account, set the type to IMAP and point it at your exchange server.  For me the username was just the user portion of the email (no Domain bit.)  password should be the same as exchange password.  

When you get to the sending mail bit configure the same.

Hope it works for you.  You will be much happier.

Cheers,

---

