---
title: "dpkg was interupted"
date: 2009-03-20
forum: General Help
---

### Post by ulfj on 2009-03-20
I get this error from time to time and then cannot download updates,when I put this into the terminal it says I must be a super user how do I correct this without doing a complete reinstall?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by howefield on 2009-03-20
> **ulfj said:**
> I get this error from time to time and then cannot download updates,when I put this into the terminal it says I must be a super user how do I correct this without doing a complete reinstall?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Precede the command with sudo, ie
```

sudo dpkg --configure -a
```

---

### Post by ulfj on 2009-03-20
great thank you, this seemed to work but when I ran the updates it said I had 1 broken (missed the next part) and I need to run a filter to locate?Does anyone know what this was or do I need to try to replicate the message?

---

### Post by howefield on 2009-03-20
It's a while since I had this, but I think if you load up Synaptic Package Manager, and press the "Custom Filters" button, then on broken. That should show the problem package.

---

### Post by ulfj on 2009-03-20
thanks that didn't show what was broken but did download a couple of small files and now ubuntu is happy again.

---

### Post by revpaul on 2009-03-21
> **howefield said:**
> Precede the command with sudo, ie
```

sudo dpkg --configure -a
```



Thank you worked like a charm :D

---

### Post by jwernecke on 2009-03-21
I get the same dpkg was interupted blah blah... i go into xterm type sudo dpkg --configure -a hit enter and it pops up with this parse error on update file 1048 when i go into the update file it is doing this "#padding" thing about 300 times and i cant modify it or delete it. What do I need to do to fix this issue. Thanks guys

---

