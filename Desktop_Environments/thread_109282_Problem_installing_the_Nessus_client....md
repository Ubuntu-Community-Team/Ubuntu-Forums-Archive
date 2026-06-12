---
title: "Problem installing the Nessus client..."
date: 2005-12-28
forum: Desktop Environments
---

### Post by Spudgun on 2005-12-28
Hello there,
I'm having problems isntalling the Nessus client (Nessus Client 10.0.0 RC1). When I try to ./configure, I get the following error:

```
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```

Anyone have any idea how to fix this?

Thanks in advance,
Spudgun

---

### Post by Lambert on 2005-12-28
Check to see if you have this package installed.

[http://packages.ubuntu.com/breezy/libs/libgtk2.0-0]("http://packages.ubuntu.com/breezy/libs/libgtk2.0-0")

```
sudo dpkg -s libgtk2.0-0
```

if not it needs to be installed.

---

### Post by Spudgun on 2005-12-28
That package is already installed, anything I can do?

Thanks,
Spudgun

---

### Post by omenix on 2006-08-18
I have the libgtk installed but when I ./configure it still says that I dont have the package or wrong path..

---

### Post by omenix on 2006-08-18
Here is the error:

checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

---

