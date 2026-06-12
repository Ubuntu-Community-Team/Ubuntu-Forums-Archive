---
title: "CF installer help"
date: 2007-09-08
forum: Desktop Effects &amp; Customization
---

### Post by Virtus92 on 2007-09-08
I used the CF installer to install compiz (fusion) and all the other stuff included in the script:
[http://ubuntuforums.org/showthread.php?t=508769]("http://ubuntuforums.org/showthread.php?t=508769")
Everything went fine until i wanted to launch the Fusion icon (it installed nice in my KDE menu).
```
root@ubuntudesktop:~$ fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: No module named compizconfig

```
Maybe the answer is in that other thread, but it has 59 (!!!) pages and I don't want to read them all.
So plz help me?!

//EDIT: I used a howto from the Forum to do it a different way. [SIZE="5"]**SOLVED**[/SIZE]

---

### Post by rainwalker on 2007-09-08
Under "Thread tools" mark this as solved, rather than in the psot

---

### Post by mattdee on 2007-09-18
how did u fix it?

---

### Post by bcdixit on 2007-09-19
i am getting exactly the same error. How was it solved?

---

### Post by Virtus92 on 2007-09-28
I just didn't used the CF installer because many people said it was bad so I used: [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty")

---

