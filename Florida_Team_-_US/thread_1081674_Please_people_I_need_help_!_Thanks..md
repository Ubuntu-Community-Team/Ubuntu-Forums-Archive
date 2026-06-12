---
title: "Please people I need help ! Thanks."
date: 2009-02-26
forum: Florida Team - US
---

### Post by dimensionpr on 2009-02-26
I am trying to install Ubuntu in a ideapad u330 and I get this black screen with this information:

Linux Ubuntu 2.6.27-7-generic #1 SMP fri Oct 24 06:40:41 UTC 2008 x86_64
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
ubuntu@ubuntu:~$

---

### Post by Sealbhach on 2009-02-26
It may be you installed the mimimal installation - if so, all you get is that black screen with a command prompt.

Type

```
 startx 
```

and press Enter just to see what happens.

---

### Post by dantrevino on 2009-02-28
Did you install the server CD?  If you did, 

```
sudo apt-get install ubuntu-desktop
```

will get you set up.

dan

---

### Post by MRCeltic on 2009-04-14
You can also try hitting the F4 key when the live menu comes up and select safe graphics mode, sometimes this helps

---

