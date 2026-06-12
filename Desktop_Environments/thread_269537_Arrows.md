---
title: "Arrows"
date: 2006-10-01
forum: Desktop Environments
---

### Post by gumbeto on 2006-10-01
hi there, I'm becoming mad with the arrows of the keyboard in the programs that run inside the shell.
It happens that instead of the normal behavior of moving the cursor or making the last typed expression appear, some characters  are typed: 
^[[A, ^[[D 
and so on.

Does anyone know how to correct this?

Thanx a lot for the help
gumbeto

---

### Post by Jussi Kukkonen on 2006-10-02
Sounds normal... What would you like to happen?

If you wanted to keep using the terminal while a program is running in the background, use "&" after the command:
```
firefox &
```
Alternatively you can press ctrl-Z to put an already running program to sleep, and commands *fg* and *bg* to bring it running again on the foreground or on the background, respectively.

---

### Post by gumbeto on 2006-10-03
Thank you for the reply but I meant something else. For example, when I run sicstus (a prolog interpreter), it runs ***inside*** the shell (it uses it to interact with the user through both input and output). But the input isn't always understood correctly, namely the meaning of the arrow keys (It prints ^[[A and things like that, instead of moving the cursor) and that's what I'd like to change.

Thanks anyway
gumbeto

---

