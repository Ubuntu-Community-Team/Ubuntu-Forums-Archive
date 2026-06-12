---
title: "public keys"
date: 2009-05-22
forum: General Help
---

### Post by dtdave on 2009-05-22
Hi, just wondering what public keys are for, sometimes I see instructions on how to install them with a 3rd party app, such as virtual box or another, where some people dont even say to install them for other apps. Do you really need them or not? Are they Ubuntu specific or any linux distro?

thanks

Dave

---

### Post by hexanol on 2009-05-22
Public keys are related to "assymetric cryptography". You can do a bunch of things with assymetric cryptography; encryption, authentification, integrity checking, etc. 

You could always look at the wikipedia [article]("http://en.wikipedia.org/wiki/Public-key_cryptography"), it explains better than me. :p

---

### Post by Brandon Williams on 2009-05-23
In the cases where you see public keys being used for package archives, it's specifically for verifying the integrity of the archive packages lists. Keys are used in order to ensure that you are getting the correct package list when you download it from the archive source, which in turn allows you to verify the integrity of the individual packages when you install them. 

Such verification is not required, and so you will sometimes find archives that don't use it. Also, if you download a specific package, rather than using apt, then you are circumventing the verification, which is part of apt, not dpkg. You can verify package integrity manually by checking md5 checksums for individual packages, but that can be tedious.

It's safer for your system if you only install software from trusted sources. The use of asymetric keys by apt helps to ensure that this is the case.

---

### Post by dtdave on 2009-05-26
thanks a bunch!

---

