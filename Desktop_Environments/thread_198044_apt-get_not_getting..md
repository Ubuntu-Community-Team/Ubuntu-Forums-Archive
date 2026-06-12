---
title: "apt-get not getting."
date: 2006-06-16
forum: Desktop Environments
---

### Post by ph33r213 on 2006-06-16
Hello. When ever I tried to apt-get some packages that I found, it can never find it. But, when I look in packages.ubuntu.com, they're there. I wouldn't have a problem with that, but when ever I try to get what I need from the site, there's always lots of dependencies I don't have, and going through all of them is kind of time consuming. :( Could it be my sources.list? How can I get the original one that came with Ubuntu?

---

### Post by ifokkema on 2006-06-16
[QUOTE=ph33r213]Hello. When ever I tried to apt-get some packages that I found, it can never find it. But, when I look in packages.ubuntu.com, they're there. I wouldn't have a problem with that, but when ever I try to get what I need from the site, there's always lots of dependencies I don't have, and going through all of them is kind of time consuming. :( Could it be my sources.list? How can I get the original one that came with Ubuntu?[/QUOTE]

I'm not sure I understand your problem completely, but it might be that you do not have your universe and/or multiverse repositories enabled. Could you show us your /etc/apt/sources.list file?

---

### Post by ph33r213 on 2006-06-16
I tried to open it, but it just came up with a blank file.

---

### Post by ifokkema on 2006-06-16
[QUOTE=ph33r213]I tried to open it, but it just came up with a blank file.[/QUOTE]
Hmm.... I assume running
```
sudo apt-get update
```

will return errors as well then.

I'm currently working from a Breezy PC, so I can't send you a standard Dapper sources.list. I bet it's posted at least once on this forum, else somewhere on the net.

---

### Post by az on 2006-06-16
[QUOTE=ph33r213]Hello. When ever I tried to apt-get some packages that I found, it can never find it. But, when I look in packages.ubuntu.com, they're there. I wouldn't have a problem with that, but when ever I try to get what I need from the site, there's always lots of dependencies I don't have, and going through all of them is kind of time consuming. :( Could it be my sources.list? How can I get the original one that came with Ubuntu?[/QUOTE]
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

