---
title: "build-dep fails"
date: 2008-12-17
forum: General Help
---

### Post by Meow27 on 2008-12-17
whenever i do sudo apt-get build-dep [insert program name here in this case battle for wesnoth]
i get the message ```
E: Build-dependencies for wesnoth could not be satisfied.

```

i think its  cause i replaced libc6 on hardy with a jaunty version.....but im not sure.... any way around this? (i want the newer version of libc6 >_<)

---

### Post by Meow27 on 2008-12-19
bump

---

### Post by FuturePilot on 2008-12-19
> **Meow27 said:**
> 

i think its  cause i replaced libc6 on hardy with a jaunty version.....but im not sure.... any way around this? (i want the newer version of libc6 >_<)

It could be, especially if you still have the repository enabled. Is there any particular reason you installed the version from Jaunty? Generally mixing stuff from different releases is a very bad idea.

---

### Post by Meow27 on 2008-12-19
i think the reason was that i wanted to be able to get gegl on, but the package manager said i needed a newer version of libc6, so i got the latest :/

can you explain to me which repositories to close and open?

---

