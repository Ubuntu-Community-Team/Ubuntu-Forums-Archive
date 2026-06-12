---
title: "[SOLVED] SOme help with GPG key...."
date: 2008-12-08
forum: General Help
---

### Post by gjoellee on 2008-12-08
I am about to sign the Ubuntero, but because of some reason the wrong key gets selected when i use this command:
```
gpg --clearsign UbuntuCodeofConduct-1.0.1.txt
```

you see, I made a key yesterday, but however I managed to write the the password wrong, and I wrote it from the same way twice so I do not have the password for that key.

I made a key today and it was successful, but because of the other key (made yesterday) is the default one, I cant sign up to become an Ubuntero.

---

### Post by Elfy on 2008-12-08
IF you login to your launchpad page - change details - you'll get a smallish bar with some options, one is OpenPGP keys - you should be able to deactivate the one causing problems

---

### Post by gjoellee on 2008-12-08
> **forestpixie said:**
> IF you login to your launchpad page - change details - you'll get a smallish bar with some options, one is OpenPGP keys - you should be able to deactivate the one causing problems

I have only one registered key at launchpad, it is the other, the one with the password I don't know which is set to default:
```
zippex@Zippex:~$ gpg --clearsign UbuntuCodeofConduct-1.0.1.txt

You need a passphrase to unlock the secret key for
user: "<the user and user commant) <e-mail>"
1024-bit DSA key, ID <ID of the one I don't have the passphrase for>, created 2008-12-07

Enter passphrase:

```I have one more key, how to I make that one appear and not the one that I don't have the passphrase for? (I guess it is some configuration on my computer)

---

### Post by Elfy on 2008-12-08
mmm not too sure - running seahorse shows my current one - I had 2 as well, maybe that will help.

---

### Post by gjoellee on 2008-12-08
> **forestpixie said:**
> mmm not too sure - running seahorse shows my current one - I had 2 as well, maybe that will help.

thank you, seahorse solved the problem :p

---

### Post by gjoellee on 2008-12-08
Solved :p

---

### Post by Elfy on 2008-12-08
Well I'd like to say I knew it would - but being honest - that was a good guess :D

---

