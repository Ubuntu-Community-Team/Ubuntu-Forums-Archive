---
title: "OpenOffice 3.0 - not starting and not fully installing."
date: 2009-03-05
forum: General Help
---

### Post by ziemas on 2009-03-05
So here's my problem.
I couldn't start my OOo 2.4 on my Ubuntu 8.10 AMD64. More and more memmory was getting ocuppied and then my OS was stopping. Or getting incredibly slow.

So I updated to OOo 3.0, and nothing changed, but I couldn't install openoffice.org-emailmerge and openoffice.org-writer2latex. It was just giving no response when "adding extension".

Also removing these partially installed packets was impossible, and yes, I tried dpkg --configure -a, dpkg --remove, etc.

Any idea what bugs my OpenOffice, and what can I do about these packets?

---

### Post by Chandler258 on 2009-03-05
OOffice depends on Java Runtine enviroment. It's a long shot, but check if it is (properly) installed. Might be even a version problem. Try typing ```
java --version
``` in shell and paste output here.

Regars, M

---

### Post by ziemas on 2009-03-05
```
ziemas@ziemas-desktop:~$ java --version
Unrecognized option: --version
Could not create the Java virtual machine.

```

And for "java -version":

```

ziemas@ziemas-desktop:~$ java -version
java version "1.6.0_14-ea"
Java(TM) SE Runtime Environment (build 1.6.0_14-ea-b01)
OpenJDK 64-Bit Server VM (build 14.0-b10, mixed mode)

```



EDIT: Ok, fix'd. Removed java from my disk manually, and removed all the configuration files of openoffice and java. Then reinstalled and it's working. :>

---

