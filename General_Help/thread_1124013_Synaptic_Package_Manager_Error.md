---
title: "Synaptic Package Manager Error"
date: 2009-04-12
forum: General Help
---

### Post by tysonxg on 2009-04-12
When I try to run the Synaptic Package Manager I get this error.
```

E: Type 'sudo' is not known on line 4 in source list /etc/apt/sources.list.d/pidgin-ppa.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```
I'm new to Ubuntu/Linux and have no knowledge in the terminal so please help.

---

### Post by hyper_ch on 2009-04-12
delete the /etc/apt/sources.list/pidgin-ppa.list file and add that repository again.

---

### Post by tysonxg on 2009-04-12
how do i delete it? becuase if i try 'sudo rm /etc/apt/sources.list/pidgin-ppa.list' i get '/etc/apt/sources.list/pidgin-ppa.list' so i don't think im doing it right....

---

### Post by hyper_ch on 2009-04-12
just navigate to the right directory and delete it from there.

---

### Post by CatKiller on 2009-04-13
> **tysonxg said:**
> how do i delete it? becuase if i try 'sudo rm /etc/apt/sources.list/pidgin-ppa.list' i get '/etc/apt/sources.list/pidgin-ppa.list' so i don't think im doing it right....

That should be sources.list.**d**. sources.list is just a text file. sources.list.d is a directory that has sources.list-type entries in.

---

