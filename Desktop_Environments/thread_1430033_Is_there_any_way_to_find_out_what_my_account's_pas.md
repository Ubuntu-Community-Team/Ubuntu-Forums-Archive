---
title: "Is there any way to find out what my account's password is?"
date: 2010-03-14
forum: Desktop Environments
---

### Post by programming.name on 2010-03-14
Hi,
I am currently running Ubuntu 9.10 desktop edtion and I wonder if I could "recover" my account's password. When I say "recover", I mean I just want to know the current password that I forgot. Although I am the root, which means that I can cahnge and reset the password by typing $ sudo passwd [account's name], I just want to know if it is possible to recover or view the forgotten password.
 
Thanks.

---

### Post by richs-lxh on 2010-03-14
By "recover" you mean "crack" as that is the only way you are going to decrypt the passwd file.

Not sure if it's ok to post cracking tools on the forum, but John the Ripper is pretty well known, it is also in the Ubuntu repos. "apt-get install john".

Some more info:
[http://www.openwall.com/john/doc/EXAMPLES.shtml](http://www.openwall.com/john/doc/EXAMPLES.shtml)
[]("http://project-rainbowcrack.com/")
and:
[http://en.wikipedia.org/wiki/Rainbow_table](http://en.wikipedia.org/wiki/Rainbow_table)
[http://project-rainbowcrack.com/](http://project-rainbowcrack.com/)

But the easy way is obviously just to change the password.

---

