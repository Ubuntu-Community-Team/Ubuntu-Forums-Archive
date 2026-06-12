---
title: "Runnung programs remotely"
date: 2008-12-26
forum: General Help
---

### Post by Ajp7987 on 2008-12-26
Hello all, I am trying to run a program on a computer that I am logged into via an ssh connection and have that program run and display on that computer.  Is this possible and if so, how?

---

### Post by Ahadiel on 2008-12-26
Assuming you're logged into an account with an active X display, try this
```
DISPLAY=:0.0 command
```

---

