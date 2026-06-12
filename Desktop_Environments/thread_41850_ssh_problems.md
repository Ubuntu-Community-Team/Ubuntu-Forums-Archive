---
title: "ssh problems"
date: 2005-06-15
forum: Desktop Environments
---

### Post by mirtux on 2005-06-15
Hi,
   i'm trying to access a computer via ssh but this is the output it gives me:
 ```

$ssh pippo@namehost
#**Permission denied (publickey)**
$

``` 
and it gives me the prompt again without asking for password.

What is the problem with that machine?

Regards,
MC

---

### Post by Knome_fan on 2005-06-15
Just a guess, but it looks like the ssh daemon on this machine is configure to use public key authentication. So the best option is probably to get a public key that works on this machine, or to configure sshd on this machine to also accept login via password only.

Good luck!

---

