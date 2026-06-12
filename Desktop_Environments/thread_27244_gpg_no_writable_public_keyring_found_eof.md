---
title: "gpg: no writable public keyring found: eof"
date: 2005-04-15
forum: Desktop Environments
---

### Post by felixdzerzhinsky on 2005-04-15
When I try to : **gpg --gen-key**   I get the following error:

[B]ygpg: no writable public keyring found: eof
Key generation failed: eof[/B]

I've googled but can't find an answer.

Anybody know why?

---

### Post by x001 on 2005-05-05
check the permissions on .gnupg folder in your home directory.

---

### Post by Tiger27 on 2008-01-17
> **felixdzerzhinsky said:**
> When I try to : **gpg --gen-key**   I get the following error:

[B]ygpg: no writable public keyring found: eof
Key generation failed: eof[/B]

I've googled but can't find an answer.

Anybody know why?


You need to be logged in as root to generate the key.

open your terminal 

sudo su

gpg --gen-key

the rest is self explanatory

---

### Post by pretard on 2008-02-03
Tiger27

Thanks for the update, running: sudo su worked and I was able to create a key.  Perhaps this is something that could be added to Kgpg or Gnomegpg when it creates keys.

---

