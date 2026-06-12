---
title: "Outdated Gaim version?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by ZombiekE on 2006-06-04
Hello, I have Gaim 1.5.1cvs. I would like to upgrade it to the latest version, but it's not in the repositories, at least the standard ones. Does anybody know any repository where I can get it?

I tried to install some plugins but they don't work with gaim 1.5.1cvs (they don't even appear and I would love to have the iRC plug-in).

Of course I could download it from Sourceforge and then install it on my own... but I would prefer to do everything with Synaptic.

Thank you :).

---

### Post by louis_nichols on 2006-06-04
1.5 IS the latest official version of gaim. the 2.0 version is still in beta stages, so cannot be included in ubuntu repos.

you can just install the source and use checkinstall instead of make install, so synaptic won't be confused.

follow [this thread]("http://ubuntuforums.org/showthread.php?t=100899&highlight=gaim+cvs")

---

### Post by PuleX on 2006-06-05
You can add this repository with unofficial gaim 2 beta 3 to your /etc/apt/sources.list

```
# Gaim 2 Beta 3
deb http://people.ubuntu.com/~seb128/deb ./
``` 

Stuff may break, though. (though it hasn't for me)

---

