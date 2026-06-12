---
title: "TSClient: failed to execute child process &quot;wfica&quot; when using ICA protocol"
date: 2007-09-09
forum: Desktop Environments
---

### Post by futare on 2007-09-09
Hi,

I am trying to connect to a Citrix server using the TSclient version 0.148.  The client works fine except when I try to use the ICA protocol.

The error message is as follow:
failed to execute child process "wfica" (no such file or directory)

Anybody ever come across this problem that knows how to resolve?

Many thanks,
Wikus

---

### Post by Bill Ramby on 2008-01-16
Don't know if this is still unresolved, but you can fix it by opening a terminal and typing:

sudo ln -sf /usr/lib/ICAClient/wfica /usr/bin/wfica

Of course this only brings you to the next error:

Error:3 (E_BAD_OPTION) Please refer to the documentation. Exiting.

Which I don't as yet know how to fix.

---

### Post by futare on 2008-01-17
Thanks Bill,

I will give it a try and let you know how I get on.

Cheers
Wikus

---

