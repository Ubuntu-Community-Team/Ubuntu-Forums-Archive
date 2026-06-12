---
title: "Opening Firefox via ssh"
date: 2009-04-26
forum: General Help
---

### Post by GCoffee on 2009-04-26
Hello,

Ok, i want to open firefox via ssh (as in I can see the firefox window on the laptop im using) so I hooked up a SSH server etc

I can connect fine with:

ssh [email]ssh@xx.xxx.xxx.xx[/email] (ip adress where x's are0

so i login and get:

ssh@dellLap1:~$

I put in firefox and i get:

Error: no display specified.

I also tried ssh -x [email]ssh@xxxx..xx..xx[/email]

still no luck :(

Can anyone help?

GC.

---

### Post by 30003019 on 2009-04-26
try ```
ssh -X user@host
``` :-)

---

### Post by Sub101 on 2009-04-26
I use: 
```
ssh -X -C <user>@<ip>
```

Which tends to work for me

---

