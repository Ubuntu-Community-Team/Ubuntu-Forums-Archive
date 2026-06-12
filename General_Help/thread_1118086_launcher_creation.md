---
title: "launcher creation?"
date: 2009-04-06
forum: General Help
---

### Post by upchucky on 2009-04-06
Hello there,

I am trying to create a launcher on my desktop or title bar that combines the following into a single step.

First I start Ventrilo by clicking an Icon on my desktop.

Then when Ventrilo is running I need to activate a ventrilo key-press detection program that lets me use a keyboard key for the "press to talk feature".

As it presently works, as shown below, I must open a terminal then do the first code entry
after that code entry is done, I must then do the second code entry 


```
cd /home/electric/ventriloctrl-0.3
```


```
./runctrl.sh
```

Even if I can only create a launcher that combines the two code entries it would be better than all the typing, or copy/pasting.


Any Ideas?

---

### Post by aaronp on 2009-04-14
open a text editor, add these two commands to a shell script and then when you create the launcher, the command to launch will be to execute the shell script you have written.

hth
Aaron

---

### Post by s.fox on 2009-04-14
Hi,

More information on creating shell script can be found [here]("http://www.bsdnewsletter.com/bsda-book/Create_a_simple_Bourne_shell_script.html")

Hope it helps.

-Ash R

---

