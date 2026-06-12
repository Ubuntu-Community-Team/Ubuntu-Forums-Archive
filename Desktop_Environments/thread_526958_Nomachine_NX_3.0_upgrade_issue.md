---
title: "Nomachine NX 3.0 upgrade issue"
date: 2007-08-16
forum: Desktop Environments
---

### Post by nkj on 2007-08-16
I have been using Nomachine NX server 2.0 on my ubuntu and it has been working properly , when i upgraded to 3.0 it is not working. It connects properly to my NX server , passes the authentication and all that , but the moment the gnome desktop finishes loading it gives an error , i looked at the at the client log file and it says " Connection reset by Peer , Check Network Connection" , The network connection is fine as i downgraded to 2.0 and that works correctly 

I have tried removing the old version and installing a fresh copy of version 3.0 and it still does not seem to work. on the server side it gives me an error stating an error in a file with some line no , i have not been able to locate that file.

Anybody else having any issues with this ?

I have installed NX 3.0 on another machine which previously did not have any version of NX and it seems to ben working correctly on that.

---

### Post by DLGandalf on 2007-10-15
same issue, never found an solution to it either.

---

### Post by nkj on 2007-10-15
I figured a workaround , the problem only occurs if i have beryl or compiz set to startup at session startup so removing that fixes the problem.

---

### Post by DLGandalf on 2007-10-23
this wasn't the case in my setup

---

