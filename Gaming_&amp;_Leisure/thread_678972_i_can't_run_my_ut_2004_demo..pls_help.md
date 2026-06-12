---
title: "i can't run my ut 2004 demo..pls help"
date: 2008-01-26
forum: Gaming &amp; Leisure
---

### Post by uselessname on 2008-01-26
well im a first timer here and hope that i will be enlightened ..

i had a problem on running the ut 2004 demo

i downloaded it in a certain german site (i forgot what's its name)
and i think its legit..
filename:
ut2004-lnx-demo3334.run
i able to install this on my pc but the problem is that when i try to run the game on the terminal..of course...
this is what i've typed in the terminal:

frost@frost-desktop:~$ ut2004

and this was the result:

bash: ut2004: command not found

..apparently,it didn't run,then i've tied to change the directory to where the ut2004 demo  was located,and here is what happens:

frost@frost-desktop:~$ cd ~/ut2004demo
frost@frost-desktop:~ut2004demo$ ut2004
bash: ut2004: command not found
frost@frost-desktop:~ut2004demo$ ./ut2004-demo
./ut2004-bin: error while loading shared libraries: libstdc++.so.5:
cannot open shared folder file: No such file or directory

..and that was my problem
i couldn't understand it bec. im still not familiar really with ubuntu

do i missed something or there was something wrong on my pc?
any suggestions,help,reactions will do
you can mail me at 

thank you

---

### Post by Perfect Storm on 2008-01-26
```
sudo aptitude install libstdc++5
```

should do it.

---

### Post by uselessname on 2008-01-28
great help,sir...
tnx...
anyway,the email thing..
sorry my bad..
i always forget that..ugh!!
again..
arigatou gozaimasu

anyway 
im thinking of installing diablo2 on ubuntu
is that possible?how?

---

### Post by Perfect Storm on 2008-01-28
It is, please search our wine forum for that question. If you have trouble with it you can post in that forum.

---

