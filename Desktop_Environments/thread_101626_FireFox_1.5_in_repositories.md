---
title: "FireFox 1.5 in repositories?"
date: 2005-12-10
forum: Desktop Environments
---

### Post by andefeldt on 2005-12-10
Hi,

Is there a repository for Ubuntu 5.10 which includes FireFox 1.5? Or how should you install it, if you don't want to mess up the apt-get database?

A.

---

### Post by claus on 2005-12-10
[QUOTE=andefeldt]Hi,

Is there a repository for Ubuntu 5.10 which includes FireFox 1.5? Or how should you install it, if you don't want to mess up the apt-get database?

A.[/QUOTE]
 I installed it as a tarball from the Mozilla site, but due to some really unpredictable behaviour I switched to Mozilla 1.7.12, which *is* included in the repositories. The tarball is actually quite easy, since all you have to do is, to extract it to the respective directory (like **/home/user/.mozilla/firefox**). But--as I said-- at least on my system **Firefox 1.5** didn't run very stable (some strange "flickering" up and down of the browser window, regardless of the site I loaded).

---

### Post by claus on 2005-12-10
[QUOTE=claus]I installed it as a tarball from the Mozilla site, but due to some really unpredictable behaviour I switched to Mozilla 1.7.12, which *is* included in the repositories. The tarball is actually quite easy, since all you have to do is, to extract it to the respective directory (like **/home/user/.mozilla/firefox**). But--as I said-- at least on my system **Firefox 1.5** didn't run very stable (some strange "flickering" up and down of the browser window, regardless of the site I loaded).[/QUOTE]

P.S.: If you want to give it a try nonetheless, I would recommend to uninstall the default **Firefox 1.07** before with ```
'sudo apt-get remove firefox' [*not* 'mozilla-firefox']
```

---

### Post by Sokraates on 2005-12-10
[QUOTE=andefeldt]Hi,

Is there a repository for Ubuntu 5.10 which includes FireFox 1.5? Or how should you install it, if you don't want to mess up the apt-get database?

A.[/QUOTE]

The best way to install FF 1.5 is with the tar.gz, as claus wrote.

Repos are not available yet and won't be for a long time, since backporting FF 1.5 requires a lot of libraries being backported, too. And until now it couldn't be done without breaking a lot of other stuff.

---

