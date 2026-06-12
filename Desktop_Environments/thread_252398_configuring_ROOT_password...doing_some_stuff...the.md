---
title: "configuring ROOT password...doing some stuff...then disabling root again/.."
date: 2006-09-06
forum: Desktop Environments
---

### Post by master5o1 on 2006-09-06
HOw do i do this...or is there a better way:

What I want to do is create my mySQL db...

I apparently need a root password, which it doesn't have :S:(

so, I figured i could configure the root password, (though i can't remember how), then do what i need with my creating the DB...

then disable root again...

Can someone please tell me the commands to do this, or atleast a better way...(including how to create a mySQL database)

---

### Post by aysiu on 2006-09-06
You don't need root:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by almrking on 2006-09-06
From Ubuntu Website:
To manually set a password for the root user, type in the following in the shell:
sudo passwd

After that you are asked to type in the new root password twice. Finally, your root user has its own password.

---

### Post by aysiu on 2006-09-06
Except that it's completely unnecessary. If you get tired of typing *sudo* multiple times, just do ```
sudo -i
``` and you'll be root for all practical purposes.

---

