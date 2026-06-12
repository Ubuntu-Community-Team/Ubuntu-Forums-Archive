---
title: "Upadte Mgr without Password?"
date: 2011-10-19
forum: Desktop Environments
---

### Post by scpatl4now on 2011-10-19
This is the second time I have run the update manager that it didn't ask me for upgraded privileges (a password).  Is this supposed to be that way?

---

### Post by Frogs Hair on 2011-10-19
You should be able to check for updates , but not install them without a password .

---

### Post by haqking on 2011-10-19
> **Frogs Hair said:**
> You should be able to check for updates , but not install them without a password .

+1

also it depends on if you did within the specified time frame of last using admin privelege

---

### Post by Larkspur on 2011-10-19
scpatl4now, are you using 11.10?  If so, that behaviour is expected (and new); admin users are able to use the Update Manager without being asked for a password.  USC, Synaptic and the apt-get commands still need authorisation, though.

---

### Post by mcduck on 2011-10-20
> **Larkspur said:**
> scpatl4now, are you using 11.10?  If so, that behaviour is expected (and new); admin users are able to use the Update Manager without being asked for a password.  USC, Synaptic and the apt-get commands still need authorisation, though.

This is right, with the exception that the password-free updates are limited to security updates from trusted sources, so any other types of updates still require a password confirmation even with the Update Manager.

---

