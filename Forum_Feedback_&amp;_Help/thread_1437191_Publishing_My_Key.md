---
title: "Publishing My Key"
date: 2010-03-23
forum: Forum Feedback &amp; Help
---

### Post by uRock on 2010-03-23
I am trying to publish a key so I can sign the Launchpad CoC. I have created one key just for this purpose but when I run the command to upload I get the following output. How do I fix this? ```
rabbit@rabbit-desktop:~$ gpg --send-keys --keyserver keyserver.ubuntu.com 12345678
gpg: WARNING: unsafe permissions on configuration file `/home/rabbit/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/rabbit/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver send failed: general error
rabbit@rabbit-desktop:~$ 

``` I edited the 8 digits back to 12345678 in this post.

Thanx,
Ronnie

---

### Post by bodhi.zazen on 2010-03-23
```
chmod 700 ~/.gnupg
chmod 600 ~/.gnupg/gpg.conf
```

---

### Post by cariboo on 2010-03-23
Make sure you have the firewall on the system you are using turned off when trying to send the key too. Several people have had that problem.

---

### Post by uRock on 2010-03-23
Those worked thanks!:)

---

