---
title: "need little compilation help"
date: 2005-06-25
forum: Desktop Environments
---

### Post by glasscleaner on 2005-06-25
i try to compile a game named lincity-ng 1.0

when i type the sudo ./configure command, after few second i got this error:
[B]
*configure: error: Library requirements (libxml-2.0 >= 2.6.11) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.*[/B]

this is not the first time i compile a problem but this time i am very very stuck. i dont catch the sence of this.

someone can tell me what to do please?


thanks

---

### Post by skoal on 2005-06-25
I believe you need the libxml2-*dev* package (not just libxml2).

\\//_

---

### Post by glasscleaner on 2005-06-25
[QUOTE=skoal]I believe you need the libxml2-*dev* package (not just libxml2).

\\//_[/QUOTE]

skoal this is the x time your help me you are to nice hehehe :)

---

### Post by glasscleaner on 2005-06-25
everything work now but after the configure, the **jam** command do nothing :(

[B][I]amphore@ubuntu:~/files/jeuxlinux/lincity-ng-1.0$ jam

amphore@ubuntu:~/files/jeuxlinux/lincity-ng-1.0$[/I][/B]

 ](*,)

---

