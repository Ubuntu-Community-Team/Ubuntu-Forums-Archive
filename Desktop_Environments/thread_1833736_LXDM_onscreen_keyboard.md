---
title: "LXDM onscreen keyboard"
date: 2011-08-26
forum: Desktop Environments
---

### Post by HarrisonNapper on 2011-08-26
Hey does anyone know how to get an onscreen keyboard like xvkbd or cellwriter to launch with the login screen in lxdm or how to revert Lubuntu to xdm (just installing and reconfiguring doesn't work, it has to be set to call lxsession in the same way that lxdm does)?

Any information is greatly appreciated. Cheers & TIA.

---

### Post by bmacgill on 2013-01-23
I found a related bug here: [https://answers.launchpad.net/onboard/+question/195106 ]("https://answers.launchpad.net/onboard/+question/195106")
___________________________


I did manage to install the following dependency:

 This fixed it:

```
$ sudo apt-get install python-gi-cairo
```

---

