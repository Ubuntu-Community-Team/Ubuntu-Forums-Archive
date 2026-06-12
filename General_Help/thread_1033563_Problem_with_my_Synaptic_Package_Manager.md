---
title: "Problem with my Synaptic Package Manager"
date: 2009-01-07
forum: General Help
---

### Post by mbamaluikenna on 2009-01-07
When I open my Synaptic Package Manager, this message shows:

An error occured:

E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Pls how can I rectify this?

---

### Post by blazemore on 2009-01-07
What happens when you type ```
cat /etc/apt/sources.list
``` in a terminal?

---

### Post by namdung on 2009-01-07
Type in terminal
```
sudo dpkg --configure -a
sudo apt-get update

```

If any error message, post it here.

---

