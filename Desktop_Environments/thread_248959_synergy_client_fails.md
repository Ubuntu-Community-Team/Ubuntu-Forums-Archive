---
title: "synergy client fails"
date: 2006-09-01
forum: Desktop Environments
---

### Post by dfeiling on 2006-09-01
Installed synergy, version 1.26, on XP as server
installed synergy, version 1.26,  on ubuntu 6.06 Dapper Drake
after configuring server, setting up host file on ubuntu
testing in debug mode 2 on the server displays following
over and over (along with indications of mouse movement)

NOTE: accepted client connection
DEBUG1:  saying hello
DEBUG2:  writef<Synergy%2i%2i>
DEBUG2:  wrote 11 bytes
NOTE:  new client disconneted

What have I done wrong?
Any advise on how to diagnose the problem?

---

### Post by dfeiling on 2006-09-04
Ran debug on client received the following:
WARNING: synergyc.cpp,265: failed to connect to server: incompatible client 1.2
Update XP Server to version 1.3.1 and it now
works as expected.

---

