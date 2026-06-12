---
title: "Evolution vs kmail"
date: 2006-01-10
forum: Desktop Environments
---

### Post by GrumpyBob on 2006-01-10
I have been thinking about switching from Evolution to Kmail.  I have never managed to get Evolution to work with my work IMAP server.  I configured fetchmail to bring down emails from the IMAP server to a local spool folder, and configured an SMTP server for outgoing mail.  OK so far, except Evolution seems quite fragile, and appears to cause system hangs (or more probably stalls, where the PC doesn't responde for quite some time).

I have installed Kontakt, with Kmail.  With Kmail, I can access the IMAP server using the same settings I have tried (unsuccessfully) with Evolution, but cannot persuade it to send email via the same SMTP details as work for Evolution.  

This seems somewhat bizarre to me, and I am wondering if there is some missing component, as I am not running KDE on this laptop.

Robert

---

### Post by lorenco on 2006-01-10
I am using KMail with IMAP (SSL) No problem
I have KDE 3.5 (But this worked on 3.4 as well.) 

You might want to try  Kontact, KDE personal information manager that ships as standard with Kubuntu.

I have Mail setup via 2 SMTP servers (TLS & Normal) and it works great.  Any reason you do not want KDE ?

What settings do you have for SMTP ? Do you need Authentication? Open relay?  A little more info should help... ;) 

Cheers

---

### Post by GrumpyBob on 2006-01-10
Your points in order...
I too have no problems reading email from the IMAP server with Kmail.
I have Kontact installed now.
Cannot send email from Kmail, even using same settings as used with Evolution.
Re KDE, I don't want to get into a KDE vs Gnome thing, I just prefer Gnome!
Like I say, I have used the same settings for SMTP as work for Evolution.  mailserver, account, authentication, etc all the same.  But doesn't work.

I have set the correct mailserver name, correct username, correct password.  I have checked "server requires authentication" and given it correct details - all in fact the same as I use in Evolution.  This is why I asked if there are other packages I should install.

Robert

---

### Post by nocturn on 2006-01-10
[QUOTE=GrumpyBob]I have been thinking about switching from Evolution to Kmail.  I have never managed to get Evolution to work with my work IMAP server.  I configured fetchmail to bring down emails from the IMAP server to a local spool folder, and configured an SMTP server for outgoing mail.  OK so far, except Evolution seems quite fragile, and appears to cause system hangs (or more probably stalls, where the PC doesn't responde for quite some time).
Robert[/QUOTE]

That is strange, what kind of error do you get on the Evolution Imap?  Also, is your work mail server Exchange?

I've been using Evolution since 0.9 and never had any issues with it.  I prefer it to Kmail for a lot of reasons, but PGP(Mime) support was the biggest one (which was broken for along time in Kmail).  Also, Evo can handle really big mail archives very fast.

I have never experienced stalls, when it stalls, can you run top in a terminal to see what is happening?

---

### Post by GrumpyBob on 2006-01-10
I will try this (running top) next time it seems to hang/stall. 

In fact I can report, with many blushes and much embarrassment, that another bout of random option changes seems to have made a successful IMAP connection.  (Honestly, I *have* made many unsuccessful attempts! - over the last three months!)

Robert

---

