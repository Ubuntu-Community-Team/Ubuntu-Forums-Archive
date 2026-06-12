---
title: "linux kernel program doubt"
date: 2009-02-20
forum: General Help
---

### Post by sangupari on 2009-02-20
Hi 
when ls is used in the command line what are the functions called in the linux kernel??:KS

---

### Post by sdennie on 2009-02-20
You probably want the strace command:

```

strace ls

```

Check the man page for more information.

---

