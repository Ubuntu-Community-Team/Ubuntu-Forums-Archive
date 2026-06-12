---
title: "Having set a root password, can I then un-set it?"
date: 2009-02-14
forum: General Help
---

### Post by Inquisitorthemad on 2009-02-14
I had to invoke a root password to get my hard disk up and running again. I want to change things to how they were beforehand - with the root password nonexistent and thus uncrackable. Is there any way for me to do this, short of reinstalling Ubuntu?

---

### Post by scragar on 2009-02-14
Open your /etc/shadow file:
```
sudo gedit /etc/shadow
```
And find the root entry:
```
root:[color=red]....[/color]:14198:0:99999:7:::
```
You see the bit I replace with .... ? make it an !
```
root:[color=red]![/color]:14198:0:99999:7:::
```
Congrats, the root account is now password less.

---

### Post by dcstar on 2009-02-14
> **Inquisitorthemad said:**
> I had to invoke a root password to get my hard disk up and running again. I want to change things to how they were beforehand - with the root password nonexistent and thus uncrackable. Is there any way for me to do this, short of reinstalling Ubuntu?

```
sudo passwd -l root
```
If you need it later on:
```
sudo passwd -u root
```

---

