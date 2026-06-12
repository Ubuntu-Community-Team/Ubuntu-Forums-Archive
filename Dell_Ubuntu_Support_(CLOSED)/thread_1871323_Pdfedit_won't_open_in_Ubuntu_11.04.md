---
title: "Pdfedit won't open in Ubuntu 11.04"
date: 2011-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RSASKA on 2011-10-28
Hello,

I got Ubuntu 11.04, and followed the directions from the following website

[https://help.ubuntu.com/community/PDFedit](https://help.ubuntu.com/community/PDFedit)

However, when I attempt to launch it via command line, I get following error

pdfedit: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory


So, I did a search for applications and found the program.

No matter how many times I try to launch this icon, the program won't open.

Now, I found another website that may be more helpful

[http://ubuntuguide.net/edit-pdf-on-ubuntu-with-pdf-editor](http://ubuntuguide.net/edit-pdf-on-ubuntu-with-pdf-editor)

But I want to uninstall this non-functional pdfedit

What is the apt commant?

---

### Post by MG&amp;TL on 2011-10-28
If you are lucky, it will be in synaptic or in the software center (under installed programs).

If not, try:

```
sudo apt-get remove --purge pdfedit
```

Which method did you use? If method 1, then the above should work. If method2, I am not sure how alien works, hopefully it will be installed in the same way.

---

### Post by RSASKA on 2011-10-28
Never mind, I figured it out


Command # 1

sudo apt-get remove alien


Command # 2

sudo apt-get remove pdfedit


Command # 3

sudo apt-get install pdfedit


Now, it works like a charm :-)

---

### Post by MG&amp;TL on 2011-10-28
Actually, you should have been able to do:

```
sudo apt-get install pdfedit
```
 and it would solve all the dependencies for you.

EDIT: never mind, you got it. :D

---

### Post by MG&amp;TL on 2011-10-28
Edited the page to make things clearer. :D

---

