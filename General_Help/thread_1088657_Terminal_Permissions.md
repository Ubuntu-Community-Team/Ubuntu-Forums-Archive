---
title: "Terminal Permissions"
date: 2009-03-06
forum: General Help
---

### Post by gdn1947 on 2009-03-06
Ubuntu 8.10

Typing  /etc/udev/rules.d/70-persistent-net.rules produces "Permission Denied". How do I change the permissions to allow this command to execute?

Thanks

---

### Post by howefield on 2009-03-06
Preface it with sudo ?

---

### Post by sisco311 on 2009-03-06
/etc/udev/rules.d/70-persistent-net.rules is a configuration file (plain text). 

you can edit the file as root:
```
gksu gedit /etc/udev/rules.d/70-persistent-net.rules
```

what are you trying to do? maybe we can help.

---

### Post by gdn1947 on 2009-03-06
sudo: etc/udev/rules.d/70-persistent-net.rules: command not found

Is that the correct expression of the command? I have tried several other combinations around sudo: and etc but no success

---

### Post by gdn1947 on 2009-03-06
Hi Sisko311, I am trying to follow a guide found on the internet to get a Belkin 54 (f5d7050 V3) USB Wireless Adaptor working. It is a nightmare which should be reatively simple, apparently. Any help you can offer would be appreciated. And yes, I have posted this in other forums but with no success as yet.

---

### Post by dgoosens on 2009-03-06
you should use sudo without a semicolon

```
sudo etc/udev/rules.d/70-persistent-net.rules
```

---

