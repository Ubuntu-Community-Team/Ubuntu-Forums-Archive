---
title: "Printing to SMB printer"
date: 2008-08-02
forum: Desktop Environments
---

### Post by hchristopher on 2008-08-02
Hi.  I'm trying to set up an Ubuntu 8.04 box (Gnome) to print to a network printer attached to a Windows server.  I used the default installed 'add printer' tool to add this printer, and I can print to it.

Problem: Since the printer is part of our AD domain, Ubuntu requires a domain user name and password to connect to it.  Which is okay.

However, the printing tool stores the user name and password provided at printer set up, and never updates it.  This is a problem, because this means that when that user changes his password (or leaves the system), none of the users on the Ubuntu box are able to print anymore. (This already happened twice.)

Question: Is there a way to hack the printing tools so that Ubuntu uses the credentials of the user who is currently logged in to the computer?  Or is there another package I could install that is able to do that?

My supervisors are not happy with the idea that we might need to create a "Linux-only" printing account whose password never changes.  And I think that would be kind of dumb too.

---

