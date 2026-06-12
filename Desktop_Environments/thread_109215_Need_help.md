---
title: "Need help"
date: 2005-12-28
forum: Desktop Environments
---

### Post by stinky321 on 2005-12-28
I have a little noobish question. wtf is a root password and why doesnt it let me enter  it:confused:

---

### Post by heimo on 2005-12-28
[quote=stinky321]I have a little noobish question. wtf is a root password and why doesnt it let me enter  it:confused:[/quote] 
root user / account is the most powerful user (windows equivalent would be administrator or "system"), also known as "super user". It has full permissions to everything on your system. In Ubuntu, root users password is not set by default (you or anyone else can't login using root account for security reasons). Normally when this password is prompted, you are actually asked to enter your own password (for so called sudo command) to temporarily use root privileges. This password is typically not echoed on screen not even ****** asterisk characters. This only works on your first regular user which was created during install process.

More information:
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by stinky321 on 2005-12-28
Ok thx. I thought i could install things with my new user too but i think im gonna use the installed user now

---

### Post by aysiu on 2005-12-28
[QUOTE=stinky321]Ok thx. I thought i could install things with my new user too but i think im gonna use the installed user now[/QUOTE] Can't you just give your new user admin privileges? System > Administration > Users and Groups

---

