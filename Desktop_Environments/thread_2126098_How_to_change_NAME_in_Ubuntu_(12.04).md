---
title: "How to change NAME in Ubuntu (12.04)"
date: 2013-03-16
forum: Desktop Environments
---

### Post by serbforce on 2013-03-16
Hello, i have this problem, when i try to change my name (not the username, but the actual display name) my ubuntu precise freezes and i have to reboot manually. ([https://www.dropbox.com/s/6javx34ha9el5gu/Example.jpg](https://www.dropbox.com/s/6javx34ha9el5gu/Example.jpg))
I am using Ubuntu 12.04 LTS with Gnome 3 shell desktop. Thanks in advance for any help !

- Srdjan

---

### Post by steeldriver on 2013-03-16
I don't know why it's doing that, but you could do it via the command line instead

```
sudo chfn -f "Display Name" username
```

See

```
man chfn
```

---

### Post by serbforce on 2013-03-16
> **steeldriver said:**
> I don't know why it's doing that, but you could do it via the command line instead

```
sudo chfn -f "Display Name" username
```

See

```
man chfn
```

Thank you so much, i dont know either.

---

