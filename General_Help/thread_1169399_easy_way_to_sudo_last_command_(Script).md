---
title: "easy way to sudo last command (Script)"
date: 2009-05-25
forum: General Help
---

### Post by swisstone198 on 2009-05-25
Edit

---

### Post by satnelav on 2009-05-25
in bash I would rather use 'sudo !!'

---

### Post by glotz on 2009-05-25
You could just use```
sudo !!
```courtesy of bash.

---

### Post by swisstone198 on 2009-05-25
> **satnelav said:**
> in bash I would rather use 'sudo !!'

It's just a little easier to type SS

---

### Post by sisco311 on 2009-05-25
EDIT: too late !!

what about:
```
sudo !!
```

EDIT2:
> **swisstone198 said:**
> It's just a little easier to type SS
```
alias SS='sudo !!'
```;)

---

### Post by swisstone198 on 2009-05-25
> **sisco311 said:**
> EDIT: too late !!

what about:
```
sudo !!
```EDIT2:

```
alias SS='sudo !!'
```;)

You can't do aliass SS='sudo !!'

you could do

alias SS='sudo `history 2 | head -1 | cut -c 8- `'

---

### Post by glotz on 2009-05-25
> **swisstone198 said:**
> # SSYou mean $ SS. ;)

---

### Post by swisstone198 on 2009-05-25
Sorry, i should have tested this a bit more, it slips up on a few things.

---

