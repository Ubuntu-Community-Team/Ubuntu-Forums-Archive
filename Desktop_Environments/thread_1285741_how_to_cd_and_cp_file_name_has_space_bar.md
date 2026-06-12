---
title: "how to cd and cp file name has space bar?"
date: 2009-10-08
forum: Desktop Environments
---

### Post by tonjaa on 2009-10-08
i try to change directory and copy file but i can't do it it file name has space bar like this.
folder name " [COLOR=RoyalBlue]Font Abc[/COLOR] "
file name     "[COLOR=DarkOrange] [COLOR=RoyalBlue]Font001 Abc Bold.ttf[/COLOR][/COLOR] "
how i can use command to change directory to folder ?
and how to use command for copy file ?

---

### Post by pmlxuser on 2009-10-08
simple place \ ie for folder you would do
```
$ cd Font\ Abc 
```
so for the file name 
```
 cp Font001\ Abc\ Bold.ttf  ~/home/fonts
```

---

### Post by tonjaa on 2009-10-08
:P[COLOR=DarkOrange] thank you very much [/COLOR].

---

### Post by arcmukh on 2012-05-07
I could not use files with spaces in loop
Below are the output :


$ls -1
a
b
c
d e[COLOR="Red"][/COLOR]
dest dir[COLOR="Red"][/COLOR]
f g[COLOR="Red"][/COLOR]
h i[COLOR="Red"][/COLOR]
$for i in `ls -1`; do echo -e $i;done
a
b
c
d[COLOR="Red"][/COLOR]
e[COLOR="Red"][/COLOR]
dest[COLOR="Red"][/COLOR]
dir[COLOR="Red"][/COLOR]
f[COLOR="Red"][/COLOR]
g[COLOR="Red"][/COLOR]
h[COLOR="Red"][/COLOR]
i[COLOR="Red"][/COLOR]
$

---

### Post by Elfy on 2012-05-07
Old thread closed.

---

