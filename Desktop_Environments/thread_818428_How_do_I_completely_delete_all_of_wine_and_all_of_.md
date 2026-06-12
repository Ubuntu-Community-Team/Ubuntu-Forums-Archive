---
title: "How do I completely delete all of wine and all of the programs installed using it?"
date: 2008-06-04
forum: Desktop Environments
---

### Post by Detailedghost on 2008-06-04
I've had too many problems with wine, and I have reason to believe it's corrupt. So I was wondering if there is a way to completely uninstall Wine and programs I install using it, so I can start over and try again.

---

### Post by jerome1232 on 2008-06-04
if you used apt-get to install
```
sudo apt-get remove --purge wine
```

you would also want to remove ~/.wine this is were all programs get installed to by defualt, also where configuration settings get saved
```
rm -rvI ~/.wine
```

you don't have to add the -vi but it lets you know what rm is doing and asks you to confirm it before doing it, it's nice in case you mistype what you want removed

changed rm command to the correct one (srry about that)

---

### Post by Rigrig on 2008-06-04
This:```
rm -vi ~/.wine
``` won't work, since *.wine* is a directory. also it would prompt you for every single file to remove, which would probably mean typing 'y' a lot of times.


This command:```
rm -rvI
``` works better for deleting it:
-r means to remove directories (**r**ecursively)
-v means it shows you everything that it is doing (**v**erbose)
-I (capital i) means it will ask you for confirmation once (from **I**nteractive)

---

### Post by jerome1232 on 2008-06-04
oh yeah lol srry I forgot you have to add -r

---

### Post by Detailedghost on 2008-06-05
thanks a ton!

---

