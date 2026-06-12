---
title: "Simple editor for big files"
date: 2012-10-02
forum: Desktop Environments
---

### Post by Azyx on 2012-10-02
I have a log file utf-8 ca 50MB, but Gedit don't open it, and Leafpad only show about the first 1MB or something. Libre Office can show the hole file, but it is slow.
Any suggestion for a more simple text-editor without size-limiation and are quiet fast?

---

### Post by jerrrys on 2012-10-02
Got some hits [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=editor+for+big+files&as_qdr=all&sa=Google+Search&lang=en")

---

### Post by hictio on 2012-10-02
Emacs is your friend :)

---

### Post by Lars Noodén on 2012-10-02
Emacs, vi or nano.  If you use nano, launch it with -w so it does not automatically wrap long lines. 

However, if you are only reading the file, you might not want to risk editing it by mistake.  In that case, you can do well with using [less](http://manpages.ubuntu.com/manpages/precise/en/man1/less.1.html) or [more](http://manpages.ubuntu.com/manpages/precise/en/man1/more.1.html).  That will also give you the ability to search for patterns.

---

### Post by LewisTM on 2012-10-02
Medit, my favorite. Works just like Gedit but has no limitation.
[https://launchpad.net/ubuntu/quantal/+package/medit](https://launchpad.net/ubuntu/quantal/+package/medit)
(Use the Quantal 1.0.93-1 package, the Precise one is buggy):KS

Cheers!

---

