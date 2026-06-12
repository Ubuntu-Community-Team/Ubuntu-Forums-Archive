---
title: "how could i accomplish this?"
date: 2011-01-19
forum: Desktop Environments
---

### Post by crazyjust on 2011-01-19
I am using ubuntu  10.10 desktop and running lamp on it for a small site. I have installed proftpd for ftp. I want to be able to log in ftp with my user (owner) and have owner be able to chmod,add,edit,delete files in /var/www. How exactly can I accomplish this? Thanks in advance.

---

### Post by 3Miro on 2011-01-19
From what you have written, the preferred way of doing those kind of tasks under Linux is SSH.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Make sure you read the security sections carefully and get familiar with the command line (i.e. terminal).

---

### Post by 3Miro on 2011-01-19
From what you have written, the preferred way of doing those kind of tasks under Linux is SSH.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Make sure you read the security sections carefully and get familiar with the command line (i.e. terminal).

---

### Post by crazyjust on 2011-01-19
Isn't there a way to make a users home directory /var/www?

---

### Post by crazyjust on 2011-01-19
Sorry posted twice. Tried to delete, but guess there is no option

---

### Post by crazyjust on 2011-01-19
Isn't there a way to make a users home directory /var/www?

---

### Post by Cheesehead on 2011-01-19
Sure, it's possible using links.  Seem 'man ln'.
But 3Miro is correct - SSH is a superior method, and is easier to maintain than an unusual linking scheme.

---

