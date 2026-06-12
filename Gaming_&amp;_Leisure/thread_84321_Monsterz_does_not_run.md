---
title: "Monsterz does not run"
date: 2005-10-30
forum: Gaming &amp; Leisure
---

### Post by banjobacon on 2005-10-30
I tried running [Monsterz](http://sam.zoy.org/monsterz/), but it's not working. A black window opens when I run the program, followed by a split second of music, and then the window closes. This is what is left in the terminal:

> leo@phonie:~/apps/monsterz-0.6.1$ python monsterz.py
monsterz.py:361: RuntimeWarning: tp_compare didn't return -1 or -2 for exception  if (w, h) == size:
monsterz.py: could not open data from `'.
Traceback (most recent call last):
  File "monsterz.py", line 1977, in ?
    main()
  File "monsterz.py", line 1966, in main
    data = Data(sharedir)
  File "monsterz.py", line 330, in __init__
    mini = scale(mini, (t * 7 / 8 - 1, t * 7 / 8 - 1))
  File "monsterz.py", line 361, in _scale
    if (w, h) == size:
RuntimeError: attempt to unlock an unlocked surface
leo@phonie:~/apps/monsterz-0.6.1$


I get the same results when running from source or installing the .deb packages. I have Python, pygame and numeric installed.

Can anyone run this program? Any clues as to what may be the problem?

---

### Post by Kemotaha on 2005-11-01
I got the game to run.  I am running breezy and jsut installed the debs and the dependencies.  I didn't have any problems.

---

### Post by Nomis on 2005-11-14
I have exactly the same problem.

Does anybody know what we can do?

---

### Post by No6 on 2005-11-14
The problem is the 0.6.1 version of the game. You need to use 0.6.0 version. Get it from here...

[http://sam.zoy.org/monsterz/monsterz-data_0.6.0_all.deb]("http://sam.zoy.org/monsterz/monsterz-data_0.6.0_all.deb")
[http://sam.zoy.org/monsterz/monsterz_0.6.0_i386.deb](http://sam.zoy.org/monsterz/monsterz_0.6.0_i386.deb)

HTH

---

