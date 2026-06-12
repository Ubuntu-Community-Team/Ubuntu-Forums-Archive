---
title: "Varsha, won't open."
date: 2006-06-13
forum: Desktop Environments
---

### Post by jISh on 2006-06-13
Hi, I'm trying to open the java application "Varsha", a DVD authoring program made in java.

So, I go to the terminal, and write
```
java -jar varsha.jar
```

and I get this:
```
Exception in thread "main" java.lang.NullPointerException
   at common.ui.HostFileSystemView.<init>(HostFileSystemView.java:53)
   at varsha.ui.Varsha.getHostFileSystemView(Varsha.java:1216)
   at varsha.ui.Varsha.addTabsToTabbedPane(Varsha.java:1201)
   at varsha.ui.Varsha.initUI(Varsha.java:1180)
   at varsha.ui.Varsha.<init>(Varsha.java:34)
   at varsha.ui.Varsha.main(Varsha.java:1243)

```

Can anybody tell me how to fix this?

---

### Post by meng on 2006-06-13
what version of java is installed?

---

### Post by jISh on 2006-06-13
Whichever comes with Ubuntu, I'm not sure.
The GIJ one I believe.

---

### Post by meng on 2006-06-14
Probably should try with Sun Java 1.5
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

