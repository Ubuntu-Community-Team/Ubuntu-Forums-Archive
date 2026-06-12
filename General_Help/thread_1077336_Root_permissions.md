---
title: "Root permissions"
date: 2009-02-22
forum: General Help
---

### Post by Ostrich37 on 2009-02-22
Hi
I am trying to load Joomla in Ubuntu. The intructions say to open it in /opt. However when I try this I get a message saying I do not have permissions. I am working on a laptop dual booted with Ubuntu and Vista and I loaded everthing an the laptop and all the passwords. How can I get round this or what have I done wrong?
Jack

---

### Post by kmac on 2009-02-22
> **Ostrich37 said:**
> Hi
I am trying to load Joomla in Ubuntu. The intructions say to open it in /opt. However when I try this I get a message saying I do not have permissions. I am working on a laptop dual booted with Ubuntu and Vista and I loaded everthing an the laptop and all the passwords. How can I get round this or what have I done wrong?
Jack

```
sudo nautilus /opt
```

---

### Post by spiderbatdad on 2009-02-22
maybe try community documentation...unpacking it in opt will not automatically work with standard ubuntu apache2 package whick looks in /var/www
[https://help.ubuntu.com/community/Joomla%201.5](https://help.ubuntu.com/community/Joomla%201.5)
[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)
learn how to use sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Ostrich37 on 2009-02-23
Hi
Thanks guys I'll try these sugestions. I'll be away for a week or so but will report back with success or otherwise!
Jack

---

