---
title: "need terminal guide"
date: 2009-05-14
forum: General Help
---

### Post by volter on 2009-05-14
I'm noob and I want to understand what I'm writing in the terminal, so can someone find some guide and give it to me.

---

### Post by saidinesh5 on 2009-05-14
here , this helped me a lot the last semister

[http://www.freeos.com/guides/lsst/index.html](http://www.freeos.com/guides/lsst/index.html)

all the best :)

---

### Post by gamblor01 on 2009-05-14
No better way to learn than to just start trying things out and see what happens.  Also make sure you understand how to use the man pages.  For example, to find out how the "grep" command works just open your terminal and type:

```

man grep

```If you want to know how "ls" works then:

```

man ls

```You get the idea...


Here's a guide with side-by-side DOS and Unix commands (looks pretty old but mostly still relevant).

[http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html](http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html)

Also, here is a list of stuff I put together for some students.  Just basic Linux commands they should know about.  The options in parenthesis are some of the options I use on a regular basis.  

> 
cd

ls (-a, -l, -d, -R):
ls
ls -l
ls -al
ld -ld
ls -lR

cp (-r/-R)

mv

rm (-r, -f)   // BE CAREFUL, especially with -rf 

find:
find . -name '*.java'
find . -name 'Hello*'
find ~ -mtime 2

grep (-r, -n, -i, -v):
grep 'pub' HelloWorld.java
grep -v 'main' Hello*.java
grep -rni 'public' .
grep -i 'MAIN' *.java

cat

head (-n)

tail (-n, -f)

less

more


*****************************
***** ADVANCED COMMANDS *****
*****************************
chmod

chown

chgrp

su (or sudo)


---

### Post by jonobr on 2009-05-14
Once you have become stronger on the terminal, you will find that a lot of working with X systems is file related.
Everything in linux/ubuntu is control be files and you would need to be able to midfy them, so when you master the basics, start to go into things like vi, vim or emacs, depending on your preference.

Also, I think your familiarity of the terminal will increase when you start to get more away from running applications and using icons and programs and actually try and do it on the terminal.

---

