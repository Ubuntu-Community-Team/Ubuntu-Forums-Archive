---
title: "I think I might have lost my private gpg key"
date: 2009-05-02
forum: General Help
---

### Post by slick666 on 2009-05-02
I recently upgraded from Intrepid to Jaunty but because I so tweaked my last system I decided to do a fresh install. I backed up my gpg private key using the command.
```
--export-secret-keys
```
and then I restored it by importing the keyfile that it generated. I've since tried to use it but all the apps that use it have some filure of another and after reading up on it it seems as if I didn't back up properly. I can see the key when I use the following command.
```

gpg --list-secret-keys
/home/XXXXXX/.gnupg/secring.gpg
-------------------------------
sec#  XXXXX/XXXXXXXX 2009-03-05
uid                  XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
ssb   XXXXX/XXXXXXXX 2009-03-05

```
It seems like the key is there but not. Have I truly lost my secret key and is there another way for me to reissue a key for my e-mail?

---

### Post by slick666 on 2009-05-03
bump bump

No ideas?

---

### Post by fdrake on 2009-05-03
[see here]("http://www.hackdiary.com/2004/01/18/revoking-a-gpg-key/") for an alternative

[here]("http://ubuntuforums.org/showthread.php?t=52179") it is explained how u can import your key, if you have a revocation certificate

---

