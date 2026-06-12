---
title: "GPG Keys for Launchpad"
date: 2009-04-25
forum: General Help
---

### Post by daz4126 on 2009-04-25
I'm trying to follow the instructions on this page:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

There is a line that gives a web address "for additional information how to add GPG keys to your system"

This page tells you how to add a key, but the original page has now reference of any key!

Does anybody know where I would find this key, because I can't install the package without it.

Thanks,

DAZ

---

### Post by zvacet on 2009-04-25
Install package and you will see message thqat GPGKeyxxxxxxxxxxxxxxxxxx is missing and you can not install.Do this

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -
```

replace **KEY** with **number** and your package will install.

---

### Post by daz4126 on 2009-04-25
Thanks Zvacet, your advice worked great ... unfortunately the fix I was installing did not!

DAZ

---

