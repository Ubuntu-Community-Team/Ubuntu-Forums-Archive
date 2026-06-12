---
title: "Unknown error message on update"
date: 2009-06-18
forum: General Help
---

### Post by joelw135 on 2009-06-18
I get the following error message when running update. How do I fix this? Thanks.

---

### Post by nandemonai on 2009-06-18
[http://aldeby.org/blog/index.php/adding-the-key-of-a-launchpad-ppa-repository.html](http://aldeby.org/blog/index.php/adding-the-key-of-a-launchpad-ppa-repository.html)

Next time read the instructions properly when adding a 3rd party repository. ;)

---

### Post by lindsay7 on 2009-06-19
Type these to commands in the termial. and add the Key number that is listed in the error message. Note you only need the last 8 digits so it will be like this.


gpg --keyserver keyserver.ubuntu.com --recv DA6DEEAA

gpg --export --armor DA6DEEAA | sudo apt-key add -

then sudo apt-get update


You will most likely need to do this some other time so keep these instructions around.

---

### Post by joelw135 on 2009-06-19
[QUOTE=lindsay7;7482235]Type these to commands in the termial. and add the Key number that is listed in the error message. Note you only need the last 8 digits so it will be like this.


gpg --keyserver keyserver.ubuntu.com --recv DA6DEEAA

gpg --export --armor DA6DEEAA | sudo apt-key add -

then sudo apt-get update

Thanks I think it worked.

---

