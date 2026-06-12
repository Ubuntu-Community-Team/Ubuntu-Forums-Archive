---
title: "Disks Manager crash"
date: 2005-10-26
forum: Desktop Environments
---

### Post by mannheim on 2005-10-26
Hi,

I have been trying to use the utility Systems->Administration->Disks (the Disk Manager). However, the application crashes: it begins to start up, its window appears, and  then I get the dialog "The application disks-admin has unexpectedly quit".

This happens on both my machines (two independent installations of Breezy on Dell desktops).

Has anyone else experience this problem, or better yet, have a suggested fix? (For example, can I reinstall the disks manager without reinstalling Breezy?) 

My setup is otherwise stable and running well. (And no, I suppose I don't **really** need the disks manager app!)

Peter

---

### Post by BORTKOMMEN on 2005-12-16
I have the same problem in my newly installed Breezy. i cannot open the applicaton and when I tried in the console I got this;

~$ gksudo disks-admin
(disks-admin:12707): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.
Entity: line 39: parser error : error parsing attribute name
      <point><mount\040point></point>
                   ^
Entity: line 39: parser error : attributes construct error
      <point><mount\040point></point>
                   ^
Entity: line 39: parser error : Couldn't find end of Start Tag mount line 39
      <point><mount\040point></point>
                   ^
Entity: line 101: parser error : error parsing attribute name
      <point><mount\040point></point>
                   ^
Entity: line 101: parser error : attributes construct error
      <point><mount\040point></point>
                   ^
Entity: line 101: parser error : Couldn't find end of Start Tag mount line 101
      <point><mount\040point></point>
                   ^

If this is a bug, how can I report it. What I have seen in this forum many have problems with this application.

---

### Post by BORTKOMMEN on 2005-12-21
It is fixed now, my fstab had corrupt entries.

---

