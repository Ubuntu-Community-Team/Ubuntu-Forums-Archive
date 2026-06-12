---
title: "Timed 'suspend', as opposed to timed 'shutdown'?"
date: 2009-03-23
forum: General Help
---

### Post by Pipps on 2009-03-23
I understand that a timed shutdown request can be performed using the following command:

```
sudo shutdown -h +60
```

Is it also possible to perform an equivalent command, to request a timed system suspend? And if so, how? Thank you.

---

### Post by damis648 on 2009-03-23
Never tried, but according to [this]("http://ubuntuforums.org/showpost.php?p=5081324&postcount=1") post:
```
pmi action suspend
```
will suspend, for timed I would try:
```
sleep 99; pmi action suspend
```
or
```
nohup sleep 99; pmi action suspend
```

---

### Post by kostja on 2010-06-22
didnt work for me : resulted in a timed freeze with no resume possibility (that im aware of). did i misunderstood something?

---

