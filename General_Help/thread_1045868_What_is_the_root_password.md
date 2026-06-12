---
title: "What is the root password??"
date: 2009-01-20
forum: General Help
---

### Post by dmakane on 2009-01-20
Hello,

I am trying to edit a file in /etc/X11/ and it just won>t let me save saying I have not the necessary permissions.
When I installed Ubuntu, I set a password for the main account but it is not working for the root.

How can I get the root permisions...

Thanks for help.

Michel

---

### Post by dcstar on 2009-01-20
> **dmakane said:**
> Hello,

I am trying to edit a file in /etc/X11/ and it just won>t let me save saying I have not the necessary permissions.
When I installed Ubuntu, I set a password for the main account but it is not working for the root.
........

root is disabled by default, use sudo with your password.

---

### Post by blackened on 2009-01-20
> **dmakane said:**
> Hello,

I am trying to edit a file in /etc/X11/ and it just won>t let me save saying I have not the necessary permissions.
When I installed Ubuntu, I set a password for the main account but it is not working for the root.

How can I get the root permisions...

Thanks for help.

Michel

I'm assuming you're trying to use gedit to change xorg.conf. The appropriate syntax would be

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by taurus on 2009-01-20
Here is something for you to read regarding sudo/gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

