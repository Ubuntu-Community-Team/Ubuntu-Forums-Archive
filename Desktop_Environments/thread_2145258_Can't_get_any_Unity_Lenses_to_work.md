---
title: "Can't get any Unity Lenses to work"
date: 2013-05-14
forum: Desktop Environments
---

### Post by lisistaan on 2013-05-14
I'm new to Ubuntu and am interested in getting some different lenses but no matter what lens I try (Rotten Tomatoes, calculator, cities scope, etc) I can't get any of them to work. I copy and past the exact code I need into the terminal and it runs the command but then at the end I get this message: ```
E: Unable to locate package unity-lens-utilities
E: Unable to locate package unity-scope-rottentomatoes


```

This is what happened after trying Rotten Tomatoes using this code: ```


sudo add-apt-repository ppa:scopes-packagers/ppa  
sudo apt-get update && sudo apt-get -y install unity-lens-utilities unity-scope-rottentomatoes 
```

Any help would be appreciated

---

### Post by diesch on 2013-05-14
Which version of Ubuntu are you using?

This packages are only available from this PPA for Ubuntu 12.04 and 12.10. I don't now if there's another source for this packages that supports other Ubuntu versions.

---

### Post by lisistaan on 2013-05-14
Ah, that would make sense as I'm using 13.04

---

### Post by Frogs Hair on 2013-05-15
If the following is the correct PPA there are raring packages listed . [https://launchpad.net/~scopes-packagers/+archive/ppa](https://launchpad.net/~scopes-packagers/+archive/ppa)

---

### Post by lisistaan on 2013-05-15
Thank you very much!

---

### Post by diesch on 2013-05-15
> **Frogs Hair said:**
> If the following is the correct PPA there are raring packages listed . [https://launchpad.net/~scopes-packagers/+archive/ppa](https://launchpad.net/~scopes-packagers/+archive/ppa)

But not for *unity-lens-utilities* and *unity-scope-rottentomatoes *

---

