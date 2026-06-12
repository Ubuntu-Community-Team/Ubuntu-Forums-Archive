---
title: "Starting program instances in the background"
date: 2009-01-17
forum: General Help
---

### Post by AwesomeTux on 2009-01-17
Hello, I am wondering how I would go about running a program instance like Gedit or Firefox in the background. I'm running Ubuntu 8.10.

---

### Post by Ahadiel on 2009-01-17
From the commandline?
```
command &
```
or with screen
```
screen command
```

---

### Post by AwesomeTux on 2009-01-17
> **Ahadiel said:**
> From the commandline?
```
command &
```
or with screen
```
screen command
```

That didn't work for what I wanted. I don't want it to draw a window, so that when I want to use the program I ran in the background, all it has to do is draw a window, and not have to start the program. Much like when Firefox is already running, opening a new window starts like that. Or when having RhythmBox running in the tray, clicking the icon just draws a window, and you can open and close that window much faster than starting the program from start to finish each time you want to skip tracks.

So I know it can be done.

---

### Post by sedawk on 2009-01-18
Firefox has a frontend, a shell script, that does all the magic.

Some other applications can be started in "minizimed" mode, so they
are not opening the normal window.

I'm not aware of a minimized switch working for all applications.
(But there might be, e.g. something like a standard argument
"--minimized" understood by the underlying widget library, e.g.
gtk, kde/qt, wxwidgets).

---

### Post by AwesomeTux on 2009-01-19
Anyone? any ideas?

---

