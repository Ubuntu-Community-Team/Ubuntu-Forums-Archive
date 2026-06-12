---
title: "Ubuntu bug or Noobie inexperience?"
date: 2006-02-03
forum: Desktop Environments
---

### Post by carlos1969 on 2006-02-03
Hi all, I just installed Ubuntu. I am making the transition from XP to Linux and after much research on Linux distros I decided on Ubuntyu.

I am trying to set up my internet access and upon typing the sudo pppoeconf command, I am prompted for a password

the only problem is as I type it in, my keyboard stops working. I see the prompt but as much as I hit the keys nothing is taken. mouse is working and my keyboard works except when I am prompted by a password. once the password is prompted, my keyboard stops working. 

so I ask, is it me? any suggestions?

---

### Post by Klaidas on 2006-02-03
The password is not displayed for security, but it is taken :)

---

### Post by carlos1969 on 2006-02-03
so its me......

is it the password different than my admin password?

---

### Post by hw-tph on 2006-02-03
When you use the sudo command, the password you are prompted for is your own password, the one you use to log on.


Håkan

---

### Post by Klaidas on 2006-02-03
Yes, when using sudo you must enter your password (not the root password)
More info: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

