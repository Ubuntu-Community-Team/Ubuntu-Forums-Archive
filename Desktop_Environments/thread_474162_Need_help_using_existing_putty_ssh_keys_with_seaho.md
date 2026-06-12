---
title: "Need help using existing putty ssh keys with seahorse"
date: 2007-06-14
forum: Desktop Environments
---

### Post by markymarknz on 2007-06-14
Hi everyone,

I have some servers setup and running fine and I access them remotely using ssh with public keys.
That is all working fine, however the keys I am using were generated using putty. When I try to import my existing private keys into seahorse it says they are of an "invalid file format".
They are standard rsa 1024 bit keys.
Does anyone know how to import these keys as I thought it would be a straight forward thing to do but it obviously isn't.

Cheers

Mark

---

### Post by markymarknz on 2007-06-17
bump :)
Anybody use Seahorse or another keyring manager that could import putty ssh keys?

---

### Post by hugmenot on 2007-06-18
Use the companion tool to putty to convert the key to the openssh format. I think it&#8217;s called puttygen.exe.

---

### Post by pfrancav on 2007-06-28
Hi, I've the same problem, I try to import the private key with seahorse, but seahorse don see like a private key.

How I convert?, I try puttygen but there is not optin to convert openssh

Thanks !

---

### Post by hugmenot on 2007-06-28
> **pfrancav said:**
> How I convert?, I try puttygen but there is not optin to convert openssh

Hello? The conversion menu?

---

### Post by markymarknz on 2007-07-14
Hi Everyone,

I tried using the puttygen.exe tool as suggested by hugmenot.
However I found that I could get seahorse to import the file but the passphrase associated with it would not be accepted. 
I ended up just creating a new key in seahorse and adding it to my servers to be accepted.
So I now have keys for when I use Putty in Windows and other keys for using Seahorse in Feisty.

Mark

---

