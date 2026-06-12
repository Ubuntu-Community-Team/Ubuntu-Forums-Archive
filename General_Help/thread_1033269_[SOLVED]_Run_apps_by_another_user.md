---
title: "[SOLVED] Run apps by another user"
date: 2009-01-07
forum: General Help
---

### Post by sikke on 2009-01-07
Hi!

I need to run apps by another user but I get an error.

examle: su - username

```
$ evolution
cannot open display: 
Run 'evolution --help' to see a full list of available command line options.
```

So it's probably because this user has no access to the other users X session. What should be done to allow other users to run programs in other users X session.

Regards

---

### Post by chrisccoulson on 2009-01-07
Before running "su", you should run the following:
```
xhost +
```
This disables access control for your X server, and will allow clients from other users to connect.

---

### Post by sikke on 2009-01-07
Thanks a lot! It works!

---

