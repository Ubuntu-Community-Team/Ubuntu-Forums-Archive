---
title: "OpenOffice only works for sudo"
date: 2006-08-21
forum: Desktop Environments
---

### Post by jimscafe on 2006-08-21
I have read many threads about OpenOffice problems and some are similar to my problem. But the errors people get are different.

I cannot start open office either by clicking on an open office file in Nautilus or by trying to start open office (any application) from the menu.

However, if I launch openoffice from a terminal window using sudo, or start nautilus using sudo and click on an oo file, it works. Here is a terminal example :-

paul@wm-ubunut:~$ ooffice - writer
[Java framework] Error in function createUserSettingsDocument (elements.cxx).javaldx failed!
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
/usr/lib/openoffice/program/soffice: line 233: 10919 Aborted                 "$sd_prog/$sd_binary" "$@"

** (process:10906): WARNING **: Unknown error forking main binary / abnormal early exit ...
paul@wm-ubunut:~$ sudo ooffice -writer
Password:

This last example worked...

I am new to the permissions side of Linux and these seems like a problem to do with permissions but I don't know how to fix it.

When I click on an oo document from nautilus, the openoffice splash screen appears for a few seconds, then disappears, then after about 10 seconds the entry in the task bar disappears.

---

### Post by RikoW on 2006-08-21
could it be that you started openoffice for the first time with sudo?
check, who is the owner of the .openoffice2 directory (and files therein) in your home dir:


```
> ls -la .openoffice.org2
total 12
drwxr-xr-x  3 wichmann wichmann 4096 2006-08-18 13:18 ./
drwxr-xr-x 67 wichmann wichmann 4096 2006-08-21 09:59 ../
drwxr-xr-x 18 wichmann wichmann 4096 2006-07-07 09:02 user/

```

If it's not you, but root that might explain the problem. You can change the ownership via:

```
chown -R username:username .openoffice2
```

(replace *username* with your username, of course :)

Cheers,

              Riko

---

