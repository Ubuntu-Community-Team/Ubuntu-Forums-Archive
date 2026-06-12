---
title: "No printscreen,no icons working for KDE 4.2"
date: 2009-03-10
forum: Desktop Environments
---

### Post by tdgs on 2009-03-10
Hello I've just installed KDE 4.2 and I have a couple of issues.

First of all printscreen refuses to work.Don't know why.I can only take screenshots using Ksnapshot.

Second a lot of system icons don't appear.Instead I see a couple question marks.My dekstop looks like this:

[img]http://i123.photobucket.com/albums/o302/steliosthesmart/problem.png[/img]

I'm running Kubuntu 8.10 and it's a fresh install I've also installed Nvidia drivers 177 version.

My system has

-AMD 64 Athlon
-Nvidia Geforce 7950GT

Any clues anyone? :(

---

### Post by yther on 2009-03-10
```
aptitude search icon | grep -i kde
```

If none of the icon theme packs have "i" beside them, try installing one of them.  I believe **kde-icons-oxygen** is the default, but if it somehow didn't get installed you might not have any icons!  Otherwise, something might be funny with the menu itself.  Try logging out and back in, running "ldconfig" in a terminal, or even rebooting.

Regarding PrintScreen... I don't think this has ever done anything for me in KDE.  I use KSnapshot for my screen captures, too.

---

