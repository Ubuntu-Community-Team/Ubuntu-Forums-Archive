---
title: "Is it possible to change locale + logout using a shell script?"
date: 2014-05-09
forum: Desktop Environments
---

### Post by Juhele on 2014-05-09
Hi,
I am creating a Lubuntu remaster for my friends and other people interested in using it. :-)  It is loading in Czech by default but some English speaking people from the linux community were interested in trying it. the remaster still contains the default Englich locale shipped with Lubuntu:

```
flynn@the-Grid:~$ locale -a
C
cs_CZ.utf8
C.UTF-8
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZM
en_ZM.utf8
en_ZW.utf8
POSIX
flynn@the-Grid:~$ 
```

Is it possible to easily change the locale to English using some shell script (which I can leave on desktop so user just clicks it) and then trigger logout so the user just executes the script and after login again he gets system in English?

thanks

---

