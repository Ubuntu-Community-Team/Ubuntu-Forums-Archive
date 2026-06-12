---
title: "Weird problem with fork() and output pipes."
date: 2009-06-18
forum: General Help
---

### Post by ydraliskos on 2009-06-18
This problem came up when trying to pipe the output of a small C program on a file.


C program roughly does this.

main()
-starts with args at runtime.
-printfs a line depending on how many args it received.
-runs a child function.
-ends.

Child function forks the *living ***** out of itself but this is of no real importance, it's just a demonstration of tree structures as processes. Forks print a bunch of stuff then die. 


Ok so I run it in terminal and get the expected output. 1 informative line about how many args it received, then the fork output.

if however, I try 
./a.out 2 3 5 > output.txt

the output.txt file, instead of the text i saw without pipes, will contain the informative line multiple times, intermingled with the fork outputs. I haven't really counted but I suspect it will be as many times as there are forks.

Why does this happen. At no point during their lives do the forks visit the start of main(). Why are those lines printed, and why only when piping the output?

---

### Post by ydraliskos on 2009-06-18
is this not the right forum for this btw?

---

### Post by wirelessmonkey on 2009-06-18
You'd probably be better of in the Programming Forum...

---

