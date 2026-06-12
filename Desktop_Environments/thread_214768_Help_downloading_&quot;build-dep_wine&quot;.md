---
title: "Help downloading &quot;build-dep wine&quot;"
date: 2006-07-13
forum: Desktop Environments
---

### Post by rickolus on 2006-07-13
After entering "sudo apt-get build-dep wine" i get this messgae

Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for wine


I am trying to follow this guide for installing WoW. 
[http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)

I have already added
"http://wine.budgetdedicated.com dapper/main Packages" and ran "sudo apt-get update"


Thanks for your help !

---

### Post by Ramses de Norre on 2006-07-13
You need this line in your sources.list to be able to fetch the source: ```
deb-**src** http://wine.budgetdedicated.com/apt dapper main
```

---

### Post by rickolus on 2006-07-13
Ok, I added that, and reloaded. Now when I enter:
"sudo apt-get build-dep wine" I get:

Reading package lists... Done
Building dependency tree... Done
Note, selecting libfontconfig1-dev instead of libfontconfig-dev
E: Build-dependencies for wine could not be satisfied.


=(

whats up with that?

---

### Post by EDevil on 2006-11-17
I too have this problem... Any solution?

---

### Post by YokoZar on 2006-11-17
> **EDevil said:**
> I too have this problem... Any solution?

That howto is very out of date and Wine has been patched to a very large degree to fix a lot of the problems it tries to work around.

Just try installing the standard Wine 0.9.25

---

