---
title: "How to run GUI programs from terminal correctly?"
date: 2010-08-03
forum: Desktop Environments
---

### Post by EgoGratis on 2010-08-03
I can't figure this out. If i run GUI program (in GNOME) from terminal. It doesn't works the same as if i run it from menus (or shortcut on desktop or panel). Or some times I run it from Alt+F2 method.

What is the difference in this methods?

For example what is the difference if i put this...

metacity --replace

...in terminal or in ALT+F2 dialog window. If I put it in terminal. GNOME doesn't work correctly.  If i put it in Alt+F2 dialog window. It works as it should. With no problems.

And what is the difference if i like to run for example FireFox or gnome-control-center from terminal or select it from menus.

If i like to run  from terminal. What would be right way to do it? 

Because sometimes i get errors in terminal (but GUI works) sometimes after i close terminal GUI program closes to. Sometimes it doesn't. But if i run that program from menus (icons) there is no such problem. It just works. If i put & at the end of program. I can work in terminal. But still all of the above is still true.

Can somebody explain this to me?

---

### Post by Doobie9 on 2010-08-03
When you run it in a terminal, the program itself is 'inside' the terminal. So if you close the terminal anything you've got running from it will also close. You get the benefits of reading live error and debugging information.

[I think there is a way to detach a program from the terminal it's launched form. Since I haven't had to do this in a long time I don't know the exact procedure.]

If you run a program from the menu or using something like alt-f2 or gnome-do, it runs inside your session (i.e., not tied down to a terminal). Other than that, I don't believe that the programs will run any differently; though I may be wrong about this.

:)

---

### Post by stderr on 2010-08-03
metacity --replace should not have any problems running in a terminal window. What issues are you experiencing? 

Running Firefox etc inside a terminal is just as you say - 

```
firefox
```

or

```
firefox &
```

to start in the background. If you haven't spawned any other processes from the [same] terminal [window] first, and if you've backgrounded the process already (second code example above), you can use disown to detach the process from the terminal. For example:

```
firefox &
disown
```

Alternatively, without backgrounding with &, you'd need to "stop" the process and then background it manually before disowning, as so:

```
firefox
[Ctrl+Z] <-- press these two keys to "stop/pause" a process
bg
disown
```

BASH builtins bg, disown & fg can optionally take a job id number. The id for your process can be ascertained by using the BASH builtin jobs

```
jobs
```

Stdout and stderr output can easily be suppressed by redirecting it somewhere like /dev/null. For example

```
firefox &> /dev/null
```

---

### Post by EgoGratis on 2010-08-07
First of all thanks for answers.

>  metacity --replace should not have any problems running in a terminal window. What issues are you experiencing? 

Unresponsive system. GUI programs losing title bar. I must log off/on to correct the problem. ALT+F2 + metacity --replace doesn't do that. It just works good.


So **disown** is the command to break GUI program (process) from terminal. What is technically speaking difference or correct term for GUI programs running from menus. And from terminal.

Terminal session vs. user (GDM) session?

---

