---
title: "I keep getting this error"
date: 2008-12-13
forum: General Help
---

### Post by Heeter on 2008-12-13
Hi all,

when I am installing a package, or updating something, I keep getting this error:
```

Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Yet everything seems fine with the install.

What is this error?

Thanks

Heeter

---

### Post by bluefrog on 2008-12-13
system-tools-backends apparently failed to install correctly.

in a terminal try
sudo dpkg --configure -a
and/or
sudo apt-get install -f

---

### Post by iponeverything on 2008-12-13
See if this clears up the problem for you.

```
sudo apt-get install util-linux 
```

---

### Post by Heeter on 2008-12-13
Hey Guys,

Thanks for help, but it didn't work, still getting the errors.


Heeter

---

### Post by plunder on 2008-12-13
after i updated i got this error, i reinstalled ubuntu did all the updates and now i'm still getting the error

Ubuntu 8.10 64-bit
Acer Aspire 6920G


If anyone else has the issue please post

---

