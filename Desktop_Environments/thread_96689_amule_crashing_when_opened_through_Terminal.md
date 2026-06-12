---
title: "amule crashing when opened through Terminal"
date: 2005-11-29
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-11-29
I got a weird problem: When I open amule through the terminal, it sloses as soon as I close the terminal.
Opening the program by clicking through the command line on my panel works fine. 

Sounds unreal? It's exactly the situation.

Any clues?

Thanx

Gabriel

---

### Post by invalid on 2005-11-29
I do not know what amule is, but I bet I know what the problem is. It sounds like this is a program that you run, and your terminal returns with the program running in the background.

I suspect that you need to start the program as a daemon, that way you can escape the shell without killing the process. Add a "&" at the end of the command.```
program &
```

Now, when you type "exit" to escape the shell, the process will remain active in the background.

Cheers,
Cb

---

### Post by GabrielWolff on 2005-11-29
Worked fine, thanx. But when closing the terminal by clicking on the x in the upper right corner, the program still terminates.

Why's that?

Gooday

Gabriel

---

### Post by invalid on 2005-11-29
I am not 100% positive why the X does not work exactly like the "exit" command, but I suspect that is acts like an interupt to the terminal login. When you explicitly type```
exit
```the terminal knows what you are doing, and makes necessary fixes.

Maybe someone who knows a little more can explain the exact difference.

Cb

---

