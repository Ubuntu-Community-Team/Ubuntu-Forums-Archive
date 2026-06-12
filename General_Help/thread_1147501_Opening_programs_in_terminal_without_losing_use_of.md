---
title: "Opening programs in terminal without losing use of terminal"
date: 2009-05-03
forum: General Help
---

### Post by PaulTR on 2009-05-03
Probably missing something pretty obvious here, buuuut whatever. I'm working on my Java programming, and have just been using the applications drop down menu to open gedit, but I was wondering if there's a way to open up gedit without losing the use of the terminal while the program is running. Right now gedit opens when the name is typed into the terminal, but then the terminal doesn't give me a new line prompt until I've closed the application. Any way around this? Thanks.


Edit: Typed gparted in this forum post when I meant edit.

---

### Post by kellemes on 2009-05-03
```
command &
```

---

### Post by PaulTR on 2009-05-03
Awesome, thanks. Makes life a bit easier :D <3 terminal

---

### Post by blackened on 2009-05-03
> **kellemes said:**
> ```
command &
```

Or alt+F2, then gedit in the run dialog.

---

### Post by kellemes on 2009-05-03
If you need to some more info about working from CLI you can find some tips right here..
[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by karlr42 on 2009-05-03
What I like to do is run command & , but then run "disown". Otherwise, when you close the terminal, the program you had put in the background with & (and have forgotten :D) will be closed

---

### Post by Primefalcon on 2009-05-03
either that or use nohup when start program example

```
$nohup firefox
```

it's just short for no hangup when terminal is closed

---

### Post by blackened on 2009-05-03
nohup seems nice but disown would probably work better. Usually, by the time I remember that I will or want to detach a process from the terminal that spawned, I have already run said program. This is why I generally save myself the trouble and launch it from the run dialog.

---

