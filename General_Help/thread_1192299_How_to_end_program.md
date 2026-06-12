---
title: "How to end program"
date: 2009-06-19
forum: General Help
---

### Post by DedicatedOT on 2009-06-19
How to end a program in console in ubuntu?

it is a console program.. but there's no root@local: showing.. what do i do to quit the program?

---

### Post by Chemical Imbalance on 2009-06-19
ctrl + z



or even try ctrl + c

---

### Post by DedicatedOT on 2009-06-19
Thank you! But now I try to run it again it says:
```

[ServicePort::open] Error: Address already in use

```

How do I restart the port 7171?

---

### Post by Chemical Imbalance on 2009-06-19
I don't know what program you're using.

Try ```
man program
```

replace "program" with the command for the program you're using to learn the options that go with it.

You could also try closing and opening your console again.

---

### Post by DedicatedOT on 2009-06-19
How do you release port 7171?

---

### Post by monkey56657 on 2009-06-20
You know the program name? 

Then the (messy) way to end it:

$ killall <program>

So if the program was transmission then do this at a terminal:

$ killall transmission

You should then have free'd up your port.

---

### Post by paperplate9 on 2009-06-20
do a 
$ sudo netstat -antp | grep 7171

look at the last column to grab the processname/id owning that port

$ sudo killall processname

to kill it

---

### Post by Hobgoblin on 2009-06-20
> **DedicatedOT said:**
> How to end a program in console in ubuntu?

it is a console program.. but there's no root@local: showing.. what do i do to quit the program?

What program?

pressing q quits a number of applications (top, aptitude, man)

---

