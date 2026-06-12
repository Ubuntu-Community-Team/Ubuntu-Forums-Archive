---
title: "simultaneous command line commands"
date: 2009-04-07
forum: General Help
---

### Post by r1ch on 2009-04-07
Hello,

I am trying to find out how I can run simultaneous commands from the command line. I have taken a look at the _[command line how-to]("https://help.ubuntu.com/community/CommandlineHowto#Multiple%20Commands")_ but it seems to only describe how to run one command after another with 
```
command 1 ; command 2
```
or how to run only upon successful completion with
```
command 1 && command 2
```
or only if command 1 fails with...
```
command 1 || command 2
```

What I am trying to do is more like the first example but instead of the terminal performing each command sequentially, I would like them to be performed simultaneously.

Does anybody have any ideas please?

Thankyou.

---

### Post by easybake on 2009-04-07
> **r1ch said:**
> Hello,

I am trying to find out how I can run simultaneous commands from the command line. I have taken a look at the _[command line how-to]("https://help.ubuntu.com/community/CommandlineHowto#Multiple%20Commands")_ but it seems to only describe how to run one command after another with 
```
command 1 ; command 2
```
or how to run only upon successful completion with
```
command 1 && command 2
```
or only if command 1 fails with...
```
command 1 || command 2
```

What I am trying to do is more like the first example but instead of the terminal performing each command sequentially, I would like them to be performed simultaneously.

Does anybody have any ideas please?

Thankyou.


Any reason this is limited to only one terminal running?

---

### Post by sdennie on 2009-04-07
You could use & to put the tasks in the background:

```

command1 & command2 &

```

Or, you can pipe the output of one command to the second:

```

command1 | command2

```

It sounds like the former is probably what you are looking for though.

---

### Post by r1ch on 2009-04-07
> **easybake said:**
> Any reason this is limited to only one terminal running?

No not really, I'm just trying to explore a bit of the terminal and wondered where/how this function was available.

---

### Post by r1ch on 2009-04-07
> **sdennie said:**
> You could use & to put the tasks in the background:

```

command1 & command2 &

```

Or, you can pipe the output of one command to the second:

```

command1 | command2

```

It sounds like the former is probably what you are looking for though.


Thankyou !! That's exactly what I was aiming for... and such a simple solution :-)

---

### Post by ajgreeny on 2009-04-07
The difference between a single & and double & is that the double & waits for the first command to execute successfully and then moves on to the second.  The single & just carries them out without waiting for success, so if the second depends on the first being successful, you need the two &s or it all "goes to worms" (dies) if the first does not work.

---

