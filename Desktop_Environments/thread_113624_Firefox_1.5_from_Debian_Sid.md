---
title: "Firefox 1.5 from Debian Sid"
date: 2006-01-06
forum: Desktop Environments
---

### Post by nix4me on 2006-01-06
Is there a way to install the Debian Sid Firefox 1.5 package in Ubuntu without breaking everything?

I know all about installing it from the mozilla binary and I know all about the different ways to get it installed....thats not what i want to do.

But, I want to experiment a little and try to get the Debian package installed.

Any ideas?

nix4me

---

### Post by dsjas297 on 2006-01-06
Use

```
dpkg -i *package*
```

where *package* is the package you want to install.

So far, I have had no package breaks by using dpkg.

---

### Post by nix4me on 2006-01-06
I know how, but Firefox 1.5 is probably not that simple.  From my understanding there are many problems associated with trying it.  Thus the reason it has not been backported and will not be backported.

nix4me

---

### Post by dcstar on 2006-01-06
[QUOTE=nix4me]Is there a way to install the Debian Sid Firefox 1.5 package in Ubuntu without breaking everything?

I know all about installing it from the mozilla binary and I know all about the different ways to get it installed....thats not what i want to do.

But, I want to experiment a little and try to get the Debian package installed.

Any ideas?

nix4me[/QUOTE]
The whole reason there is not a package is that it would try and replace the existing package - which would right royally break Breezy.

You need to install via the binary path (it isn't that difficult), or create another separate package **not** called "Firefox".

---

### Post by nix4me on 2006-01-06
I am already using 1.5.

I want to install the debian package for testing reasons.  I have a problem with Ubuntu and the binary Firefox 1.5 which does not show up on my Debian Sid box.

I am trying to find out why there is a problem.

nix4me

---

