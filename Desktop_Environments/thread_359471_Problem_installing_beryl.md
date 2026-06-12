---
title: "Problem installing beryl"
date: 2007-02-12
forum: Desktop Environments
---

### Post by ohmycar on 2007-02-12
I added the respotories for beryl and i uninstalled it and tried to reinstall it but i get this error message:

here is a screenshot:
[IMG]http://img401.imageshack.us/img401/7353/screenshotkf9.png[/IMG]

---

### Post by [S|G] on 2007-02-12
It looks like you've got some conflicting packages on your system.
You could try to type "sudo apt-get install beryl-core" in a terminal and see which problems will show up. If you get more "but it is not going to be installed" messages, try to "sudo apt-get install [package name]" where the name is the package that isn't going to be installed.

At some point you'll probably run into packages that are installed that are from a different version that beryl was expecting, maybe because you added extra repositories with newer/conflicting versions of existing packages.

---

### Post by ohmycar on 2007-02-13
yeah, i got it to work now. turns out i was just mismatching packages.
all i did was reinstall ubuntu - upgrade to edgy - reinstall beryl

now its beautiful :)

---

### Post by Brunellus on 2007-02-13
Thread moved.  Beryl is off-topic in Absolute Beginners.

---

### Post by jvc26 on 2007-02-13
The latest beryl does require a more or less completely updated computer - or at least it did when it first came out. :)
Il

---

