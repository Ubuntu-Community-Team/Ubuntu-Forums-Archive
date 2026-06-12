---
title: "Can't run nicotine (slsk client)?"
date: 2005-04-09
forum: Desktop Environments
---

### Post by dangerous666 on 2005-04-09
I can install nicotine app through apt-get, but I can't get it running.  :-| 

When I try to run nicotine i get the following message at the terminal:

Nicotine supports "psyco", an inline optimizer for python
code, you can get it at [http://sourceforge.net/projects/psyco/](http://sourceforge.net/projects/psyco/)
Can not find required PyGTK. The current search path is
['/usr/bin', '/usr/lib/python24.zip', '/usr/lib/python2.4', '/usr/lib/python2.4/plat-linux2', '/usr/lib/python2.4/lib-tk', '/usr/lib/python2.4/lib-dynload', '/usr/local/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages/HTMLgen', '/usr/lib/python2.4/site-packages/Numeric', '/usr/lib/python2.4/site-packages/PIL', '/usr/lib/site-python']

I realized the Pygtk, in debian, is called python-gtk2, and I have installed (ubuntu default) the python-gtk2 vs 2.6...

What's wrong?  :-s

---

### Post by bored2k on 2005-04-09
> The following NEW packages will be installed:
  nicotine python-psyco python2.4-psyco

Do you have all three?

---

### Post by dangerous666 on 2005-04-09
[QUOTE=bored2k]Do you have all three?[/QUOTE]

when I try to instal python-psico, apt get says that it depends of a python-gtk2 lower than 2.4....

Have you tried nicotine?
I've already done that.... I would like to know why the nicotine's deb is downloaded and installed without solving its dependencies... 

In the error message, it says:
Can not find required PyGTK. The current search path is
['/usr/bin', '/usr/lib/python24.zip', '/usr/lib/python2.4', '/usr/lib/python2.4/plat-linux2', '/usr/lib/python2.4/lib-tk', '/usr/lib/python2.4/lib-dynload', '/usr/local/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages/HTMLgen', '/usr/lib/python2.4/site-packages/Numeric', '/usr/lib/python2.4/site-packages/PIL', '/usr/lib/site-python']

So can I conclude that my pygtk installation is located in a wrong place?

---

### Post by bored2k on 2005-04-09
[QUOTE=dangerous666]when I try to instal python-psico, apt get says that it depends of a python-gtk2 lower than 2.4....

Have you tried nicotine?[/QUOTE]
 What?! what repositories are you using? I just installed nicotine
> Setting up python2.4-psyco (1.3-1ubuntu2) ...

Setting up python-psyco (1.3-1ubuntu2) ...
bored@psychotic:~$

Oh oh remove the python-gtk2 you got from Debian, use UBuntu repos.

---

