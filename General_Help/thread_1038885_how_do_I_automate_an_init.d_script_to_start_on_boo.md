---
title: "how do I automate an init.d script to start on boot?"
date: 2009-01-14
forum: General Help
---

### Post by bobdobbs on 2009-01-14
Hi.

I've created my own firewall startup script.

It works when I run it from the terminal. But I would like to it to run automattically on boot.

How can I make this happen ?

---

### Post by dcstar on 2009-01-14
> **bobdobbs said:**
> Hi.

I've created my own firewall startup script.

It works when I run it from the terminal. But I would like to it to run automattically on boot.

How can I make this happen ?

/etc/rc.local

---

### Post by blackened on 2009-01-14
You can also make the script executable, then add it to System -> Preferences -> Sessions.

---

### Post by adult swim on 2009-01-14
for script named script
make sure your script is executable, chmod 755 script
put it in /etc/init.d
then run sudo update-rc.d script defaults

---

