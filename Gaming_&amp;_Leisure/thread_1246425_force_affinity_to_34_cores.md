---
title: "force affinity to 3/4 cores?"
date: 2009-08-21
forum: Gaming &amp; Leisure
---

### Post by kenji_03 on 2009-08-21
I'm trying to tweak around with affinity in Ubuntu for various reasons.  (Don't tell me "You don't need to", I've read the billion other threads that tell me I'm an idiot for wanting to).

My question is this: is there an easy command or short-set of commands I can run in order to force all other programs to run on 3/4 of my cores?  I ask this because I want to be 100% sure one core is always free for me to give a program it's own personal core (games, rendering programs, etc...)

I know that some programs do not utilize parallel processing: ([http://www.codinghorror.com/blog/archives/000942.html](http://www.codinghorror.com/blog/archives/000942.html)), but I'm still really new to Ubuntu and Linux and would really appreciate any advice anyone has.

I tried to read this article: [http://www.ibm.com/developerworks/linux/library/l-affinity.html](http://www.ibm.com/developerworks/linux/library/l-affinity.html) but (sadly) I kind of got confused in reading it :oops:

---

### Post by Vadi on 2009-08-21
The page you linked is irrelevant, because it's for programmers who want to code this functionality in.

For a command-line program, I think you can use "taskset" to set the affinity of each process individually. Don't know how to make a script to do the 3/4ths though.

---

