---
title: "scim breaks firefox 1.5"
date: 2006-05-17
forum: Desktop Environments
---

### Post by cesera on 2006-05-17
I am using Kubuntu 5.10 (Breezy) and have installed firefox 1.5 as described in:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

but when I try to install scim as described in:

[http://www.ubuntuforums.org/showthread.php?p=124214]("http://www.ubuntuforums.org/showthread.php?p=124214")

as soon as I install the following packages:
* scim
* scim-chinese
* scim-config-socket
* scim-frontend-socket
* scim-gtk2-immodule
* scim-server-socket
* scim-tables-zh (option)
* xfonts-intl-chinese
* xfonts-intl-chinese-big
* ttf-arphic-gbsn00lp
* ttf-arphic-gkai00mp
* ttf-arphic-bkai00mp
* ttf-arphic-bsmi00lp

I can no longer start firefox, it comes up with the following error (when run from the command line):

```
/opt/firefox/run-mozilla.sh: line 131:  9656 Segmentation fault      "$prog" ${1+"$@"}
```

And as soon as I remove them again it works again.

Does anyone know what I can do about this and if it is possible to set up a Chinese input method in Kubuntu without breaking firefox 1.5

---

### Post by link141 on 2006-05-17
You *are* using SCIM as your input method for Chineese, did you follow the specialized directions for installing it with the version of Firefox you uploaded?  The Wiki you provided in the link states that Firefox crashes on startup with SCIM installed.  Also, this is a Mozilla independent release of firefox, it may not be as compatible with Ubuntu packages, though this is an unlikely cause.  Try following the instructions for installing Firefox with SCIM, it's down the page on the wiki (the direct links --> [https://wiki.ubuntu.com/SCIM](https://wiki.ubuntu.com/SCIM) |  [https://wiki.ubuntu.com/CompileFirefoxNewVersion](https://wiki.ubuntu.com/CompileFirefoxNewVersion) ) if you don't know how to compile (instructions provided) correctly you may want to check out these input method programs (I didn't check them out yet)  XIM, IIIMF, UIM, kinput, XCIN, or Chinput.  Come back with any problems you encounter, we'll be here to help ;).

---

