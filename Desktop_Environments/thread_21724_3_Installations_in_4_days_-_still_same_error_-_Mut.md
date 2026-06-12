---
title: "3 Installations in 4 days - still same error - Mutt, Postfix"
date: 2005-03-23
forum: Desktop Environments
---

### Post by vvu on 2005-03-23
I have installed Kubuntu on three different machines with non-identical setups and I keep getting errors pertaining to Postfix, Postfix (something else), and Mutt - what gives here as I did not even choose to install these?  Almost everytime I apt-get something and install...I get an error regarding the script or install process about these three things.

Thanks.

---

### Post by bosteen on 2005-03-23
This one got me as well, but I offer a solution as seen elsewhere on this forum! (Works for me but YMMV...  oh yeah, sorry to whoever posted this solution first, I can't remember on what thread I saw it....)

```
$ sudo /etc/init.d/postfix stop
(enter password if needs be. This command turns off postfix)
$ sudo apt-get install postfix
```

In theory, this should stop the apt-get errors. Removing postfix may cause update errors later as it is part of the 'ubuntu-base' meta-package.

Ben

---

