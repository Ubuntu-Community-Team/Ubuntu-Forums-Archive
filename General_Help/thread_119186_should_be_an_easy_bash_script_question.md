---
title: "should be an easy bash script question"
date: 2006-01-18
forum: General Help
---

### Post by 0MG on 2006-01-18
I have a little script I wrote that worked like a champ in Mepis. Does not run in ubuntu.

I get the error: 

bash: /usr/bin/ifa: /bin/bash^M: bad interpreter: No such file or directory

Here's the first couple lines:

```
#!/bin/bash
# Bring up an interface, choose SSID, pull dhcp, add alias, login to server
read -p "Interface? " If ;

```

Any insight for a script noob?

tia

---

### Post by 0MG on 2006-01-18
I got it - needed a package called flip to convert the file.

Works now.:D

---

