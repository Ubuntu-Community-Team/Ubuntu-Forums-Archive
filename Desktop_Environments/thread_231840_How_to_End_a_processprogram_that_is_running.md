---
title: "How to End a process/program that is running?"
date: 2006-08-07
forum: Desktop Environments
---

### Post by RESmonkey on 2006-08-07
I usually get stuck in a game called EnemyTerritory (Wofenstein), I just wanted to know how I could kill the game process?

I can go to Ctrl+Alt+F1 into terminal, but what is the command to end a process/kill a process, etc?

---

### Post by raffytaffy on 2006-08-07
killall (game name)

---

### Post by cantormath on 2006-08-07
> **RESmonkey said:**
> I usually get stuck in a game called EnemyTerritory (Wofenstein), I just wanted to know how I could kill the game process?

I can go to Ctrl+Alt+F1 into terminal, but what is the command to end a process/kill a process, etc?
in terminal

```
cantormath@cantormath-laptop:~$ top
```
find the process
```
cantormath@cantormath-laptop:~$ kill -9 <processID>
```

---

### Post by RESmonkey on 2006-08-07
Thanks guys, I'm going to try them every time i want to quit.

---

