---
title: "Compiled Evince has no PDF support?"
date: 2009-02-19
forum: General Help
---

### Post by Psyphre on 2009-02-19
Hi,

I compiled evince yesterday successfully however for some odd reason it has no pdf support at all. Is this normal? Am I supposed to add pdf support afterwards or compile it with pdf support or something? I'm a bit confused, I'm sure it isn't supposed to be like this.

Thanks in advance.
Psyphre.

---

### Post by Yellow Pasque on 2009-02-20
My guess is that you didn't have all of the necessary development library packages installed (specifically libpoppler-dev). Run:
```
sudo apt-get build-dep evince
```
and then try configuring/making/installing again.

---

### Post by Psyphre on 2009-02-20
Temujin.

Thank you so much you were completely correct!
Just a final question, does that command work for everything I want to compile? Obviously i replace it with the name of the application/program.

Thanks again.

---

### Post by Yellow Pasque on 2009-02-20
Not always, but it's a good shortcut. The build-dep option will grab the dependencies you need to build a package as it appears in the Ubuntu repo. Sometimes, when you're compiling a newer/different version from source, there will be additional dependencies (or the versions in the repo won't be current enough). It's always a good idea to read any README/INSTALL text files that come with a source package (or maybe a wiki/FAQ on its website) to verify the dependencies and make sure you have the appropriate -dev package.

---

