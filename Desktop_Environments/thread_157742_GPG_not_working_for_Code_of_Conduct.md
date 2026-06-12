---
title: "GPG not working for Code of Conduct"
date: 2006-04-09
forum: Desktop Environments
---

### Post by obama on 2006-04-09
Hey everyone.  I've been trying to sign the "Code of Conduct" ([https://launchpad.net/codeofconduct/1.0](https://launchpad.net/codeofconduct/1.0)) for a while now, but it won't work.

I auto-generated my keys just today, and I'm new to gpg.  I run the command 

```
sudo gpg --clearsign ~/coc.txt
```

and it creates the appropriate .asc file.  However, when I submit this file online, it says "Error" "No public key"

Can anyone provide some assistance?

---

### Post by az on 2006-04-09
Did you upload your key fingerprint to launchpad?

[https://wiki.ubuntu.com/GnuPrivacyGuardHowto](https://wiki.ubuntu.com/GnuPrivacyGuardHowto)

---

