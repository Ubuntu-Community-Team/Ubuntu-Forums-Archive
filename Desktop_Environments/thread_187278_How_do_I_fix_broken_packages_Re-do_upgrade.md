---
title: "How do I fix broken packages/ Re-do upgrade?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-06-02
I've tried to upgrade to Dapper...but I'm having some major problems.

I have 47 broken packages.  How do I fix them?  I can't use Synaptic, so it will have to be via the terminal.

Or...am I better simply running the whole apt-get dist-upgrade again?

](*,)

---

### Post by Nachtengel on 2006-06-02
try:

```
sudo apt-get update
```

then 
```
apt-get install synaptic
```

that should get you back in business with synaptic & you can fix your problems from there.

---

