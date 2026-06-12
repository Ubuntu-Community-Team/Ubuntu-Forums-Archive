---
title: "Enlightenment without root permissions"
date: 2014-09-11
forum: Desktop Environments
---

### Post by ocket8888 on 2014-09-11
I want to use the Enlightenment DE, because it's what I'm used to and I like it a lot. However, I don't have root permissions on my machine. Due to the potential for this to wreck my user profile on the system, I'm hesitant to just type ```
./configure --prefix=$HOME/bin && make && make install && echo "exec Enlightenment" >> ~/.xinitrc
```
What can I do to ensure a healthy, sane installation?

---

### Post by ocket8888 on 2014-09-11
I didn't really make it very apparent, but I do have the source for the DE, and I'm reasonably competent at using the terminal.

---

### Post by QIII on 2014-09-11
Hello!

I have no idea if what you are trying to do will work, but ...

You can us sudo to elevate your user privileges to do just about anything you would need root access for.

---

