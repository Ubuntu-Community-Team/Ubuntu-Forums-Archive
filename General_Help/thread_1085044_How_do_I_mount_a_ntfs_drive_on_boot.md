---
title: "How do I mount a ntfs drive on boot?"
date: 2009-03-02
forum: General Help
---

### Post by tjtoml on 2009-03-02
I normally do it like this:
[IMG]http://i42.tinypic.com/2469da1.png[/IMG]

I want to automate that so that it happens whenever I log in.

---

### Post by Slim Odds on 2009-03-02
Funny how nobody ever does a forum search before they ask questions like this. This question gets asked about twice a day.

---

### Post by bodhi.zazen on 2009-03-02
You add an entry in fstab :)

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by tjtoml on 2009-03-02
thanks. got it....

by adding
```
/dev/sdb1 /media/"Western Digital"
```
to /etc/fstab

---

