---
title: "Dependency is not satisfiable: gir1.2-muffin-3.0?"
date: 2015-03-19
forum: Desktop Environments
---

### Post by remmas-sido on 2015-03-19
Hello guys 
I am using Ubuntu 12.04, I am trying to install and setup the Cinnamon Desktop Environment. I have downloaded a package named cinnamon version [CENTER][COLOR=#333333][FONT=Trebuchet MS]1.4-UP3 from this link: 
[/FONT][/COLOR][/CENTER][http://packages.linuxmint.com/list.php?release=Maya#backport;](http://packages.linuxmint.com/list.php?release=Maya#backport;) however, when I try to install it with the Ubuntu Software Center it give me this error: Dependency is not satisfiable: gir1.2-muffin-3.0.
Is there anyway to solve it, also is there a way I can add Linux Mint repository  to software sources list,because I am not a big fan of PPA.

---

### Post by buzzingrobot on 2015-03-19
You're seeing that message, of course, because that package is not available in the 12.04 repositories.  I see it is available on the Mint repo.  Whether or not it could be successfully installed and used on 12.04, and whether it has its own dependencies that would need to be installed... I don't know. (If you do try installing it, I'd recommend using gdebi or the command line.  If additional dependencies are needed, these will display them, and you can try to chase them down and install them.)

---

### Post by ian-weisser on 2015-03-19
That package does not exist in 12.04. It was added to Ubuntu in 14.04.
```
$ rmadison gir1.2-muffin-3.0
 gir1.2-muffin-3.0 | 1.7.3-1ubuntu1 | trusty/universe | amd64, arm64, armhf, i386, powerpc
 gir1.2-muffin-3.0 | 2.2.6-2        | utopic/universe | amd64, arm64, armhf, i386, powerpc, ppc64el
 gir1.2-muffin-3.0 | 2.2.6-4        | vivid/universe  | amd64, arm64, armhf, i386, powerpc, ppc64el

```

I see three choices for you:

1) Easiest: Upgrade to Ubuntu 14.04 or later.

2) Harder: Find a PPA or backport of the package someplace on the dirty, untrustworthy internet that is compatible with 12.04

3) Hardest: Download the source and build the package locally.

---

