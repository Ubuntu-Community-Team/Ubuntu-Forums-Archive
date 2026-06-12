---
title: "Why doesn't Canonical send out a firefox update?"
date: 2006-02-06
forum: Desktop Environments
---

### Post by SuperMike on 2006-02-06
Why doesn't Canonical send out a Firefox update? Seems easy enough to do. The natives are getting restless and are coming up with their own solution:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

Seems like an easy thing for Canonical to do and it looks like they've missed more than one version release that they had an opp. to send out an install from.

---

### Post by aysiu on 2006-02-06
Updates to software happen only every six months. Firefox 1.5 will be in Dapper in April. If you're that restless, that's what the Wiki is for.

---

### Post by kaamos on 2006-02-06
Type this command in a terminal and you understand why it will not be updated:
```
(apt-cache rdepends firefox && apt-cache rdepends mozilla-firefox) | sed 's/ //g;s/^|//g;' | sort | grep -v "^ReverseDepends" | sort | uniq | xargs apt-cache showsrc | grep "^Package" | sed 's/Package: //g' | sort | uniq | grep -v "buntu-meta$"
```
(command copied from jdongs post)

---

### Post by GeneralZod on 2006-02-06
[QUOTE=SuperMike]Seems easy enough to do.[/QUOTE]

A "proper" replacement is rather harder than you'd think :)

[http://ubuntuforums.org/showthread.php?t=96595](http://ubuntuforums.org/showthread.php?t=96595)

---

### Post by lcg on 2006-02-06
[QUOTE=SuperMike]Why doesn't Canonical send out a Firefox update?[/QUOTE]
Because after a release that version is stable and remains so. Only security critical updates take place. And even those are usually done via backporting a security patch instead of packaging a new version. All in the interest of stability.

[QUOTE=SuperMike]Seems like an easy thing for Canonical to do and it looks like they've missed more than one version release that they had an opp. to send out an install from.[/QUOTE]
If you really think that updating firefox is that easy, you might want to read [the point of view of the backports team]("http://www.ubuntuforums.org/showthread.php?t=96595").

HTH,
Lars

---

### Post by SuperMike on 2006-02-06
Thanks for the update, guys. I didn't realize all of this. Well, as long as my Firefox is secure, then I'm cool with waiting.

---

