---
title: "Help with GPG Key"
date: 2009-01-13
forum: General Help
---

### Post by NewJack on 2009-01-13
I recently had to reinstall Ubuntu on my computer.  Did a wipe of my HDD (using DBAN) and did a clean install.  I had a GPG Key that I generated under my old install of Ubuntu and I still have the information about that key (Passphrase, Pub, Fingerprint and Sub) "written down".  

Here is the question:  Am I able to enter the key information somewhere to continue using the old key, or do I have to generate a new one?

---

### Post by NewJack on 2009-01-16
Bump

---

### Post by NewJack on 2009-01-23
Bump

---

### Post by Dr Small on 2009-01-23
If you no longer have the private/public key pair, then you have to make a new pair. All the old information is no longer good if you don't have the private key.

---

### Post by NewJack on 2009-01-24
I figured as much, just wasn't sure if there was a work around.  Thanks for the response.

---

### Post by adamlau on 2009-01-24
All you need is the private key. If you do not have that, then you have no choice but to --gen-key :) .

---

### Post by NewJack on 2009-01-24
I do have the Public Key, Fingerprint and Sub _***written***_ down.  With the combination of those, is it possible to restore everything?

---

### Post by Dr Small on 2009-01-24
> **NewJack said:**
> I do have the Public Key, Fingerprint and Sub _***written***_ down.  With the combination of those, is it possible to restore everything?
No. You'll need the private key (which you apparently don't have) in order to restore the key. Otherwise, anyone who has your public key would be able to make a private key based off of those same figures (defeats the purpose of GnuPG).

You had better just generate a new key and be done with it. ;)

---

### Post by NewJack on 2009-01-25
Thanks alot for the response.  New key it is :)

---

### Post by kevdog on 2009-01-25
What do you mean by sub?  I'm unfamiliar with that terminology.  However the private key is the crux to the entire problem.  May I suggest the following for backup next time:

1. If you want to keep a paper copy of the private key (which it seems like you did this time stating you "wrote" it down), use this utility:
[http://www.jabberwocky.com/software/paperkey/](http://www.jabberwocky.com/software/paperkey/)

---

