---
title: "terminal is automatically terminating"
date: 2009-02-06
forum: General Help
---

### Post by gautamdamodar on 2009-02-06
i use ubuntu 7.10 gusty
when i try to open terminal (logged in as root), it is automatically getting closd.
but i can open terminal when logged in as other users.
plz help me

---

### Post by drs305 on 2009-02-06
How are you opening the terminal?

You can try opening a terminal as a normal user and then running the following to gain admin rights:
```

sudo -i

```
To terminate admin rights, close the terminal or type "quit".

There is also "sudo -s" but "-i" keeps the user's shell, which is most likely what you want. You can read about the differences by typing *man sudo* in a terminal.

---

