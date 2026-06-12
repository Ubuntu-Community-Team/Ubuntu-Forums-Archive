---
title: "Can't Open Administrative Options"
date: 2005-09-15
forum: Desktop Environments
---

### Post by schuttup on 2005-09-15
I just installed Ubuntu 5.04 and I can't open any administrative options:  Date and Time, Synaptic Packager, Add/ Remove Programs etc.  It asks for my password, but after I give it, nothing happens -- nothing at all.  Anybody know what gives?

---

### Post by agm642 on 2005-09-15
This will *probably* work:
Open a terminal and give the command "su". Type in the root password. Afterwards, enter "visudo". Under the line where it says "root ALL=(ALL) ALL", add "(your username or group) ALL=(ALL) ALL". Then save the file and you should be OK.

---

