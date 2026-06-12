---
title: "Way to find install date for a linux system"
date: 2009-01-03
forum: General Help
---

### Post by nemp on 2009-01-03
Is there a way to find the date a particular instance of linux OS was installed ?

---

### Post by Sorivenul on 2009-01-03
syslog should tell you, but you won't need all of it:
```
sudo cat /var/log/installer/syslog | less
```

To exit the view, just type "q", without the quotes.

The date in syslog should be your install date. I'm currently working on a new setup, and my output begins with:
> Dec 26 05:49:31 

---

### Post by abn91c on 2009-01-03
install hardinfo from the repositories then click on the operating system line

---

### Post by nemp on 2009-01-03
Thank you :)

---

### Post by rampage_1973 on 2011-03-23
> **Sorivenul said:**
> syslog should tell you, but you won't need all of it:
```
sudo cat /var/log/installer/syslog | less
```

To exit the view, just type "q", without the quotes.

The date in syslog should be your install date. I'm currently working on a new setup, and my output begins with:

you can also do this (just another way to get the same info)

at root prompt type "ls -al /var/log/installer/syslog" 

results should be similiar to below:

-rw------- 1 root root 230110 2009-04-13 13:29 /var/log/installer/syslog

note the date here "2009-04-13 13:29" 

I know this post is older but i hope that it helps someone else like me out!

thanks for sharing your knowledge!

---

