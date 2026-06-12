---
title: "ctrl-c in xterm"
date: 2009-04-27
forum: Desktop Environments
---

### Post by rijen on 2009-04-27
I installed 9.04 and have the following problem:
While in a xterm, on the commandline, pressing ctrl-c generates a new line, but does not terminate the xterm (as expected).
when I start an application in the xterm, pressing ctrl-c not only terminates that program but also the xterm!
How do I prevent the xterm from terminating too?

---

### Post by kerry_s on 2009-04-27
```
program-name &
```

but why don't you just use **alt+f2** if you want to run a program, it will even remember what you ran to save you typing, just use the up arrow key.

---

### Post by rijen on 2009-04-27
> **kerry_s said:**
> ```
program-name &
```

but why don't you just use **alt+f2** if you want to run a program, it will even remember what you ran to save you typing, just use the up arrow key.

Thnx for your response, I will try the & 
I thought it ment that the program will be started in the background, but it is shows info on the console.
It is existing software that start 3 xterm windows, that runs as expected under OpenSuse

---

### Post by rijen on 2009-04-27
> **rijen said:**
> Thnx for your response, I will try the & 
I thought it ment that the program will be started in the background, but it is shows info on the console.
It is existing software that start 3 xterm windows, that runs as expected under OpenSuse

The ampersand does not work. xterm terminates anyway :(

---

### Post by kerry_s on 2009-04-27
so why can't you use alt+f2? it's a lot easier.

anyway's i have my coffee now, so try this:

launch your program with "&" on the end> program-name &
now you need the job number, type> jobs
now you need to disown it> disown %#

see pic:

---

### Post by Locutus_of_Borg on 2009-04-27
that should not be happening

is there any output if you open an xterm from another xterm and press ctrl-C in the second one?

---

