---
title: "debian buster xfce firefox esr how to enable apparmor profiles"
date: 2020-03-23
forum: Debian
---

### Post by ipv on 2020-03-23
the title of the thread is self-explanatory.

can someone please point me to a tutorial or guide me as to how i can enable app-armor profiles for firefox esr in debian buster xfce.

---

### Post by ipv on 2020-03-23
> **EuclideanCoffee said:**
> Please  post a new thread if you have a specific question about app-armor in  Debian

done.

> **EuclideanCoffee said:**
> Yes, exactly as it is written.

unfortunately no.

following this tutorial : [URL="https://flatlinesecurity.com/posts/firefox-apparmor/"]https://flatlinesecurity.com/posts/firefox-apparmor/
[/URL]
on 'buntu it works flawlessly but on debian when i do this :

```
sudo aa-enforce /etc/apparmor.d/usr.bin.Firefox
```

i get this :

```
Profile for /etc/apparmor.d/usr.bin.Firefox not found, skipping
```

---

### Post by ipv on 2020-03-23
sorted, figured it out from the debian wiki.

---

### Post by EuclideanCoffee on 2020-03-23
Please write your solution, so this can be a helpful resource for others. Thank you.

---

### Post by ipv on 2020-03-24
> **EuclideanCoffee said:**
> Please write your solution, so this can be a helpful resource for others.

[https://wiki.debian.org/AppArmor/HowToUse](https://wiki.debian.org/AppArmor/HowToUse)

---

