---
title: "Conky Display Ubuntu Version"
date: 2010-09-26
forum: Desktop Environments
---

### Post by Shadow21 on 2010-09-26
Is there a conky variable that displays the Ubuntu version (ex 10.04)?

---

### Post by bra|10n on 2010-09-26
[COLOR=Black]${pre_exec lsb_release -d | cut -f 2| tr "[:upper:]" "[:lower:]"}[/COLOR]

---

### Post by Shadow21 on 2010-09-26
> **bra|10n said:**
> [COLOR=Black]${pre_exec lsb_release -d | cut -f 2| tr "[:upper:]" "[:lower:]"}[/COLOR]

That's what I was looking for but is there a way to make that only show the 10.04?

---

### Post by hrickh on 2010-09-26
> **Shadow21 said:**
> That's what I was looking for but is there a way to make that only show the 10.04?
Change the "-d" to "-r".

R.
==

---

### Post by Shadow21 on 2010-09-26
> **hrickh said:**
> Change the "-d" to "-r".

R.
==

Thanks :)

---

### Post by MooseDog on 2010-09-26
another thanx!

---

### Post by Gaygerbil on 2010-09-27
Another, nohter thanks! : D

---

### Post by Shadow21 on 2010-10-10
Sorry to bring this back up but how do I change this:

```
${pre_exec lsb_release -d | cut -f 2| tr "[:upper:]" "[:lower:]"}
```

to make it only display the kernel version?

---

### Post by ner0tic on 2010-10-10
> **Shadow21 said:**
> Sorry to bring this back up but how do I change this:

```
${pre_exec lsb_release -d | cut -f 2| tr "[:upper:]" "[:lower:]"}
```

to make it only display the kernel version?

if i remember correctly ${kernel}

---

### Post by hrickh on 2010-10-11
> **ner0tic said:**
> if i remember correctly ${kernel}
It is. I have this in mine:

Kernel: $alignr$kernel

R.
==

---

### Post by Shadow21 on 2010-10-11
Thanks again :)

---

