---
title: "Running executables"
date: 2009-06-03
forum: General Help
---

### Post by shekshek on 2009-06-03
Hi,
  My question is if I write a shell script or compile and build a C program...why do I have to run it by saying ./name ? 

For eg. if I write a shell script and then I do ```
chmod u+x scriptname
```...then afterwards I want to be able to run it with just saying scriptname...instead of ./scriptname. Is there a way to do this?

I'm asking because that's how it is at my school. I don't know which linux they use...sorry about that...but it's not ubuntu...and they use kde instead of Gnome. I don't know if all this matters.

Thanx a lot.

---

### Post by Tibuda on 2009-06-03
If the binary is on the PATH, then you don't need the ./

---

### Post by DGortze380 on 2009-06-03
When you type a command in the shell (most shells) the PATH Variable is checked. This contains a set of directories to search for executables. If the directory in which your script is stored is in your PATH, you can just type the name. If not, you must tell the shell ./ (here and now) run "this".

I generally create a directory for my scripts and add it to my PATH. Alternately, you can use /usr/bin or /usr/sbin directories.

---

### Post by shekshek on 2009-06-05
oh ok. thanx a lot

---

