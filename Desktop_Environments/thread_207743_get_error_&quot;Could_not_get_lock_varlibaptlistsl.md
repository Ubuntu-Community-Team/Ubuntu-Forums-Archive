---
title: "get error &quot;Could not get lock /var/lib/apt/lists/lock&quot;"
date: 2006-07-02
forum: Desktop Environments
---

### Post by syxbit on 2006-07-02
help guys.
i get it when installing certain things (in this case Kaffeine), i only have 1 terminal open, and don't have synaptic or anything else open.

---

### Post by tonyr on 2006-07-02
You might have a 'not quite dead' apt process still running in the background.
In the terminal do
```

ps aux | grep apt

```

If it shows an apt looking process, you can do
```

sudo pkill apt

```
(or a more specific name) to get rid of it.

---

### Post by syxbit on 2006-07-02
i just tried doing an apt-get and it worked (before i was doing aptitude)

---

### Post by mukherjee.siddhartha on 2006-10-28
> **tonyr said:**
> You might have a 'not quite dead' apt process still running in the background.
In the terminal do
```

ps aux | grep apt

```If it shows an apt looking process, you can do
```

sudo pkill apt

```(or a more specific name) to get rid of it.Thanks, Itt worked :mrgreen:

---

### Post by AztecLogic on 2008-02-12
Or just delete the lock!

sudo rm /var/lib/apt/lists/lock

---

