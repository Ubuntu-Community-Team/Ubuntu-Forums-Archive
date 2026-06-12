---
title: "prompt customizing problem"
date: 2009-05-02
forum: General Help
---

### Post by zackpete on 2009-05-02
I changed my command prompt to make it green. Here's the code I used: \e[32m\u@\h:\w$\e[0m
Now whenever I navigate through older commands (up arrow) sometimes part of one of the commands gets stuck there and I can't clear it until I run another command. Not a big problem, but it's bugging the hell outta me. Anyone know what's going on?

zack@home:~$ for ARG iecho $PS1
\e[32m\u@\h:\w$\e[0m

'for ARG i' is the part that's stuck in this case

---

### Post by zackpete on 2009-05-05
bump

---

