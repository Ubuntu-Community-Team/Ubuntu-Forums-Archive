---
title: "root access???"
date: 2010-02-01
forum: Desktop Environments
---

### Post by dados on 2010-02-01
Hello to everyone,

Since yesterday I became a user ubuntu platform, and now I have one question, Why I can not open a root file and lost + found file in File system destination. It is say I have no permission, but I do not understand why, because I was install the system and I am administrator. I was read something like it is because of security reason, but how to open that files?

Thank you...

---

### Post by lykwydchykyn on 2010-02-01
See if this explains the issue:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lisati on 2010-02-01
Some things need "extra" privileges for you to be able to do them. In Ubuntu, you can use "sudo" (="**S**uper **U**ser **Do**")

Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Edit: beaten to it! :D

---

### Post by lykwydchykyn on 2010-02-01
> **lisati said:**
> Some things need "extra" privileges for you to be able to do them. In Ubuntu, you can use "sudo" (="**S**uper **U**ser **Do**")


Not to nitpick, but I feel compelled to  correct this sometimes when I see it.  "su" (and thus "sudo") doesn't stand for "super user", but rather "substitute user".  It can be used to run a command or enter a shell of any user, not just root.  It just defaults to root.

reference: [http://linux.die.net/man/1/su](http://linux.die.net/man/1/su)

---

### Post by lisati on 2010-02-01
> **lykwydchykyn said:**
> Not to nitpick, but I feel compelled to  correct this sometimes when I see it.  "su" (and thus "sudo") doesn't stand for "super user", but rather "substitute user".  It can be used to run a command or enter a shell of any user, not just root.  It just defaults to root.

reference: [http://linux.die.net/man/1/su](http://linux.die.net/man/1/su)

:) I was aware of that; not meaning to nitpick, but in this context, it amounts to the same thing.

---

### Post by dados on 2010-02-01
Thank you for fast answer... I just want to know why, and hove? Also did I have restricted with other privileges with administrator login, and not only open this two files?

---

### Post by lykwydchykyn on 2010-02-01
> **lisati said:**
> :) I was aware of that; not meaning to nitpick, but in this context, it amounts to the same thing.
Just trying to kill a common misnomer.  I realize it's secondary to, and largely irrelevant to, solving the OP's problem.

speaking of which:

> **dados said:**
> Thank you for fast answer... I just want to know why, and hove? Also did I have restricted with other privileges with administrator login, and not only open this two files?

Even though you are "administrator", you do not have root privileges by default.  This is different from how it works on Windows.

Being administrator on Ubuntu means you have the privilege to run sudo and acquire root privileges.  But you have to run sudo (or some graphical equivalent like gksudo) before a command to actually do something that requires those privileges.

So if you want to do something with those files in Nautilus, you need to run Nautilus as root.  Run "gksudo nautilus" and you should be able to open those files after entering your password.

---

### Post by dados on 2010-02-01
Thanks, I will need some times to understand all this :-)

---

### Post by lisati on 2010-02-01
> **lykwydchykyn said:**
> Just trying to kill a common misnomer.  I realize it's secondary to, and largely irrelevant to, solving the OP's problem.


Thank you. One of the good things about comminities such as this one is that if misconceptions creep in, there's a good chance someone will be able to explain things gracefully, as you did.

---

