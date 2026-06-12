---
title: "Another cryptic Message on Update"
date: 2009-06-19
forum: General Help
---

### Post by joelw135 on 2009-06-19
I received the below error and tried everything but no dice can someone please let me know what to do? Thanks. I tried this also.
gpg --keyserver keyserver.ubuntu.com --recv BF810CD5

gpg --export --armor BF810CD5 | sudo apt-key add -

sudo apt-get update

---

### Post by kostkon on 2009-06-19
Try giving this command
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7D2C7A23BF810CD5
```
and then do a
```
sudo apt-get update
```

---

### Post by joelw135 on 2009-06-19
> **kostkon said:**
> Try giving this command
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7D2C7A23BF810CD5
```
and then do a
```
sudo apt-get update
```

Thank you, I think that did it. Could you suggest a easy book to learn this?

---

### Post by kostkon on 2009-06-19
> **joelw135 said:**
> Thank you, I think that did it. Could you suggest a easy book to learn this?
Actually, there is a [free book]("http://www.ubuntupocketguide.com/") you can check. :)

Also a good resource is the [official Ubuntu documentation]("http://help.ubuntu.com/").

Hope that helps.

---

### Post by joelw135 on 2009-06-19
> **kostkon said:**
> Actually, there is a [free book]("http://www.ubuntupocketguide.com/") you can check. :)

Also a good resource is the [official Ubuntu documentation]("http://help.ubuntu.com/").

Hope that helps.

Thanks, just downloaded it and will start reading, but at my age I hope I can remember some of it.:lolflag:

---

### Post by QIII on 2009-06-19
I have several volumes of spiral notebooks I have kept since the Unix days.

Might be worth while to just start keeping notes.  I've saved my own backside on several occasions.

---

