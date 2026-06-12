---
title: "Kmail problem after upgrade KDE 3.5.0 -&gt; 3.5.1"
date: 2006-02-02
forum: Desktop Environments
---

### Post by cyklotronen on 2006-02-02
Can not start Kmail after my KDE 3.5.0 -> 3.5.1 upgrade.

I get the folowing error:
```
kmail: symbol lookup error: /usr/lib/libkmailprivate.so: undefined symbol: _ZN4KPIM8Identity4nullE
```

Have anyone a clue on how to solve this issue?

---

### Post by ERam123 on 2006-02-03
I get the same problem...  any ideas?

---

### Post by cyklotronen on 2006-02-03
I did a search in the adept manager for kmail and even though I had tried to do a full upgrade the kmail package was uppgradable and not uppgraded.

After uppgrading kmail everything runnes smooth. ;)

---

### Post by ERam123 on 2006-02-03
Worked for me as well.  Thanks!

---

### Post by daller on 2006-02-11
[QUOTE=cyklotronen]I did a search in the adept manager for kmail and even though I had tried to do a full upgrade the kmail package was uppgradable and not uppgraded.

After uppgrading kmail everything runnes smooth. ;)[/QUOTE]

How did you upgrade it when the package was held back? (Any console solution to this?)

---

### Post by Neo Ex on 2006-02-11
I think you can run 'sudo apt-get dist-upgrade', but I've solved simply checking KMail for upgrading in Adept (it will remove a package and installing another one, but that's why the package changed his name).

---

### Post by Aleksandersen on 2007-10-18
Hi forum,

I have the same problem. Though my KMail was upgraded during the dist-update. I have tried to reinstall KMail, but that did not fix the problem.

Other suggestions?

**Update:** I removed KMai and installed it again. Did not fix the problem.

---

