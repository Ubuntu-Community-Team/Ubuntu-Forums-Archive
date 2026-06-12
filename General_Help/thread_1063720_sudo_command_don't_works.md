---
title: "sudo command don't works"
date: 2009-02-08
forum: General Help
---

### Post by alex0705 on 2009-02-08
if i want to install a aplication by the terminal, the code is 
sudo apt-get ...
then i need to type in my pasword, but i can't do that if i push any character on the keyboard it don't works, what do i need to do?

---

### Post by drs305 on 2009-02-08
That is a normal security feature. You won't see the characters as you type but they are being recorded. Type your password, then hit ENTER.

---

### Post by Monotoko on 2009-02-08
It does work, it just doesnt show it, if it showed your password youd be rather screwed dontcha think?

just type your password in as it is, ignore the fact it isnt coming up then press enter

---

### Post by alex0705 on 2009-02-09
okay thx, that worked

---

### Post by blazemore on 2009-02-09
Actually, this is an excellent point.
It might be a good idea to provide some kind of visual feedback for sudo

eg

```
user@ubuntu-desktop: sudo apt-get update
enter password: *********

```

---

### Post by sisco311 on 2009-02-09
> **blazemore said:**
> Actually, this is an excellent point.
It might be a good idea to provide some kind of visual feedback for sudo

eg

```
user@ubuntu-desktop: sudo apt-get update
enter password: *********

```

[http://brainstorm.ubuntu.com/idea/11136/]("http://brainstorm.ubuntu.com/idea/11136/")

[http://brainstorm.ubuntu.com/idea/11118/]("http://brainstorm.ubuntu.com/idea/11118/")

---

