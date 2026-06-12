---
title: "[SOLVED] Can't log in -&amp;gt; password changed?"
date: 2007-06-23
forum: Desktop Environments
---

### Post by neburzaragoza on 2007-06-23
Hi,

I changed  in Ubuntu 6.06 for two months. I always have been using the same login and password. this evening, I was intalling some silly things inmy laptop, but nothing serious (timidity, mediuntu...). Anyway nothing special with *sudo *or *passwd*.

I rebooted my computer and then, in the welcome message, I introduce my login and password, but I am able to log in my own session.

I restart with *Live CD*, I tried to changed my password for a new one, but they told me that my old one is not correct.

to sum up:[B]

-> I did not forget my password
-> My password has changed (impossible to change to a new one)
->right before restarting I did not change imporatant things with *sudo*.[/B]

what can I do?

meanwhile, I forced to remain in my Windows :(

thank you for your suggstions

---

### Post by soul_rebel on 2007-06-23
try to log in from the console (control-alt-F1)
and tell us if it works from there
(control-alt-f7 to get back to the graphic)

---

### Post by taurus on 2007-06-23
Maybe you are running out of space!  Boot into recovery mode from GRUB menu and post the output of this command here.

```
df -h
```
And if you want to free up some space, run

```
aptitude clean
df -h
```

---

### Post by neburzaragoza on 2007-06-23
here you have the console respone when I try to log in.

```

mon_login-laptop login : mon_login
password:
Last login : Fri Jun 22 21:53:47 2007 on :0
Linux mon_login-laptop 2.6.15-28-386 #1 PREEMPT Thu May 10 09:45:42 UTC 2007 i686 GNU&Linux
...
...
1 error from la last log in.
the last time was Sat 23 Jun 2007 11:25:47 PDT en tty1
```

but I think you're kind of right, before loggin out I was nearly 99% of my free space.
I-ll try you commandes right now!

thanks again

---

### Post by neburzaragoza on 2007-06-23
yeah!!!
definitly that was the problem, My Linux hd was to 100%.
I wrote your commands down and now I'm on 93%.
thank you very much for you help... how could I knew that?
cheers

---

