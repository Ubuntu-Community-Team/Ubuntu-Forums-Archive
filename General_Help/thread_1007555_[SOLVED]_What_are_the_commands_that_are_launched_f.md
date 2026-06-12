---
title: "[SOLVED] What are the commands that are launched for these?"
date: 2008-12-10
forum: General Help
---

### Post by ardchoille42 on 2008-12-10
I would like to learn about the following things, trying to learn a bit more about Ubuntu today.

1. What command is launched when the user presses alt+f2?

2. What command is launched when the user clicks on log out?

I am attempting to write a custom gui and need to know how to launch these as if I were doing it from command line.

---

### Post by ajcham on 2008-12-10
> What command is launched when the user presses alt+f2?

The Gnome Run Dialog has been combined into the panel app, so there is no separate command.  Two options I would suggest are:

a) There is a project which has extracted the code for the Run Dialog and can be installed as a standalone app.  It can be obtained from [here (freshmeat.net)]("http://freshmeat.net/projects/grd/").

b) A simpler run dialog can be installed from the repos - look for grun. It lacks the functionality of the gnome-run-dialog, but if it suffices, it would be the easier option.

> What command is launched when the user clicks on log out?

I believe it is [FONT="Fixedsys"]**/usr/bin/gnome-session-save --kill --silent**[/FONT]

---

### Post by snova on 2008-12-10
Alt-F2 is, I believe, intercepted by part of the desktop. I'm not sure *which* part. In KDE it's krunner, at the least.

As for Log Out, it's probably not a command either, but a signal of some kind to the desktop system to terminate and return control to the DM. Not sure.

But writing a custom GUI? Could you elaborate on that? That's an incredible amount of work if you're attempting what I think you are.

---

### Post by fooman on 2008-12-10
not quite what your looking for,  but for alt-f2...try:

```
gksu
```

for logout:

```
gnome-session-save --kill
```

---

### Post by snova on 2008-12-10
> **fooman said:**
> not quite what your looking for,  but for alt-f2...try:

```
gksu
```

That would have some rather unfortunate side effects. :|

---

### Post by sisco311 on 2008-12-10
> **ardchoille42 said:**
> I
1. What command is launched when the user presses alt+f2?


in xfce is *xfrun4*.

try to open a terminal. press Alt+F2, switch to the terminal and list the running processes: *ps -ef*.

---

### Post by ardchoille42 on 2008-12-10
> **ajcham said:**
> The Gnome Run Dialog has been combined into the panel app, so there is no separate command.  Two options I would suggest are:

a) There is a project which has extracted the code for the Run Dialog and can be installed as a standalone app.  It can be obtained from [here (freshmeat.net)]("http://freshmeat.net/projects/grd/").

b) A simpler run dialog can be installed from the repos - look for grun. It lacks the functionality of the gnome-run-dialog, but if it suffices, it would be the easier option.



I believe it is [FONT="Fixedsys"]**/usr/bin/gnome-session-save --kill --silent**[/FONT]

Looks like grun will suffice nicely, thank you for the info :)

I took your info about /usr/bin/gnome-session-save, read the man page, it was easy to find once I had the name of the binary involved, this is what I found:


gnome-session-save can be used from a GNOME session to save a snapshot of the currently running applications. This session will be later restored at your next GNOME startup session.

The --gui argument will report errors in dialog boxes instead of printing to stderr.

If called with the --logout argument, the current GNOME session will be ended, unless logging out has been inhibited by an application. The  --force-logout argument can be used to end the session regardless of the inhibition state.

When the --logout-dialog argument is given, the standard dialog displaying logout options is displayed. When --shutdown-dialog argument is given, the standard dialog displaying shutdown options is displayed.

The --kill argument is deprecated. It is equivalent to the --logout-dialog argument. If --silent is used with --kill, then it will behave as if --logout was used.

The session is not saved when gnome-session-save is called with any of the arguments ending the session.

---

### Post by ajcham on 2008-12-10
Glad I could help, and the extra info about gnome-session-save is much appreciated (despite referring to them frequently, I still overlook man pages on occasion).

---

