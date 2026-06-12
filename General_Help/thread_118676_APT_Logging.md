---
title: "APT Logging:"
date: 2006-01-17
forum: General Help
---

### Post by klepto on 2006-01-17
Is there any log, or any way to log what apt installs. 
Every now and then something I installed makes something else
not work right and I'd like to know what I've installed so far.

---

### Post by GeneralZod on 2006-01-17
I'm not sure if there is a log kept, but

```

dpkg --list

```

will print out all currently installed packages.

Edit:

Try /var/log/dpkg.log.  I don't know how complete it is, though, and whether it lists things installed with Synaptic.

Edit2:

Just checked, and yes it does.

---

### Post by klepto on 2006-01-17
Thanks alot guy!

---

