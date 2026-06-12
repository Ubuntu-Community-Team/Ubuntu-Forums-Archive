---
title: "couldnt find this question, really need help, grep"
date: 2009-04-18
forum: General Help
---

### Post by jli024 on 2009-04-18
my uncles pushing me to learn this, and i forgot what it does. please some1 reply. i need to know what ps -ef | grep -i does and situations where i can use it. so what it does, and a situation in the terminal where i can use it please! ty:popcorn:

---

### Post by justin_guerin on 2009-04-18
Read the output of the following two commands:

man ps
man grep

You might also want to google for "Unix pipe", a the vertical separator between the two commands, |, is called a pipe.

---

### Post by jli024 on 2009-04-20
i just need to know when to use ps -ef | grep -i in the terminal. or a situation to use that exact line. :mrgreen:

---

### Post by VCoolio on 2009-04-20
It is a process search (ps)
for every process using standard syntax (-ef)
out of with you select ( | grep).
I don't understand the -i part and the command as such does nothing. I use this line for example often:
```
ps -ef | grep conky
```
to show all conky processes, so I can kill and restart the one I want (killall / pkill conky would kill all conky processes).

---

### Post by Iowan on 2009-04-20
> **jli024 said:**
> my uncles pushing me to learn this,Your uncle wouldn't happen to be an instructor who gives homework assignments???

---

### Post by jli024 on 2009-04-20
he wants me to learn vi, and oracle stuff. and he told me to learn a bunch of vi script stuff 2 weeks ago, and told me this to learn that random line, and i was like okay, and slacked off for a eek and a half and forgot what that did

---

### Post by dmizer on 2009-04-20
> **jli024 said:**
> he wants me to learn vi, and oracle stuff. and he told me to learn a bunch of vi script stuff 2 weeks ago, and told me this to learn that random line, and i was like okay, and slacked off for a eek and a half and forgot what that did

I'm sure your uncle would be helpful and understanding if you asked him.

Closing thread, as the question has been answered.

---

