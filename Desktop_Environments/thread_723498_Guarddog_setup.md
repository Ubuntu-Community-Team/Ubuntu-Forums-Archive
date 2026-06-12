---
title: "Guarddog setup"
date: 2008-03-13
forum: Desktop Environments
---

### Post by Malikius on 2008-03-13
I am trying to change the settings in Guarddog but it tells me I don't have administrative access. I am the only user on this system. How do I change my user access to admin. Or do I need to log in as root???? Awaiting assistance. 

Thanks in advance.

---

### Post by chadeldridge on 2008-03-14
Run the application with sudo or gksudo (if its an X based program).  I know nothing of this application so I could be completely off the mark, but any time you need admin access to do something just throw sudo in front of the command in terminal or gksudo for GUI programs.

---

### Post by kellemes on 2008-03-14
You can start guarddog from the terminal like so..
```
gksudo guarddog &
```

gksudo: asks for your password.. this gives you the root-privileges you need.

---

### Post by Malikius on 2008-03-16
thanks I will try that.

---

### Post by mjrwingnut on 2008-06-09
Be sure to enbale "DNS, FTP, HTTP, HTTPS, POP3 & STMP" or it will not work in the internet zone

---

