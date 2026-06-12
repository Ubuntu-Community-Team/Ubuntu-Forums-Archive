---
title: "Error using Synaptic Package Manager"
date: 2009-04-26
forum: General Help
---

### Post by erasmusp on 2009-04-26
Trying to install a game (gweled) using the Synaptic Package Manager, I get the following error after selecting and okay'ing the two packages it needs to install:

"Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)"

Any idea why this would be?

Regards,
Phill

---

### Post by erasmusp on 2009-04-26
I forgot to mention this is using Ubuntu 8.10.....

---

### Post by plucky on 2009-04-26
Open Software Sources and try another server.I am getting "Failed to connect" with that server.


If that doesn't work,post the output of ```
cat /etc/apt/sources.list
```

Good Luck

---

### Post by erasmusp on 2009-04-26
Thanks! :) Switched to the UK server and it works!

Cheers,
Phill

---

