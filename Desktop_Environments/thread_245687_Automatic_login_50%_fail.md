---
title: "Automatic login 50% fail"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Sfac on 2006-08-28
Hi all, im having a weird problem with automatic login. My account is setted for automatic login in the login window but almost 50% of the times it fails and it required manual access.
Any hints?
Thank you in advance.

---

### Post by Sfac on 2006-08-28
Bump

---

### Post by jimbob on 2006-08-28
You are talking about 50% of the times you boot up right?

Take a look at the file /etc/gdm/gdm.conf.

Near the beginning you should see lines like:

AutomaticLoginEnable=true
AutomaticLogin=<your user name here>

Other than that I don't know what to tell you.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Sfac on 2006-08-28
It was the first thing i checked...my username is there.

---

