---
title: "chown on 206,682 items"
date: 2008-12-29
forum: General Help
---

### Post by mashcaster on 2008-12-29
I have tried chown on 206,682 items in a specific folder but it does not allow it:

> mashcaster@mashcaster-desktop:~$ sudo chown -R mashcaster /home/mashcaster/Desktop/new/*
[sudo] password for mashcaster: 
sudo: unable to execute /bin/chown: Argument list too long
mashcaster@mashcaster-desktop:~$ 


How do I get around this problem?

---

### Post by d1291 on 2008-12-29
Here's a possible solution (bash):

[b]for i in /home/mashcaster/Desktop/new/*
do
chown -R mashcaster $i
done[/b]

You might want to do su and run the whole thing from a root terminal to avoid 200'000 sudo calls, or stick it in a script and sudo that.

---

