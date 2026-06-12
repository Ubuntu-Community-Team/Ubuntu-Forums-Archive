---
title: "How to make something that executes a command"
date: 2008-12-11
forum: General Help
---

### Post by caru93 on 2008-12-11
Kind of like a .bat in windows, how do i make something like that in ubuntu?
like, i need something to make my life much easier, where i can click on it, and it executes a command.
for example.. say i wanted to run a "sudo modprobe acerhk force_series=6000" command, all i'd have to do is click on that. rather then open terminal and type it out everytime.

again, kind of like the function of a .bat in windows.
how do i make/do this?

---

### Post by fubbleskag on 2008-12-11
create a text file with the command(s) and save it. then make it executable using
```
chmod +x filename
```

---

### Post by ajcham on 2008-12-11
Right-click on the desktop and select 'create launcher'.
Set type to 'application in terminal', give the launcher a useful name, and enter the command in the 3rd box.  Click OK.

---

