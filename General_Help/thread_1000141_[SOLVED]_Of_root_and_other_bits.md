---
title: "[SOLVED] Of root and other bits"
date: 2008-12-02
forum: General Help
---

### Post by Silver_fox on 2008-12-02
Hi

I'm yet another boring newbie who cannot find the answer in F1. I am trying to run NetworkManager in terminal but the system tells me I need to be in root. However, when setting the O/S up, there has never been an opportunity to set up root with a password. How can I run NetworkManager as root when I can only sign in as a standard user?

---

### Post by Grolsche on 2008-12-02
Have u tried going to

System>administration>users and groups and then highlighting root and clicking unlock then go to properties of the root and enter a password?

---

### Post by snova on 2008-12-02
Prefix the command you're trying to run with sudo. Don't quote.

Enabling the root account is unsupported on these forums, being against Ubuntu policy or something like that, although possible.

---

### Post by Grolsche on 2008-12-02
ah , well me being a newbie too, that was the only way I could get it to work when i needed to do something and it came up with the message that the account I was on wasn't root.

I did try the su and sudo commands but that didnt work for me either.

---

### Post by sisco311 on 2008-12-02
prepend *sudo* to the command you want to run as root.
(use *gksu* for graphical applications.)

```
gksu NetworkManager
```

---

### Post by snowpine on 2008-12-02
Hi Silver Fox,
Usually when you come across a tutorial that says "Do x as root," it means the tutorial was not written specifically for Ubuntu. To "translate" the tutorial to Ubuntu, simply use the sudo command (as was suggested in your other thread). 

For example:

"Log in as root, open a terminal, and type: apt-get install firefox"

Becomes in Ubuntu:

"open a terminal, and type: sudo apt-get install firefox"

It's just the Ubuntu way of accomplishing the same thing.

---

### Post by utnubuuser on 2008-12-02
Doesn't "sudo su" give you equivalent to "root" privileges?

---

### Post by sisco311 on 2008-12-02
> **utnubuuser said:**
> Doesn't "sudo su" give you equivalent to "root" privileges?

*sudo su* or *sudo -s* starts a root shell, but keeps the current shell's environment.

*sudo su -* or *sudo -i* gives you roots environment configuration.

```
sisco@acme:~$ sudo -s
root@acme:~# echo $HOME
/home/sisco
root@acme:~# exit
exit
sisco@acme:~$ sudo -i
root@acme:~# echo $HOME
/root
root@acme:~# exit
logout
sisco@acme:~$ 

```

---

