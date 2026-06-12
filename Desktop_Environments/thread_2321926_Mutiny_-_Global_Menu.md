---
title: "Mutiny - Global Menu"
date: 2016-04-25
forum: Desktop Environments
---

### Post by $yl9pAR%t on 2016-04-25
Anybody knows, how to turn off (if possible) Global Menu in Mutiny?

Thanks in advance.

---

### Post by $yl9pAR%t on 2016-04-26
Bump.

---

### Post by QDR06VV9 on 2016-04-26
What dose this return from the terminal
```
apt-cache policy indicator-appmenu
```

---

### Post by $yl9pAR%t on 2016-04-26
I have non-english version of Ubuntu so better I'll just write. It is not installed, but of course available to install.

---

### Post by vasa1 on 2016-04-26
> **mefisto888 said:**
> I have non-english version of Ubuntu so better I'll just write. ...
@mefisto, please try this command:
```
LANG=C apt-cache policy indicator-appmenu
```Does it provide you with terminal output in "English"?

See: [http://askubuntu.com/questions/725855/why-is-lang-csudo-apt-get-clean-etc-recommended](http://askubuntu.com/questions/725855/why-is-lang-csudo-apt-get-clean-etc-recommended) for more.

---

### Post by $yl9pAR%t on 2016-04-26
Thanks for an advice about language. In meanwhile I have installed it (I mean indicator-appmenu).

```

indicator-appmenu:
  Installed: 15.02.0+16.04.20151104-0ubuntu1
  Candidate: 15.02.0+16.04.20151104-0ubuntu1
  Version table:
 *** 15.02.0+16.04.20151104-0ubuntu1 500
        500 http://pl.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by $yl9pAR%t on 2016-04-27
I think I got it. This Global Menu in Ubuntu MATE (with Mutiny) is called TopMenu Panel Applet and I can add/remove it whenever I wish. One thing I do not know yet is lack of menu after reboot, neither in windows neither on panel.

EDIT:
It was my fault, I had one more (almost invisible) TopMenu Panel Applet added on left panel. After removal it, everything is OK.

---

